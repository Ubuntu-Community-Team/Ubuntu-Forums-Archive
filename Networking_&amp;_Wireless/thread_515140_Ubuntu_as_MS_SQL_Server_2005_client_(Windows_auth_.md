---
title: "Ubuntu as MS SQL Server 2005 client (Windows auth mode only)"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by getut on 2007-08-01
This is far from a newbie question and I've found a LITTLE info on joining a linux box to a Windows Active Directory domain, but I can find nothing on my ultimate goal... Be able to write and test T-SQL queries directed at a Microsoft SQL Server 2005 server. SQL server supports 3 authentication modes, SQL Server auth (SQL server specific username and passwords), Windows auth (Active Directory integrated username and passwords) and the third mode accepts both. Our server is in Windows auth mode and can't be changed.

How can I connect my Ubuntu machine to SQL server to write queries, stored procedures, etc.

This is the ONLY THING I have left that is keeping me from getting rid of my vmware install and dumping windows completely. Walkthroughs, examples, anything would be greatly appreciated, but the more specific the better.

---

### Post by sfarber53 on 2007-08-02
Maybe you should simply migrate the database to a Linux friendly product like MySQL or PostgresSQL.  It seems a waste of time to stay with an inferior database, even though what you propose should be possible.

Good luck with your project.

- Steve

---

### Post by fransdewet on 2007-12-26
Use Aqua Data Studio.  it costs money but works very very well.  It allows you to connect using NT Authentication.  We use it on our Windows machines and Linux machines and it just always works.

---

