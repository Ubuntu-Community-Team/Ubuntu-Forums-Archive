---
title: "Did i misconfigure odbc ?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by WitchCraft on 2011-07-02
I have a question on ODBC on Ubuntu 11.04

This is my cSharp test program:
```

using System;
using System.Data;
using System.Data.Odbc;

namespace ODBCtest
{
	class MainClass
	{
		
		
		// http://www.dbforums.com/delphi-c-etc/1608453-odbc-connection-mysql-c.html
		// http://www.java2s.com/Code/ASP/ADO.net-Database/MySQLODBCconnectionC.htm
		public static void MySQL_ODBC()
		{
			// Unhandled Exception: System.DllNotFoundException: libodbc.so
			// apt-get install unixodbc-dev
			
			string strProduct = "Test";
			strProduct = strProduct.Replace("'", "''");
			
			string strODBCConnectionString =
				"Driver={MySQL ODBC 3.51 Driver};Server=localhost;" +
				"Database=bind;UID=root;PWD=IsNotSecure123456;";
			
			
			strODBCConnectionString = 
				"Driver={MySQL};Server=localhost;" +
				"Database=bind;UID=root;PWD=IsNotSecure123456;";
			
			strODBCConnectionString = 
				"Driver={Firebird};Dbname=localhost:/var/lib/firebird/2.5/data/employee.fdb;" +
				"user=SYSDBA;Password=IsNotSecure123456;";
			
			
			strODBCConnectionString = 
				"Driver={MySQLDNS};Server=localhost;" +
				"Database=bind;UID=root;PWD=IsNotSecure123456;";
			
			strODBCConnectionString = 
			"DRIVER={MyODBC 3.51 Driver DSN};" + 
 			"SERVER=localhost;DATABASE=bind;" + 
 			"UID=root;PASSWORD=IsNotSecure123456;" + 
 			"OPTION=3"	;
			
			// http://www.connectionstrings.com/dsn
			
			// Working
			strODBCConnectionString = 
			"DSN=MySQL DNS;" +
			"UID=root;" + 
 			"PWD=IsNotSecure123456" ;
			
			
			// Working MySQL
			strODBCConnectionString = 
			"DSN=FooBar;" +
			"UID=root;" + 
 			"PWD=IsNotSecure123456" ;
			
			
			// Not really working
			strODBCConnectionString = 
			"DSN=Foo;" +
			"UID=sysdba;" + 
 			"PWD=IsNotSecure123456" ;
			
			
			// Not really working
			strODBCConnectionString = 
			"DSN=Foo;" + 
			"Driver=Firebird;" + 
			"DBName=localhost:/var/lib/firebird/2.5/data/employee.fdb;" + 
			"UID=sysdba;" + 
 			"PWD=IsNotSecure123456" ;
			
			// Error, 
			//Unhandled Exception: System.Data.Odbc.OdbcException: ERROR [HY000] 
			//[unixODBC][MySQL][ODBC 5.1 Driver]
			//Access denied for user 'sysdba'@'localhost' (using password: YES)
			
			/*
			strODBCConnectionString = 
			"DSN=\"Firebird Employees\";" + 
			"UID=sysdba;" + 
 			"PWD=IsNotSecure123456" ;
			*/
			
			
			
			
			// Working MySQL
			strODBCConnectionString = 
			"DSN=FooBar;" +
			"UID=root;" + 
 			"PWD=IsNotSecure123456" ;
			
			
			// Working
			strODBCConnectionString = 
			"DSN=Firebird Employees;" +
			"UID=SYSDBA;" + 
 			"PWD=IsNotSecure123456" ;
			
			strODBCConnectionString = 
			"DSN=Firebird_NoWhiteSpace;" +
			"" + //"Driver=Firebird;" + 
			"" + //@"DBName=/var/lib/firebird/2.5/data/employee.fdb;" + 
			"UID=sysdba;" + 
			"PWD=IsNotSecure123456";
			
			
			// http://www.devlist.com/ConnectionStringsPage.aspx
			
			
			Console.WriteLine(strODBCConnectionString);
			
			 OdbcConnection con = new OdbcConnection(strODBCConnectionString);
			
            string strSQL = @"INSERT INTO product(product) 
				                  VALUES( """ + strProduct + @""" );";
			
			//strSQL = @"SELECT rdb$get_context('SYSTEM', 'ENGINE_VERSION') 
            // as version from rdb$database;";
			
			con.Open();
			Console.WriteLine(strSQL);
			
            OdbcCommand cmd = new OdbcCommand(strSQL, con);
            try
            {
                cmd.ExecuteNonQuery();
            }
            catch (Exception ex)
            {
				Console.WriteLine(ex.Message);
            }
			finally
			{
				con.Close();
			}
			
		}
		
		
		public static void Main (string[] args)
		{
			MySQL_ODBC();
			Console.WriteLine ("Hello World!");
		}
	}
}

```


And these are my odbc config file:


odbc.ini
```

[ODBC Data Sources]
FooBar = "MySQL DNS"
FiEm = Foo

[Firebird Employees]
Description = Firebird
Driver = Firebird
Dbname = localhost:/var/lib/firebird/2.5/data/employee.fdb
User = sysdba
Password = IsNotSecure123
Role =
CharacterSet =
ReadOnly = No
NoWait = No



[Firebird_NoWhiteSpace]
Description = Firebird
Driver = Firebird
Dbname = localhost:/var/lib/firebird/2.5/data/employee.fdb
User = sysdba
Password = IsNotSecure123
Role =
CharacterSet =
ReadOnly = No
NoWait = No


[MySQL DNS]
Driver = /usr/lib/odbc/libmyodbc.so
SERVER = localhost
PORT = 3306
DATABASE = bind
OPTION = 3
USER = root
PASSWORD = IsNotSecure123
Role =
CharacterSet =
ReadOnly = No
NoWait = No

[MySQLVDNS]
Driver = MySQL
SERVER = localhost
PORT = 3306
DATABASE = bind
OPTION = 3
USER = root
PASSWORD = IsNotSecure123
Role =
CharacterSet =
ReadOnly = No
NoWait = No

```


odbcinst.ini
```

[Firebird]
Description = InterBase/Firebird ODBC Driver
Driver = /usr/lib/libOdbcFb.so
Setup = /usr/lib/libOdbcFbS.so
Threading = 1
FileUsage = 1
CPTimeout =
CPReuse =

[MySQL]
Description = ODBC for MySQL
Driver = /usr/lib/odbc/libmyodbc.so
Setup = /usr/lib/odbc/libodbcmyS.so
UsageCount = 2

```


Now my question:
I seem only to be able to access odbc via DSN.
Is there a reason for this ?

1. Shouldn't I be able to access ODBC by supplying all info myself ?
2. It works fine for MySQL, but it doesn't work for firebird.

ODBC itselfs seems to work fine however, as I can connect via isql. Did I misconfigure firebird somewhere ?

3. Must there be a plain text password in odbc.ini ?
Can't it be hashed or encrypted, or left away ?

4. What's the syntax for [ODBC Data Sources] ?
I would expect:
myrandom name = my odbc source

and then being able to access "my odbc source" with DSN="myrandom name" programmatically, but it doesn't seem to work that way...

---

### Post by WitchCraft on 2011-07-14
bump.

---

### Post by WitchCraft on 2011-07-15
bump.

---

