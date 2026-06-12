---
title: "How do I connect to a Microsoft Access .mdb file?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by bwallum on 2010-01-17
Hi

I have a legacy Access database file that I would like to use. I am a complete beginner when it comes to running databases in Ubuntu.

Any suggestions as to how I can use the mdb file?

---

### Post by Muttley99 on 2010-01-17
Have you installed 'openoffice' and used their database software? as far as I'm aware they are compatible.

[HTML]sudo apt-get install openoffice
[/HTML]
from the terminal

---

### Post by Sir Jasper on 2010-01-17
Hi,

There is a good chance that OpenOffice (in your repository if not already installed) can read and write to Microsoft Access files.

Either just try it. or google say, openoffice microsoft access to read about it.

My regards

---

### Post by Roger Allott on 2010-01-17
I've never been able to get OpenOffice to read an mdb file properly, but there's an app called 'MDB Viewer' that is good for that.

Open Synaptic and search for 'mdb'. The key package you need is mdbtools-gmdb, but you'll find a few others there that may help you too.

---

### Post by bodhi.zazen on 2010-01-17
You could also look at this project :

[http://www.kexi-project.org/](http://www.kexi-project.org/)

---

### Post by oldfred on 2010-01-17
OpenOffice in windows will open a MS Access file but I have not gotten it to work in Linux. I tried installing an ODBC connection and thought I had all the settings but it did not work.

I did find this:
Convert from MSAccess to sqlite using Jackcess
[http://code.google.com/p/mdb-sqlite/](http://code.google.com/p/mdb-sqlite/)
Java MSAccess tool
[http://jackcess.sourceforge.net/](http://jackcess.sourceforge.net/)

In the repository is mdbtools, libmdbtools, and mdbtools-gmdb that allows conversion and export.

---

### Post by Sir Jasper on 2010-01-17
Hi,

As a last resort this is what Cheesemill said on this forum some 24 hours ago:

----------------------------
Did you read my post in your previous thread about this?
[http://ubuntuforums.org/showpost.php...0&postcount=11](http://ubuntuforums.org/showpost.php...0&postcount=11)

Just follow the instructions here to install wine, then run the Office 2007 installer. Done.

You can't use wine to run programs that are already installed on a Windows drive, you have to install them again in Ubuntu.
----------------------------
So if Wine will run Office 2007 programs I assume it will also run earlier versions as well.

---

### Post by bwallum on 2010-01-17
MDB Viewer (see Roger Allott) allows read only access of tables and the ability to export but no structure (queries, forms, reports, modules are not available.)

OOo Forum seems to be quiet (ish) on the subject considering the number of people that must be keen to use old mdb databases.

I've not tried it in Wine, I have never had any real success (full implementation) with Windows apps in Wine although I am currently trying to get a Windows proprietory application (Farmplan) running at the moment and haven't given in yet.

Anybody have any experience with mySQL? Now that I can access the data I might just as well set up the tables in mySQL and work from there to restore the functionality. What is(are) the name(s) of the packages I need to set up mySQL tables and get a gui to do simple manipulations and reports?

I'll duck kexi for now, it needs KDE desktop apparently and a few other bits.

---

### Post by bodhi.zazen on 2010-01-17
mysql is reasonably easy to install and manage. You can manage the database directly with mysql commands, although you may also use web based graphical tools such as phpmyadmin

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

google will lead you to mysql commands, here is one of many cheat sheets :

[http://nparikh.org/unix/mysql.php](http://nparikh.org/unix/mysql.php)

---

### Post by Roger Allott on 2010-01-17
I don't like the recommendation to use phpmyadmin. For people migrating from Windows, I suggest the use of MySQL Administrator and MySQL Query Browser as being far more intuitive.

---

### Post by bwallum on 2010-01-18
OK, I'll try them all. After a fair bit of googling I found this way to start up mySQL:-```
bob@ubuntu-bob:~$ mysql -h 127.0.0.1 -u root -p
```I got the following returned> Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 36
Server version: 5.1.37-1ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>I think the 127.0.0.1 refers to the 'localhost' address and is the address for the mySQL server. I think I've accessed that server as root (I would prefer to access as user). -h is followed by the hostname, -u by the user and -p prompts for the user password. I have managed to get a database up and running:-> mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.00 sec)

mysql> create database cman;
Query OK, 1 row affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| cman               | 
| mysql              | 
+--------------------+
3 rows in set (0.00 sec)

mysql>A gui would be better for me though. I try the command ```
phpmyadmin
```in a terminal and a couple of seconds transpire, then the prompt returns, without a gui. I have tried gksudo and sudo as well. 

How do I start the phpmyadmin gui?

I also have MySQL Administrator and MySQL Query Browser showing in Applications>Programming. I can start them both using root.

How do I set up the appropriate information in MySQL Administrator and MySQL Query Browser to run as bob?

My understanding of mySQL is that the database runs on a server, which can be a virtual server running on my pc. I connect to the database with an administration client, which is phpmyadmin or MySQL Administrator and connect a client application to the database to get some meaningful results, such as OOo Base.

I'm sure it's easy once you know how but I'm not sure I have even the architecture concepts right yet.

---

### Post by bodhi.zazen on 2010-01-18
As indicated earlier, phpmyadmin is but one of several tools.

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by bwallum on 2010-01-18
Thanks bodhi!> Once phpMyAdmin is installed point your browser to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to start using it.That's just what I needed, good steer!

I can now see mySQL db with two tools, immediately I can see the Apache2 server and the php app. The mist is lifting! Thanks again everyone.

---

### Post by bwallum on 2010-01-18
Flushed with the success of getting my first MySQL database started I thought I would take some r and r and try Kexi.

It's up and running (using KDE in the background so no impact on my Gnome desktop). It appears to be able to read data from a mdb file but when I try it it gets to the point of import and tells me "No appropriate migration driver found" Do you know of one bodhi?

---

### Post by bodhi.zazen on 2010-01-18
> **bwallum said:**
> Flushed with the success of getting my first MySQL database started I thought I would take some r and r and try Kexi.

It's up and running (using KDE in the background so no impact on my Gnome desktop). It appears to be able to read data from a mdb file but when I try it it gets to the point of import and tells me "No appropriate migration driver found" Do you know of one bodhi?

I have not used a MS Access db for years and years. Last time I did I migrated it to mysql , although the tool I used at the time was vendor specific.

---

### Post by bwallum on 2010-01-23
Ok, some success now with simple tools. This is what I did to extract the schema (tables and fields) from a Microsoft Access 2003 mdb file, placed on my Desktop. You need an empty MySQL database started to do this. 

Install mdbtools from the repository or ```
sudo apt-get install mdbtools
```Then run```
mdb-schema /home/ME/Desktop/MYDATABASE.mdb
```A sql statement results, not perfect but just remove blank lines and take out the excess tabs. You need only a space between the field name and the field type, e.g. FieldName Text(100). The drop statements won't be applicable first time through but if you want to change the script then make sure you include the drop commands for any tables with the same name before recreating them. This is now a sql file that you can run in your MySQL db. First, though, I recommend you copy and paste the output to a text file. You can then manipulate it with tools such as *replace* in gedit to get the file right. Save your new file as a txt file.

Once you have a file that you hope will run connect to your MySQL database. I used [phpmyadmin]("https://help.ubuntu.com/community/phpMyAdmin")```
sudo apt-get install phpmyadmin
```To open, open a browser and type in [http://localhost/phpmyadmin](http://localhost/phpmyadmin). Now find the import tab and type the path and filename of your new file or browse for it. Press the Go button. phpmyadmin will tell you if the file runs successfully (or not). I managed a few syntax errors, all down to things like spaces in table names.

That's the tables and fields imported.

To populate the tables with data run```
mdb-export -I /home/ME/Desktop/MYDATABASE.mdb ONEOFMYTables | sed -e 's/)$/)\;/'
```The sed statement is to put a ";" at the end of each line to keep MySQL happy. You will get a return of data for any one table that you select. Copy and paste the terminal output to a text file as before and then import it into MySQL in the same way as importing the db schema above. In case you think I'm a sed guru and ask me questions I can't answer, [this is where I got the steer from]("http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/"). Note that Niall has a neat way to enter the schema and data directly into a MySQL database without the text file bit that I resorted to. If you get Niall's pipe to mysql to work do post back the solution.

As for views, forms and reports, I have found nothing to translate these. It is necessary to re write these in MySQL I think. Do post back if you know better.

Once you have a MySQL database running then Kexi connects to it easily and the Kexi functionality is similar to Access. 

I am still trying using OOo Base but it is possible and easy apparently. I'm just not quite getting it at the moment. Anybody know how to set up an ODBC or JDBC connection?

---

### Post by oldfred on 2010-01-23
I had tried to set up an ODBC connection for Access but never got it to work. I followed this info for how to set up ODBC even though it was for another db.

For a different database but shows ODBCConfig
[http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux](http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux)

see A neophyte's guide tab in 
[http://www.unixodbc.org/](http://www.unixodbc.org/)
Doing this as root will create and edit the /usr/local/etc/odbcinst.ini (for the driver info) and /usr/local/etc/odbc.ini (for the system DSN) files.

The easysoft products are not free, but they do have some info on installing.
[http://www.easysoft.com/developer/interfaces/odbc/linux.html](http://www.easysoft.com/developer/interfaces/odbc/linux.html)
[http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc](http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc)

---

### Post by bwallum on 2010-01-23
Could maybe short circuit this by saying I'm trying to set up an ODBC betwen OOo Base and MySQL, sorry to confuse.

---

### Post by oldfred on 2010-01-23
An ODBC config is independent of where your are going to use it. The screens shown in the examples are exactly the screens you need to use, except you have to put in your parameters for MySQL. It was meant as an example on all the screens you have to use to create the ODBC connection. You then can choose that connection in various apps like OObase.

---

### Post by bwallum on 2010-01-25
Wow, some journey this one, all I wanted to do was use an old Access db and I now know how to set up a server based db and connect to it. This is my experience in attempting to link Open Office Base (aka OOo Database but it is really a client when you link to a 'proper' database like MySQL) to the MySQL server set up and loaded with data in the posts above.

It helped me a lot to consider the diagram found on one of Oldfred's links. Unfortunately I couldn't find it again so drew my own, pdf attached. Apologies and thanks to the creative individual that did the original.

The biggest mistake I made was thinking that OOo Base simply needed a MySQL ODBC driver. It does, but not simply. It needs a CONNECTION. The connection uses the MySQL ODBC driver but also includes who makes the connection and where the connection is made.

To make a connection, a driver/connection manager is needed. I found two. An old established and commonly used connection manager called unixodbc. It's in the repositories. unixodbc-bin (community supported) gives a gui.
To get it,```
sudo apt-get install unixodbc-bin
```and to run it,```
gksudo ODBCConfig
```

The gui needs to know where the driver is under the Drivers tab and also where the database is under the System DSN tab. Screen shots attached for libmyodbc.so driver and path, database named cman, default location url localhost, and default port 3306. You can call the connection whatever you like.

The second manager is in beta and is called MySQL Workbench, available [*here.*]("http://dev.mysql.com/downloads/workbench/5.1.html") Screenshot attached.

It is designed to replace MySQL Administrator and MySQL Query Browser when mature but also has driver/connection management built in and db design too. Loads of information to help unravel what is going on and very easy to set up MySQL and OOo Base.

That's about me done I think. I'm now about to explore how OOo and MySQL interact when forms and reports are configured in OOo. Thanks to everybody that helped me get here.

There may be a shortcut for anybody having to use Access mdb files regularly. Easysoft claim to have an odbc linux driver for mdb files and you can [*try in on a 14day trial*]("http://www.easysoft.com/products/data_access/odbc-access-driver/index.html?location=Applications%20menu"). Usual proprietary hassle with 'security keys' etc. Managed to download it but not got it working yet. 

Best Regards
Bob

---

### Post by GuiGuy on 2010-04-02
> **Roger Allott said:**
> I don't like the recommendation to use phpmyadmin. For people migrating from Windows, I suggest the use of MySQL Administrator and MySQL Query Browser as being far more intuitive.

... I'd add "mysql Workbench" to the list...

---

