---
title: "MS Access database on a Ubuntu machine."
date: 2010-02-01
forum: New to Ubuntu
---

### Post by HunterjWizard on 2010-02-01
I'm trying to use Ubuntu to get around the 10-user file sharing restriction on Windows XP. I work for a small company using an archaic Access 97-based database system(the owner absolutely flat out refuses to upgrade). Since we now have 11 employees I had the idea to put the database file on a linux box that wouldn't have the same user restrictions.

There's nothing to be done on the back-end besides share a file across the network. 

Previously I had used a knoppix system with a FAT32 partition but the results were fairly slow. I'm wondering if anyone can advise me on the best way to go about this. 

The 'Server' is currently dual-booting to windows XP and Ubuntu Linux, there is also a FAT32 partition on there and a second hard drive with no partitions to speak of. The database file is around 300 megs.

Thanks in advance.

---

### Post by cariboo on 2010-02-03
You could just place all the files on the server, it won't make a difference whether it is running 32-bit or 64-bit. Then just create a link to the application on the Windows desktops. You may have to set the user and group ownership to one that everyone can access as well as read and write permissions.

You will of course have to set up Samba in order for the Windows desktops to be able to access the application.

I have an Access application that I'm converting to python and sqlite, as the original developer no longer wants to have anything to do with it, and there are still companies out there that are using it.

I have one question, though. Why have a dual boot server? A server once setup properly, should just be put in a corner and run headless, until everyone forgets that it's even there.

---

### Post by oldfred on 2010-02-04
Access is not the best database tool for network use. It will copy the entire access file over the network each time is is updated.

Before I retired, I had the reputation in the corp of using a lot of Access dbs which corporate did not prefer. Separately a contractor created a VB program for our shipping department and used an Access db for the records. Corporate insisted for security that the Access file be on a corporate server even though the application was local. It started ok, but as the data grew we started to complain about the network getting slower. Corporate had lots of excuses but bottom line was the Access file was getting larger and using all the bandwidth. We moved it back to local but it still consumed a lot of local bandwidth. And anytime we had network issues it was Fred doing something with Access. I created most of my mutiuse Access files as front end/back end databases and then if more that a few users converted the backend to SQL server.  I would suggest looking at converting to a SQL db for the data on your server and link to the data in Access.

---

### Post by gjosef on 2011-02-10
> **oldfred said:**
>  I created most of my mutiuse Access files as front end/back end databases and then if more that a few users converted the backend to SQL server.  I would suggest looking at converting to a SQL db for the data on your server and link to the data in Access.

What server backends is Access compatible with? Granted, I only tested this five or six years ago, but back then, the Access front-end was not getting along well with a MySQL*backend. MS*SQL*Server will work of course, but that's not an open source solution and it won't run on Linux.

---

### Post by indytim on 2011-02-10
On a longer term basis, I would strongly recommend a plan to dump Access and migrate to a full featured relational database. I would suggest that you take a good look at our near-native applications in the form of a LAMP server.  This configuration is built for the web and has the scaling factors that allow easy growth should the need arise.

The downside on this possibly for you is the initial learning curve.  Once you've accomplished this, it becomes very easy to maintain and grow your applications.

I'm the designer of a very large scale corporate MIS.  We're serving up a user base of 2500+ on 5 continents.  We're currently using 6 inter-related databases with around 300 cross linked tables.

My thoughts.

IndyTim / DataMan

---

### Post by gjosef on 2011-02-10
> **indytim said:**
> On a longer term basis, I would strongly recommend a plan to dump Access and migrate to a full featured relational database.

Everyone who has done heavier projects with Access knows that it's not professional grade. It's also a stagnated product. But it does have one small advantage: non-developers with good general computer experience can use it for quickly creating temporary or customized forms and reports. Handy in a smaller team where work processes need to be flexible and there is not a full-blown IT*department available to develop all potentially needed functions.
If I knew another quick and handy form and report builder, then I could probably scrap access altogether.

---

### Post by oldfred on 2011-02-11
Theoretically any ODBC data base should work. But even conversion from Access to MS SQL was not automatic. Some datatypes did not convert consistently, some functions (round) were different in T-SQL and Access, so whatever you use is not simple as running just Access.

I also am trying to learn python with sqlite to see what I can do, but now that I am not working I have no pressure to make something work.

I also saved these links, but have not used them.

You could also look at this project :
[http://www.kexi-project.org/](http://www.kexi-project.org/)

KDE but works in Gnome
[http://knoda.sourceforge.net/](http://knoda.sourceforge.net/)

Uses postgreSQL but only the one's it creates
[http://www.glom.org/wiki/index.php?title=Main_Page](http://www.glom.org/wiki/index.php?title=Main_Page)

OpenOffice database

---

### Post by drdos2006 on 2011-02-11
This may be of some help.

[http://dabodev.com/](http://dabodev.com/)
[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)
[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)

regards

---

### Post by Cdn~innu on 2011-02-11
You can create two access db's, one with all the forms, queries, reports etc. in it and a backend db with just the tables to reduce net traffic load with multi users. Each user W/S gets a copy of the front end db and that links to the comman backend (table only) db. 

Open Office Base is getting closer to being similar, however has not yet built a group of users familiar enough to make it as user friendly as access at this point. Any of the other db's like sql based ones (mysql, HSQL, etc) don't have quite flexibility in designing reports and forms as access without purchasing third party report applications etc.

The access database operates with it's own generic housekeeping/logging user that requires both read and write access to whatever file system it is located on; that is in addition to the workgroup user that is logged into the ms access application. That is why a network share has to be open to basically everybody. The security is built into the workgroup file and user permissions are set up there. The flexibility is built in to give read write design and own permissions on each individual object in the database. There is also the capability to define sub groups within a group and adjust group permissions so that you just add any given user to one of the specific subgroups and the permissions are set. The workgroup file has to be a custom one you create yourself and place on a common network share, with the back end DB. then everyone joins that workgroup when running that db. I believe their is a command line switch that can be used to specify the workgroup security file to use with a specific db. That way the workstation can use the default open one when not using the shared db.

---

