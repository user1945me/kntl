CREATE TABLE cafeterias (
  id int(11) NOT NULL AUTO_INCREMENT,
  name varchar(100) NOT NULL,
  description text DEFAULT NULL,
  image varchar(255) DEFAULT NULL,
  PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
CREATE TABLE menus (
  id int(11) NOT NULL AUTO_INCREMENT,
  cafeteria_id int(11) NOT NULL,
  name varchar(100) NOT NULL,
  description text DEFAULT NULL,
  price int(11) NOT NULL,
  image varchar(255) DEFAULT NULL,
  PRIMARY KEY (id),
  KEY cafeteria_id (cafeteria_id),
  CONSTRAINT menus_ibfk_1 FOREIGN KEY (cafeteria_id) REFERENCES cafeterias (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
CREATE TABLE about (
  id int(11) NOT NULL AUTO_INCREMENT,
  description text NOT NULL,
  image varchar(255) DEFAULT NULL,
  video varchar(255) DEFAULT NULL,
  PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
CREATE TABLE transactions (
  id int(11) NOT NULL AUTO_INCREMENT,
  user_id int(11) DEFAULT NULL,
  items text NOT NULL,
  total int(11) NOT NULL,
  qr_code varchar(255) DEFAULT NULL,
  status enum('pending','completed') DEFAULT 'pending',
  created_at datetime NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
