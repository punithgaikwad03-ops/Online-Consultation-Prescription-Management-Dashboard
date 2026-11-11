ONLINE CONSULTATION & PRESCRIPTION MANAGEMENT DASHBOARD

A desktop database application for a telemedicine platform, built with Python, Tkinter, and SQLite. It manages doctors, online consultation sessions, and prescription items through a simple tabbed GUI backed by a relational database.

FEATURES

Relational database design with three linked tables (doctors, consultations, prescription_items) using foreign keys and ON DELETE CASCADE
Automatic sample data is inserted when the database is empty
Add a consultation and its prescription in a single step
Reuse an existing doctor profile or create a new one
Delete a doctor, a consultation, or a single prescription item
Four live data tabs: combined SQL JOIN view, Doctors, Consultations, and Prescription Items
Input validation for blank fields and invalid or negative medicine cost
All tables and delete dropdowns refresh after every insert or delete

DATABASE STRUCTURE

doctors -> consultations -> prescription_items

doctors: doctor_id (primary key), doctor_name (unique), email
consultations: consultation_id (primary key), doctor_id (foreign key), patient_name, consultation_date
prescription_items: prescription_id (primary key), consultation_id (foreign key), medicine_name, cost

Cascade rules:

Deleting a doctor also deletes that doctor’s consultations and their prescription items
Deleting a consultation also deletes its prescription items
Deleting a prescription item deletes only that row

TECH STACK

Python 3
SQLite (sqlite3, built into Python)
Tkinter / ttk (Notebook and Treeview widgets)

No extra packages are required.

HOW TO RUN

Clone the repository.
Open CE4_Online_Consultation_Prescription_Dashboard_25SSDS415051.ipynb in Jupyter or VS Code.
Run all cells. The Tkinter window opens on a computer with a graphical desktop.
The database file consultation_dashboard.db is created in the working folder.

Note: In cloud notebooks without a desktop display (such as Google Colab), the database setup and helper functions will run, but the GUI window cannot open. Run it locally to use the dashboard.

To reset the demo, close the app, delete consultation_dashboard.db, and run the setup again.

HOW IT WORKS

get_connection() opens the SQLite database and enables foreign-key enforcement.
initialize_database() creates the tables and adds sample data if the database is empty.
add_consultation_record() reuses or creates a doctor, then inserts the consultation and prescription.
fetch_join_view() combines all three tables using SQL JOIN.
delete_record() deletes the selected row and lets SQLite cascade to child rows.
refresh_all() reloads every tab and dropdown after each operation.
