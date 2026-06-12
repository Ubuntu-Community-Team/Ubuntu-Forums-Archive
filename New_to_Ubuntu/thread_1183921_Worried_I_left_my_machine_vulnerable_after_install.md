---
title: "Worried I left my machine vulnerable after installing mysql"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by speedwinder on 2009-06-10
I'm not sure if should've posted this in the security section but this is a pretty begginer problem I have and I'm having a panick attack right now.

I wanted to install MythTV and it required that I intall mysql server 5.1 and its components. I know very little about mysql and have no desire to use it. While it was being installed it prompted me to enter a root password. I just clicked cancel. It later prompted me again and I just clicked forward without entering a password. It prompted me a third time and this time I did entered a password and clicked forward. It then assigned me some random password.

I read a little about mysql and learned that its something people use to share files and open source software. I typed mysql at the comand prompt and it immediately gave me the mysql> prompt. I don't think I was logged in as root but nonethless is started mysql without prompting me to enter a password. So I panicked. I don't want anybody accessing any of my files through mysql!

I immediately uninstalled every mysql component that was installed in package manager. I also deleted the directories /etc/mysql and /var/lib/mysql that were still there. Has this done away with any sort of access that that someone might have to my machine through mysql? Please help!

---

### Post by ubersolid on 2009-06-10
run ```
mysql_secure_installation
``` in the terminal and set a password for mysql root, it is NOT the same as root on you system btw. Then just accept the defaults and you will be fine.

---

### Post by ChrisDerson on 2009-06-10
Just to add to ubersolid's comments, MySQL is not a file sharing tool, it's a database - it stores data.  It's used by an enourmous number of applications, and it's very likely that you'll need to install it for something sooner or later.
MySQL is pretty secure, and does not provide access to the file system directly, while you are quite right to be cautious, in this case you have very little to worry about.
MySQL makes a big deal about passowrds because it is used in many large websites and commercial systems - systems that many users have potential access to.  For these systems being cautious about security makes a lot of sense.
Hope this helps set your mind at rest.

---

### Post by speedwinder on 2009-06-10
Thank you guys for your reply's. I feel a safer now knowing that it doesn't provide access to the file system directly. I tried reinstalling mysql to run mysql_secure_installation but it encountered some errors and I got a message saying it crashed. Probably because I had deleted those directories. I guess that means my files are pretty inaccessible which is what I want.

---

### Post by Celauran on 2009-06-10
> **speedwinder said:**
> I typed mysql at the comand prompt and it immediately gave me the mysql> prompt. I don't think I was logged in as root but nonethless is started mysql without prompting me to enter a password.

It did that because you didn't enter anything when prompted for a password. Had you provided a password when asked during the install, you would have been prompted for a password when using the mysql command.

That aside, as others have mentioned, MySQL is a database engine, not a file sharing utility. Additionally, the default configuration only allows access from the localhost, so they'd have to already have gotten into your machine.

---

### Post by johnl on 2009-06-10
I think it's also important to note that by default, mysql will only listen for connections from your local machine.   You would have to modify the configuration in order for someone to be able to access it remotely.

Edit: beat me to it :)

---

### Post by The Cog on 2009-06-10
MySQL is a database engine. It stores data tables in its own directory (/var/lib/mysql I think). If it is configured to do so, it will listen for incoming connections, but a default install only acccepts connections from the local machine. Even if listening for remote connections, you have to configure MySQL with users and grant them permission to connect remotely, and specify which data tables they area allowed to see. Even if remote users have permissions to see data tables, the can't access the filesystem.

You will need to reinstall MySQL if you want to use MythTV - it uses MySQL to store the program guide, recording schedule, and all the other stuff it needs to store.

---

### Post by speedwinder on 2009-06-11
Thanks everybody. That clears things up. I think I understand this creature they call MySQL a little better now.

---

