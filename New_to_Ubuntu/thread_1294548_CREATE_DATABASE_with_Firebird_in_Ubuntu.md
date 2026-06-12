---
title: "CREATE DATABASE with Firebird in Ubuntu"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Don Bowen on 2009-10-18
Is there an Ubuntu forum for the SQL database Firebird?

I've been successful with it on Windows... but not with Ubuntu...... yet.

Specifically, I want to know how to CREATE a database at the ISQL command line interface.

>CREATE DATABASE '/home/don/fred.fdb' user 'SYSDBA' password 'masterkey';

doesn't work... like it does in windows...it gives the

Statement failed, SQLCODE = -902
Unable to complete network request to host "localhost".
-Failed to establish a connection.
-Connection refused

error.  I understand the concept of making a connection to the network to use firebird.... that's what it was made to do after all, but this is a local database.
maybe the 3050 port needs to be open with Ubuntu?
Any help will be much appreciated.

---

