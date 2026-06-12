---
title: "starting sql"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by manish411 on 2011-02-01
I am starting a course in database management systems. We are learning sql commands and working with queries theoretically but I want to practice them practically . What is the basic things to install. I would like to start by writing code instead of using an IDE.

---

### Post by bleutyler on 2011-02-01
I do not have access to my Ubuntu box at the moment, but have you tried:

```
sudo apt-get install mysql
```

If that does not work, you have [http://dev.mysql.com/downloads/mysql/](http://dev.mysql.com/downloads/mysql/) option.

To help you, the manual which covers everything mySQL from the developers themselves can be found at:

[http://dev.mysql.com/doc/refman/5.5/en/](http://dev.mysql.com/doc/refman/5.5/en/)

---

### Post by mcduck on 2011-02-01
You should check the official Ubuntu Server guide.

[https://help.ubuntu.com/10.10/serverguide/C/mysql.html]("https://help.ubuntu.com/10.10/serverguide/C/mysql.html")

---

### Post by The Cog on 2011-02-01
The easiest way to get started is to install the SQLite Manager plugin to firefox. This allows you to create single-file databases and use them either with the simple GUI or using SQL commands. Despite being single-file databases, they are full featured and capable of storing gigabytes of data. No server to set up and configure first. The only disadvantage is that sqlite isn't a database server so you can't connect to it remotely - it's intended for local applications. Just what you need for sql practice.

---

