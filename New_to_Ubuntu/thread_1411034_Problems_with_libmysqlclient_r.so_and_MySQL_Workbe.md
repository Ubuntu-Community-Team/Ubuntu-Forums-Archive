---
title: "Problems with libmysqlclient_r.so and MySQL Workbench"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by tormok on 2010-02-19
I have installed Ubuntu 9.10 for the first time 2 days ago, and now I have run into a small problem.

I need to connect to some remote databases and plan to use MySQL Workbench for that.

I have downloaded the **mysql-workbench-oss-5.1.18a-1ubu904-i386.deb** from [http://dev.mysql.com/downloads/workbench](http://dev.mysql.com/downloads/workbench) and installed it using the Package Installer.

But when I use Workbench to connect to a remote database, I get the message:
> **Test connect failed**
Couldn't load library libmysqlclient_r.so: libmysqlclient_r.so: cannot open shared object file: No such file or directory

I then did some research and found this page: [https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench)

In a terminal i entered:
[FONT="Courier New"]sudo apt-get install liblua5.1-0 libzip1 libmysqlclient15off
sudo dpkg -i /home/tormok/Downloads/mysql-workbench-oss-5.1.18a-1ubu904-i386.deb[/FONT]

And I still get the same error, when I try to connect to the database.

I then tried:
[FONT="Courier New"]sudo apt-get remove liblua5.1-0 libzip1 libmysqlclient15off
sudo apt-get remove mysql-workbench-oss[/FONT]

and again:
[FONT="Courier New"]sudo apt-get install liblua5.1-0 libzip1 libmysqlclient15off
sudo dpkg -i /home/tormok/Downloads/mysql-workbench-oss-5.1.18a-1ubu904-i386.deb[/FONT]

And I can still get the same error message.

What do I do now?

---

### Post by tormok on 2010-02-19
I solved it.

I opened Synaptic Package Manager and installed **libmysql++3** and **libmysql++-dev**, and no longer get the error message.

:)

---

### Post by iburry on 2010-03-18
This was exactly what I was looking for. Thanks =)

---

### Post by CeltaWeb on 2010-05-02
> **tormok said:**
> I solved it.

I opened Synaptic Package Manager and installed **libmysql++3** and **libmysql++-dev**, and no longer get the error message.

:)

Great this is exactly what I needed!!

After searching through tonnes of posts this is all you need
Thanks

Im impressed with Workbench, the Reverse and Forward Engineer along with the synchronize functions are really cool

---

### Post by mudar123 on 2010-06-09
**libmysql++3** and **libmysql++-dev **didn't work for me...

my solution was installing [B]Workbench 5.2.22 RC 2
[/B]

---

