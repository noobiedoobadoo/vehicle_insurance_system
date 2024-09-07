# Entity Relationship diagram
![image](https://github.com/user-attachments/assets/c061c75f-7738-4f81-a6e8-1492b64c876b)

#database schema

owner
![image](https://github.com/user-attachments/assets/3adca372-1f93-4d8a-b9b8-1a6ffce45a2d)

car
![image](https://github.com/user-attachments/assets/59f2129e-c6c0-48c8-a45d-a55bd0aa1336)

accident
![image](https://github.com/user-attachments/assets/40d7d413-842f-4ab1-883b-fec73a950235)

policy
![image](https://github.com/user-attachments/assets/1bdce37b-420e-47c3-b66d-ae0370b0d684)


## DDL Statements

### 1. CREATE TABLE `accident`
```
CREATE TABLE `accident` (
  `license_no` varchar(32) NOT NULL,
  `owner_id` int NOT NULL AUTO_INCREMENT,
  `driver_name` varchar(45) NOT NULL,
  `time_of_accident` datetime DEFAULT NULL,
  `place` varchar(45) DEFAULT NULL,
  `repair_cost` int DEFAULT NULL,
  `workshop_name` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`owner_id`),
  KEY `a_lc_no_idx` (`license_no`),
  CONSTRAINT `a_lc_no` FOREIGN KEY (`license_no`) REFERENCES `car` (`license_no`)
);
```
### 2. CREATE TABLE `car`
```
CREATE TABLE `car` (
  `license_no` varchar(30) NOT NULL,
  `owner_id` int DEFAULT NULL,
  `brand` varchar(45) NOT NULL,
  `model` varchar(45) DEFAULT NULL,
  `color` varchar(45) DEFAULT NULL,
  `mfg_date` date NOT NULL,
  PRIMARY KEY (`license_no`),
  KEY `p_id_idx` (`owner_id`),
  CONSTRAINT `p_id` FOREIGN KEY (`owner_id`) REFERENCES `owner` (`owner_id`) 
  ON DELETE CASCADE ON UPDATE CASCADE
);
```
### 3. CREATE TABLE `policy`
```
CREATE TABLE `policy` (
  `policy_id` int NOT NULL AUTO_INCREMENT,
  `start` date NOT NULL,
  `isvalid` tinyint DEFAULT NULL,
  `license_no` varchar(45) DEFAULT NULL,
  `owner_id` int DEFAULT NULL,
  `amount` int NOT NULL,
  `end` date DEFAULT NULL,
  PRIMARY KEY (`policy_id`),
  UNIQUE KEY `license_no` (`license_no`),
  KEY `owner_id_idx` (`owner_id`),
  KEY `lc_no_idx` (`license_no`),
  CONSTRAINT `lc_no` FOREIGN KEY (`license_no`) REFERENCES `car` (`license_no`),
  CONSTRAINT `owner_id` FOREIGN KEY (`owner_id`) REFERENCES `owner` (`owner_id`)
);
```
### 4. CREATE TABLE `owner`
```
CREATE TABLE `owner` (
  `owner_id` int NOT NULL AUTO_INCREMENT,
  `owner_name` varchar(45) NOT NULL,
  `dob` date NOT NULL,
  `address` varchar(45) DEFAULT NULL,
  `pincode` int DEFAULT NULL,
  `mob_no` varchar(13) DEFAULT NULL,
  PRIMARY KEY (`owner_id`)
);
```

## Menu - submenu
![image](https://github.com/user-attachments/assets/d2885bf7-78ba-481c-aded-03c8c723a33d)







