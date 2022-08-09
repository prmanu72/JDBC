Steps to connect java to database
1. Import package java.sql.*
2.   a. Load driver (mysql connector for eclipse)


     b. register driver
3. Establish the connection
4. Create statement
5. Execute query
6. Process result
7. Close connection & statement
```java
package myjdbc;

// 1. Import package java.sql.*
// 2a. Load driver (mysql connector for eclipse)
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;



public class Demo {
	
	public static void main(String[] args) throws Exception {
		
		String url="jdbc:mysql://localhost:3306/prash";
		String username="root";
		String password="1234";
		String query = "select * from students";
		
		
		// 2b. register driver
		Class.forName("com.mysql.jdbc.Driver");
		
		// 3. Establish the connection
		Connection con = DriverManager.getConnection(url, username, password);
		
		// 4. Create statement
		Statement st = con.createStatement();
		
		// 5. Execute query
		ResultSet rs = st.executeQuery(query);
		
		// 6. process result
		while(rs.next()) {
			System.out.println(rs.getString(2));

		}
		
		
		// 7. Close connection & statement
		st.close();
		con.close();
	}

}
```
Output
```
Naruto
Sasuke
Sai
```
