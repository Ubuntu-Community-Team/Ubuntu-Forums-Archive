---
title: "Can I use ONE mysql db on both Vista and Ubuntu?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by razzbar on 2009-08-14
I have a machine that came with Vista, and recently installed Ubuntu on a new partition. I have an apache server with mysql on the Vista partition, and would like to use the existing database from Ubuntu. I need to work on it from both operating systems. Need. To.

I've configured apache on Ubuntu to use the same document root that Vista is using, but can't figure out how to get mysql on the Ubuntu side to reach the mysql database on the Vista partition. 

I've changed the my.cnf file to point ' datadir' to point to the location of the database directory on the Vista side, and changed ownership of it, which stopped the "partition is full error' when starting mysql. I also made changes to the  /etc/apparmor.d/usr.sbin.mysqld as recommended in other threads. 

... but no luck. Yet. 

A symbolic link didn't help either. What should I try next? 

BTW, this is my firs post here, so extra thanks for any replies!

---

### Post by LowSky on 2009-08-14
Can I ask Why you need to access a database from two operating systems? But as long as you know the location of the database and the hostname and password, log into it should be a breeze.

open a terminal and try

```
 mysql -h {hostname} -u username -p {databasename}
Password: {your password}
```

if that doesn't work maybe you need sudo powers

```
 sudo mysql -h {hostname} -u username -p {databasename}
Password: {your password}
```

[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by razzbar on 2009-08-14
I have both Ubuntu and Vista on one machine, and although I prefer developing on the Ubuntu partition, sometimes I have to be running Vista. 

To clarify, there are TWO installations of mysql, on the machine. One on Ubuntu, one on Vista. Each mysql server has its own data directory. I want there to be ONE data directory, so that I can access the same data whether I'm running Ubuntu or Vista.When I'm running Ubuntu, mysql doesn't even know the database on the Vista side exists. And vice-versa.

The hostname is going to be 'localhost' regardless of which OS I'm running, but 'localhost' is going to be reading from different data directories, depending on which OS. I want BOTH operating systems to read the SAME data.

---

### Post by ainsworth_t on 2009-08-14
Instead of installing MySQL in both Vista and Ubuntu, you could try installing it in a VirutalBox VM. Setup a common data partition for both Vista and Ubuntu, point the VBox folder settings to save the VDI and vbox settings to the common data partition, create the VM, then you should be able to access it from both OSes (you'll have to manually add the VM to the VirtualBox inventory in one of the OS environments).

---

### Post by razzbar on 2009-08-14
Thank you for the advice. I'm not familiar with VirtualBox. 

I solved the problem just a minute ago by simply creating a symbolic link to the Vista side database folder that I was interested in. The only 'gotcha' is that the Vista partition has to be mounted. Apparently, this does not happen automatically on logging into the system, but *does* happen automatically when you try to look at it in Nautilus -- which disguises the fact that it has to be mounted. 

Thanks for your advice.

---

### Post by ainsworth_t on 2009-08-17
You can edit /etc/fstab to auto-mount your Vista partition every time you boot into Ubuntu.

---

