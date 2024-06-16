# Book My Show

## Entities

1. Users

- **Attributes:**
  - id (PK)
  - name
  - email
  - phoneNumber

2. City

- **Attributes:**
  - id (PK)
  - name
  - state
  - zipcode

3. Theatres

- **Attributes:**
  - id (PK)
  - theatre_name
  - city (FK)

4. Screens

- **Attributes**
  - id (PK)
  - screen_name
  - theatre (FK)
  - capacity

5. Movies

- **Attributes:**
  - id (PK)
  - movie_name
  - actors
  - movie_length

6. Movie_Schedules

- **Attributes:**
  - id (PK)
  - movie (FK)
  - screen (FK)
  - start_time
  - end_time

## SQL Queries:

### Table Creation and Sample Data Insertion

- Users

```
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  phone VARCHAR(20)
);

INSERT INTO users (name, email, phone) VALUES
('Amit Patel', 'amit.patel@example.com', '9876543210'),
('Priya Sharma', 'priya.sharma@example.com', '8765432109'),
('Rahul Kumar', 'rahul.kumar@example.com', '7654321098'),
('Neha Gupta', 'neha.gupta@example.com', '6543210987'),
('Sandeep Singh', 'sandeep.singh@example.com', '5432109876');
```

- City

```
CREATE TABLE city (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  state VARCHAR(100) NOT NULL,
  zipcode VARCHAR(10) NOT NULL
);

INSERT INTO city (name, state, zipcode) VALUES
('Bangalore', 'Karnataka', '560001'),
('Hyderabad', 'Telangana', '500001'),
('Pune', 'Maharashtra', '411001');
```

- Theatres

```
CREATE TABLE theatres (
  id INT PRIMARY KEY AUTO_INCREMENT,
  theatre_name VARCHAR(255) NOT NULL,
  city INT,
  FOREIGN KEY (city) REFERENCES city(id)
);

INSERT INTO theatres (theatre_name, city) VALUES
('Inox Mall of India', 1),
('PVR Phoenix Marketcity', 1),
('Cinepolis Mantri Square', 1),
('INOX GVK One', 1),
('PVR Grand Mall', 2),
('SPI Cinemas Express Avenue', 2),
('Cinepolis Seasons Mall', 3),
('PVR Acropolis', 3),
('INOX Crystal Palm', 3),
('Cinepolis Phoenix United', 3);
```

- Screens

```
CREATE TABLE screens (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  theatre INT,
  capacity INT NOT NULL,
  FOREIGN KEY (theatre) REFERENCES theatres(id)
);

INSERT INTO screens (name, theatre, capacity) VALUES
('Screen 1', 1, 150),
('Screen 2', 1, 200),
('Screen 3', 1, 70),
('Screen 4', 1, 100),
('Screen 5', 1, 170),
('Screen 6', 1, 170),
('Screen 1', 2, 150),
('Screen 2', 2, 200),
('Screen 3', 2, 70);
```

- Movies

```
CREATE TABLE movies (
  id INT PRIMARY KEY AUTO_INCREMENT,
  movie_name VARCHAR(255) NOT NULL,
  actors TEXT,
  movie_length BIGINT
);

INSERT INTO movies (movie_name, actors, movie_length) VALUES
('Chennai Express', 'Shah Rukh Khan, Deepika Padukone, Sathyaraj', 141),
('The Godfather', 'Marlon Brando, Al Pacino, James Caan', 175),
('Baahubali 2: The Conclusion', 'Prabhas, Rana Daggubati, Anushka Shetty', 171),
('Padmaavat', 'Deepika Padukone, Ranveer Singh, Shahid Kapoor', 164);
```

- Movie_Schedules

```
CREATE TABLE movie_schedules (
  id INT PRIMARY KEY AUTO_INCREMENT,
  movie INT,
  screen INT,
  start_time DATETIME NOT NULL,
  end_time DATETIME NOT NULL,
  FOREIGN KEY (movie) REFERENCES movies(id),
  FOREIGN KEY (screen) REFERENCES screens(id)
);

INSERT INTO movie_schedules (movie, screen, start_time, end_time) VALUES
(1, 1, '2024-06-15 10:00:00', '2024-06-15 12:30:00'),
(2, 2, '2024-06-15 10:00:00', '2024-06-15 12:30:00'),
(3, 3, '2024-06-15 10:00:00', '2024-06-15 12:30:00'),
(4, 4, '2024-06-15 10:00:00', '2024-06-15 12:30:00'),
(1, 5, '2024-06-15 10:05:00', '2024-06-15 12:40:00'),
(3, 6, '2024-06-15 10:05:00', '2024-06-15 12:50:00'),
(1, 1, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(2, 2, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(3, 3, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(4, 4, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(1, 5, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(3, 6, '2024-06-15 13:00:00', '2024-06-15 15:55:00'),
(2, 7, '2024-06-15 10:00:00', '2024-06-15 12:30:00'),
(2, 8, '2024-06-15 10:45:00', '2024-06-15 14:00:00'),
(2, 9, '2024-06-15 10:30:00', '2024-06-15 13:45:00'),
(2, 7, '2024-06-15 13:00:00', '2024-06-15 16:05:00'),
(3, 8, '2024-06-15 14:30:00', '2024-06-15 16:45:00'),
(4, 9, '2024-06-15 14:00:00', '2024-06-15 16:15:00');
```

### Sample Data Insertion

## Example Table Data

### Users

| id  | name          | email                     | phone      |
| --- | ------------- | ------------------------- | ---------- |
| 1   | Amit Patel    | amit.patel@example.com    | 9876543210 |
| 2   | Priya Sharma  | priya.sharma@example.com  | 8765432109 |
| 3   | Rahul Kumar   | rahul.kumar@example.com   | 7654321098 |
| 4   | Neha Gupta    | neha.gupta@example.com    | 6543210987 |
| 5   | Sandeep Singh | sandeep.singh@example.com | 5432109876 |

### City

| id  | name      | state       | zipcode |
| --- | --------- | ----------- | ------- |
| 1   | Bangalore | Karnataka   | 560001  |
| 2   | Hyderabad | Telangana   | 500001  |
| 3   | Pune      | Maharashtra | 411001  |

### Theatres

| id  | theatre_name               | city |
| --- | -------------------------- | ---- |
| 1   | Inox Mall of India         | 1    |
| 2   | PVR Phoenix Marketcity     | 1    |
| 3   | Cinepolis Mantri Square    | 1    |
| 4   | INOX GVK One               | 1    |
| 5   | PVR Grand Mall             | 2    |
| 6   | SPI Cinemas Express Avenue | 2    |
| 7   | Cinepolis Seasons Mall     | 3    |
| 8   | PVR Acropolis              | 3    |
| 9   | INOX Crystal Palm          | 3    |
| 10  | Cinepolis Phoenix United   | 3    |

### Screens

| id  | name     | theatre | capacity |
| --- | -------- | ------- | -------- |
| 1   | Screen 1 | 1       | 150      |
| 2   | Screen 2 | 1       | 200      |
| 3   | Screen 3 | 1       | 70       |
| 4   | Screen 4 | 1       | 100      |
| 5   | Screen 5 | 1       | 170      |
| 6   | Screen 6 | 1       | 170      |
| 7   | Screen 1 | 2       | 150      |
| 8   | Screen 2 | 2       | 200      |
| 9   | Screen 3 | 2       | 70       |

### Movies

| id  | movie_name                  | actors                                         | movie_length |
| --- | --------------------------- | ---------------------------------------------- | ------------ |
| 1   | Chennai Express             | Shah Rukh Khan, Deepika Padukone, Sathyaraj    | 141          |
| 2   | The Godfather               | Marlon Brando, Al Pacino, James Caan           | 175          |
| 3   | Baahubali 2: The Conclusion | Prabhas, Rana Daggubati, Anushka Shetty        | 171          |
| 4   | Padmaavat                   | Deepika Padukone, Ranveer Singh, Shahid Kapoor | 164          |

### Movie_Schedules

| id  | movie | screen | start_time          | end_time            |
| --- | ----- | ------ | ------------------- | ------------------- |
| 1   | 1     | 1      | 2024-06-15 10:00:00 | 2024-06-15 12:30:00 |
| 2   | 2     | 2      | 2024-06-15 10:00:00 | 2024-06-15 12:30:00 |
| 3   | 3     | 3      | 2024-06-15 10:00:00 | 2024-06-15 12:30:00 |
| 4   | 4     | 4      | 2024-06-15 10:00:00 | 2024-06-15 12:30:00 |
| 5   | 1     | 5      | 2024-06-15 10:05:00 | 2024-06-15 12:40:00 |
| 6   | 3     | 6      | 2024-06-15 10:05:00 | 2024-06-15 12:50:00 |
| 7   | 1     | 1      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 8   | 2     | 2      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 9   | 3     | 3      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 10  | 4     | 4      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 11  | 1     | 5      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 12  | 3     | 6      | 2024-06-15 13:00:00 | 2024-06-15 15:55:00 |
| 13  | 2     | 7      | 2024-06-15 10:00:00 | 2024-06-15 12:30:00 |
| 14  | 2     | 8      | 2024-06-15 10:45:00 | 2024-06-15 14:00:00 |
| 15  | 2     | 9      | 2024-06-15 10:30:00 | 2024-06-15 13:45:00 |
| 16  | 2     | 7      | 2024-06-15 13:00:00 | 2024-06-15 16:05:00 |
| 17  | 3     | 8      | 2024-06-15 14:30:00 | 2024-06-15 16:45:00 |
| 18  | 4     | 9      | 2024-06-15 14:00:00 | 2024-06-15 16:15:00 |
