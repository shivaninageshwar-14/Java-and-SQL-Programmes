# Java-and-SQL-Programmes
1)Inserting Data
package NodeJs;

import java.sql.*;

import java.util.Scanner;



public class InsertData {

    public static void main(String[] args) {

        try {

            Class.forName("com.mysql.cj.jdbc.Driver");
                                                                                                                                                                                                                                                                   
            try (Connection con = DriverManager.getConnection("jdbc:mysql://localhost/student2", "root", "1234");

                 PreparedStatement pstmt = con.prepareStatement("INSERT INTO student VALUES (?, ?, ?,?)")) {



                Scanner sc = new Scanner(System.in);

                System.out.println("Inserting Data into student table:");

                System.out.println("________________________________________");



                System.out.print("Enter student id: ");

                int s_id = sc.nextInt();

                System.out.print("Enter student name: ");

                String s_name = sc.next();

                System.out.print("Enter student address: ");

                String s_address = sc.next();

                System.out.print("Enter student address: ");

                String email = sc.next();

                pstmt.setInt(1, s_id);

                pstmt.setString(2, s_name);

                pstmt.setString(3, s_address);

                pstmt.setString(4, email);

                pstmt.executeUpdate();



                System.out.println("Data inserted successfully into student table");



            } catch (SQLException err) {

                System.out.println("ERROR: " + err);

            }

        } catch (ClassNotFoundException e) {

            System.out.println("MySQL JDBC driver not found");

        }

    }

}
