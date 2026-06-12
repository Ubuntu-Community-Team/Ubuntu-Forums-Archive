---
title: "java program + my logic"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by navaneethan on 2010-09-14
```
import java.io.*;
import java.sql.*;

public class MyInsert
{
	public static void main(String args[])
	{
		_String string[] =new String[10];_
		InputStreamReader input = new InputStreamReader(System.in);
		BufferedReader reader = new BufferedReader(input);

		System.out.println(" ENTER ID:");
		_string[0] = Integer.parseInt(reader.readInt());_
		
		
		System.out.println(" ENTER NAME:");
		string[1] = reader.readLine();

		System.out.println(" ENTER GENDER:");
		string[2] = reader.readLine();

		System.out.println(" ENTER DOB:");
		string[3] = reader.readLine();

		System.out.println(" ENTER QUALIFICATION:");
		string[4] = reader.readLine();

		System.out.println(" ENTER ADDRESS:");
		string[5] = reader.readLine();

		System.out.println(" ENTER EMAIL:");
		string[6] = reader.readLine();

		System.out.println(" ENTER PHONE:");
		string[7] = reader.readLine();

		System.out.println(" ENTER INTEREST:");
		string[8] = reader.readLine();                
		

		try {
			Class.forName ("com.mysql.jdbc.Driver");				
			Connection conn = DriverManager.getConnection ("jdbc:mysql://localhost/nava_work", "root", "nava");
	
			Statement stat = conn.createStatement();	
			
			ResultSet result = stat.executeQuery("INSERT INTO STUDENT VALUES(_string[0],string[1],string[2],string[3],string[4],string[5],string[6],string[7],string[8]"_);
			
			System.out.println("RECORD IS INSERTED ");
			
				
				System.out.println("");
			
			conn.close();
		}catch (Exception e) 
			{
				System.out.println("EXCEPTION IS:"+e.getMessage());	
			}
				
	}

	}


```

This program is used to insert the value in a table from the user,I have done it in my own logic,Hope it is correct but syntactically goes wrong.May you help to find out? especially underlined statements makes me dubious?Is it possible the underlined statements?

---

### Post by fly-by-night on 2010-09-14
mmm...

Programming and Development:
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by lykeion on 2010-09-15
There are lots to be said about your code, however I'm gonna concentrate on your two underlined code lines.
[PHP]String string[] = new String[10];[/PHP]Yes this is the way you declare a string array with 10 elements.
But in your code you only fill it up with 9 elements?
Also every time you write something that's repetitive (like your print & read lines) you should be thinking "isn't it better to do this in a loop?"

[PHP]string[0] = Integer.parseInt(reader.readInt());[/PHP]
This does not compile. BufferedReader has no method called readInt() Why don't you use java.util.Scanner instead, it has a nextInt() method to read integers?
Also if the ID column in your database is a primary key of the table (not a personal id nr or something) you usually don't let users add it themselves, instead set it as auto incremented.

A great resource to learn how to program in Java - both logic and syntax - is to read and look at the examples of the _[Sun Java Tutorials]("http://download.oracle.com/javase/tutorial/")_.
Some pages you should start looking at:
[LIST]
[*]_[Language Basics]("http://download.oracle.com/javase/tutorial/java/nutsandbolts")_
[*]_[Arrays]("http://download.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html")_
[*]_[JDBC]("http://download.oracle.com/javase/tutorial/jdbc")_
[/LIST]

---

