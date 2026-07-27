# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1247" height="718" alt="Screenshot 2026-07-26 193827" src="https://github.com/user-attachments/assets/d104eac3-4827-4bb4-bba2-8b5caaf60060" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|  Member      |   Member ID (PR'),Member Name,Membership_ Type,Start Date, Phone No,Email             |   Each member has a unique ID    |
| Program       |   Program_ID (PK),Program Name,Duration Fee                 |   Each program can have multiple members and trainers.    |
|    Trainer    |     Trainer ID(PK),Trainer Name,Specialization,Phone_no,Experience               | Trainers can be assigned to multiple programs      |
|  Attendance      |   Attendance_ID (PK), Attendance_Date, Status                 |  Stores attendance details of members.     |
|   Payment     |   Payment_ID (PK), Payment_Date, Payment_Type, Amount                 |  Tracks membership and training payments     |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member – Program (Joins) | M:N | Partial on both sides | A member can join multiple fitness programs, and each program can have multiple members. |
| Trainer – Program (Assigned To) | M:N | Partial on both sides | A trainer can be assigned to multiple programs, and a program can have multiple trainers |
| Member – Trainer (Books) | M:N | Partial on both sides | Members can book personal training sessions with different trainers, and trainers can train multiple members. |
| Member – Attendance (Has) | 1:N | Total on Attendance side | One member can have multiple attendance records, but each attendance record belongs to one member |
| Member – Payment (Makes) | 1:N | Total on Payment side | One member can make multiple payments, while each payment is associated with only one member |
### Assumptions
- Each member, trainer, and program has a unique ID.
- A member can join multiple programs and book multiple training sessions.
- Payments are recorded separately for each member.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1282" height="838" alt="Screenshot 2026-07-26 193455" src="https://github.com/user-attachments/assets/ed0f9de4-bd65-4e54-ad88-a8891d62ec3f" />


### Entities and Attributes

## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| Member | Member_ID (PK), Member_Name, Membership_Date, Phone_No, Email | Stores details of registered library members |
| Book | Book_ID (PK), Title, Author, Category | Contains information about books available for borrowing |
| Event | Event_ID (PK), Event_Name, Event_Date, Event_Time | Stores details of library events |
| Speaker | Speaker_ID (PK), Speaker_Name, Specialization, Phone_No, Email | Stores details of speakers participating in events|
| Room | Room_ID (PK), Room_No, Room_Type, Capacity | Maintains room details for events and study purposes |
| Loan | Loan_ID (PK), Loan_Date, Due_Date, Return_Date | Records book borrowing and return details |
| Fine | Fine_ID (PK), Fine_Amount, Fine_Date, Status | Stores overdue fine information |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Member – Loan (Borrows) | 1:N | Total on Loan side | One member can borrow multiple books through different loans |
| Loan – Book (Includes) | N:1 | Partial on both sides | Each loan record is associated with one book |
| Member – Event (Registers) | M:N | Partial on both sides | Members can register for multiple events, and events can have many members |
| Event – Speaker (Has) | M:N | Partial on both sides | An event can have multiple speakers, and a speaker can participate in multiple events |
| Event – Room (Uses) | N:1 | Total on Event side | Each event is conducted in one room, while a room can host many events over time |
| Loan – Fine (Generates) | 1:1 | Partial on Fine side | A fine is generated for overdue book returns|
### Assumptions
- Each member and book has a unique ID.
- A member can borrow multiple books and register for multiple events.
- Fines are applied only for overdue book returns.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1187" height="848" alt="Screenshot 2026-07-26 195448" src="https://github.com/user-attachments/assets/cb9c317b-5755-44bd-bec1-9f134f692546" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| Customer | Customer_ID (PK), Customer_Name, Phone_No, Email | Stores customer information for reservations and orders |
| Reservation | Reservation_ID (PK), Reservation_Date, Reservation_Time, No_of_Guests | Records table reservation details |
| Table | Table_ID (PK), Table_Number, Capacity, Status | Stores restaurant table details |
| Order | Order_ID (PK), Order_Date, Order_Time, Total_Amount | Records food orders placed by customers |
| Dish | Dish_ID (PK), Dish_Name, Category, Price | Stores menu items with category and price |
| Bill | Bill_ID (PK), Bill_Date, Total_Amount, Service_Charge | Stores billing information for each reservation |
| Waiter | Waiter_ID (PK), Waiter_Name, Phone_No, Shift | Stores waiter details and service assignments |

### Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Customer – Reservation (Makes) | 1:N | Total on Reservation side | A customer can make multiple reservations |
| Reservation – Table (Assigned To) | N:1 | Total on Reservation side | Each reservation is assigned to one table |
| Reservation – Order (Places) | 1:N | Total on Order side | A reservation can include multiple food orders |
| Order – Dish (Contains) | M:N | Partial on both sides | An order can contain multiple dishes, and a dish can appear in multiple orders|
| Reservation – Bill (Generates) | 1:1 | Total on both sides | One bill is generated for each reservation |
| Waiter – Reservation (Serves) | 1:N | Partial on both sides | A waiter can serve multiple reservations|

### Assumptions
- Each customer and reservation has a unique ID.
- A reservation is assigned to one table and served by one waiter.
- A bill is generated for every reservation.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
