---
title: "SQL on Ubuntu"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by chatterjee on 2010-03-11
I just want to know if there is any software in which we can apply the SQL commands as we do in oracle etc.I just want to use the basic commands create,select update etc.What is the option.

---

### Post by Siph0n on 2010-03-11
Are you looking for something like MySQL?

---

### Post by Mighty_Joe on 2010-03-11
Are you looking to run the server locally (i.e. store the database on your local machine) or do you just want to run a client to access a remote SQL database?  Either way, Ubuntu has you covered.

---

### Post by TurnOfTide on 2010-03-11
I wish toad supported linux, but they don't. However you can use this:

[http://www.oracle.com/technology/software/products/sql/index.html](http://www.oracle.com/technology/software/products/sql/index.html)

---

### Post by chatterjee on 2010-03-11
I'm a newbie in SQL.Actually I'm now learning how to use the commands in it i.e. to create table,update and delete data in it etc.I can do these things in Oracle (in Windows),now I'm searching for a piece of software(in Ubuntu) which will allow me to run those commands so that I can learn SQL.

---

### Post by Mighty_Joe on 2010-03-12
You haven't answered my question.  Do you want to have the database local or not?  
Oracle makes a Linux release, but I don't think it is supported under Ubuntu ([see here]("http://www.orafaq.com/wiki/Operating_system")).  
Siph0n mentioned MySql.  There are other SQL database available for Ubuntu: PostgreSQL, for instance.
Again, you must ask yourself a question: do you want to learn SQL or Oracle?  Oracle has some particular quirks so if you want to learn it, you'd be better served getting a platform that supports it.  If you just want to bounce SQL queries off a server, install MySql and have at it.

---

### Post by r-senior on 2010-03-12
If you want Oracle specifically, Oracle XE works fine on Ubuntu. It's a while since I had it installed and I don't remember if it provides a standalone SQL*Plus, but the web interface to the server has a SQL command area where you can enter queries, etc.

[http://www.oracle.com/technology/products/database/xe/index.html]("http://www.oracle.com/technology/products/database/xe/index.html")

There's an outdated guide to installing Oracle XE on Ubuntu here:

[https://help.ubuntu.com/community/Oracle10gDapper]("https://help.ubuntu.com/community/Oracle10gDapper")

You might want to look at Oracle SQL Developer, which looks like it's a Java app, so would run on Ubuntu (although there's no .deb to install). IDEs like Netbeans and Eclipse also have database plugins where you can run SQL.

---

### Post by bluelamp999 on 2010-03-12
> **r-senior said:**
> If you want Oracle specifically, Oracle XE works fine on Ubuntu. It's a while since I had it installed and I don't remember if it provides a standalone SQL*Plus, but the web interface to the server has a SQL command area where you can enter queries, etc.

[http://www.oracle.com/technology/products/database/xe/index.html]("http://www.oracle.com/technology/products/database/xe/index.html")

There's an outdated guide to installing Oracle XE on Ubuntu here:

[https://help.ubuntu.com/community/Oracle10gDapper]("https://help.ubuntu.com/community/Oracle10gDapper")

You might want to look at Oracle SQL Developer, which looks like it's a Java app, so would run on Ubuntu (although there's no .deb to install). IDEs like Netbeans and Eclipse also have database plugins where you can run SQL.

I concur with this advice. Oracle XE and Oracle SQL Developer both run well on Ubuntu and both are free! As in beer...

---

### Post by Method X on 2010-03-12
You need LAMP(Linux Apache MySQL Php).

---

### Post by Mighty_Joe on 2010-03-12
> **bluelamp999 said:**
> As in beer...

Just to nitpick, not "free as in beer", but "free with the following restrictions":
> 
Can I use Oracle Database XE for free deployment?
Oracle Database XE is free for runtime usage with the following limitations:
• Supports up to 4GB of user data (in addition to Oracle system data)
• Single instance only of Oracle Database XE on any server
• May be installed on a multiple CPU server, but only executes on one processor in any server
• May be installed on a server with any amount of memory, but will only use up to 1GB RAM of available memory
[Oracle Database XE FAQ]("http://www.oracle.com/technology/products/database/xe/pdf/dbxe_faq.pdf")

For our OP's purposes, it sounds fine.

[QUOTE=Method X]You need LAMP(Linux Apache MySQL Php). [/QUOTE]

Why does the OP "need" LAMP if he just wants to learn SQL?

---

