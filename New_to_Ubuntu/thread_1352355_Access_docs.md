---
title: "Access docs"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by always_smile on 2009-12-11
How can I open microsft access files ,it gives me this error message when I try to open a file: There is no application installed for JET database files,thank you!

---

### Post by NoaHall on 2009-12-11
What file format are they saved in? (What's the bit on the end)?

---

### Post by lykwydchykyn on 2009-12-11
If you have .mdb files, you can import the DATA into OpenOffice.org base or Kexi.  That won't bring in forms, reports, stored queries, or stuff like that.  Just the tables.

---

### Post by always_smile on 2009-12-11
> **lykwydchykyn said:**
> If you have .mdb files, you can import the DATA into OpenOffice.org base or Kexi.  That won't bring in forms, reports, stored queries, or stuff like that.  Just the tables.
Yes the file is mdb but how can I import the data into openoffice,as a beginner I need to get easy steps to do it,thank you.

---

### Post by lykwydchykyn on 2009-12-11
> **always_smile said:**
> Yes the file is mdb but how can I import the data into openoffice,as a beginner I need to get easy steps to do it,thank you.

Ack; after testing it out myself it appears OpenOffice can no longer do this.  It used to, but apparently the driver for it was quite shoddy and they dropped support for it.

You can try Kexi, it still claims to support .mdb files, though I don't have an mdb file to test with.

The other, last-ditch-defense option is to install mdbtools and export all the tables to CSV files with the mdb-export command.

---

### Post by oldfred on 2009-12-11
I got close but not quite, I got a connection but not all the configuration:
Downloaded from synaptic:
unixodbc-bin
unixodbc
libmyodbc

then I followed the instructions here to configure a odbc connection:
[http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux](http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux)

---

### Post by joes7 on 2009-12-11
Get Wine.
[http://www.winehq.org](http://www.winehq.org)

---

### Post by llamabr on 2009-12-11
There is absolutely no way that wine is going to run microsoft access.  If you need microsoft access, you need to run it in windows.

---

### Post by mediax on 2010-01-07
I know I'm ages late on this, but I've just had the same problem and managed to work round it.

I found that MDB Viewer gave me access to my Access database tables, which was enough for my needs - I rewrote the queries I needed in SQL and I was off and running.

If you install mdbtools through Synaptic, you should get MDB Viewer appearing on your Applications, Office menu.

Good luck!

---

### Post by cyblance on 2010-01-15
Any help please? Sorry about piggy backing on this forum..:)

I am migrating a few of the company's boxes to ubuntu (open Office data).  A few of the remote machines are still using access. My questions are:
1.  Is it possible to get a single platform to hold tables that both access and OoDB can read and write too?
2. Which - if any - of these would be the most stable?
3. Is this even possible?

---

### Post by mediax on 2010-01-15
> **cyblance said:**
> 
1.  Is it possible to get a single platform to hold tables that both access and OoDB can read and write too?

I'm no expert, but I would have thought that setting up your tables as SQL databases and linking to them from Access and OoDB will achieve what you're after.

---

### Post by chinaski on 2011-03-22
> **mediax said:**
> I found that MDB Viewer gave me access to my Access database tables
[I've used MDB Viewer today]("http://gnulinuxarea.wordpress.com/2011/03/22/gnulinux-visualizzare-la-password-di-un-database-microsoft-access-mdb-con-mdb-viewer/") on a password protected Access 2003 database. 

It was enough to open the .mdb file then select Administrator and Users tables and then click on Data to view all the passwords. 

I am writing this info because it might be useful for someone.

---

