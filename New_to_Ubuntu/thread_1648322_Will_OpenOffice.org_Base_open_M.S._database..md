---
title: "Will OpenOffice.org Base open M.S. database."
date: 2010-12-18
forum: New to Ubuntu
---

### Post by gordon33 on 2010-12-18
Hello All

Will OpenOffice.org Base open a M.S. database.  I woke up the database on my Ubuntu 10.04 by following the process below.

Go to System>Administration>Synaptic package Manager and enter the search term
Code: OpenOffice.org Base

I have a Microsoft Access database made before 1997. Will it open in the OpenOffice.org Base.  Or would it be easier to make up a new database?

Presently the Access file is on a 3.5 " floppy.  I will have to get it moved to a flash stick.


Gordon33

---

### Post by stmiller on 2010-12-18
May be possible:

[http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access](http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access)

---

### Post by oldfred on 2010-12-18
I think that only works in windows as windows will then have the JET program to open the database already installed. 

I converted one database that was from Access 2000, a while back. But I used Kexi and had to add some drivers.

I think you can use MDB Viewer and copy each table to a  text file. While it shows queries, forms etc it does not display them.

None of the copies will include forms, reports or any code behind those forms and reports. 

Microsoft Access in Wine - some success
[http://ubuntuforums.org/showthread.php?t=1113065](http://ubuntuforums.org/showthread.php?t=1113065)
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by gordon33 on 2010-12-18
Hello oldfred, and stmiller

Thank you for the information.

It looks as if this will take a little bit of time.  I was hoping it would be easy.

Gordon33

---

### Post by marl30 on 2010-12-18
I have used Kexi from the Koffice suit to successfully open Access 2003 database. Maybe it could be of help to you. What I did was to choose import existing database, then browse to the file, and I was able to view and edit the database.

---

