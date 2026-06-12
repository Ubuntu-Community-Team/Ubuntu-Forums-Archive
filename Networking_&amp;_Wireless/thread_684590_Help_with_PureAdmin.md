---
title: "Help with PureAdmin"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by alexv305 on 2008-02-01
I cant get Virtual Users to connect... Users existing on the machine can log in to the FTP accounts but Virtual users get a 530 Authentication Error... The 3 files that it selects for defaults for the user accounts are there and it creates users normally, for some reason they just cant get authenticated. It will say user found OK, then after PureAdmin requests a password it says "530 Authentication Error"...

Anyone know how to resolve this?

Im running Ubuntu 7.10..

---

### Post by patryk77 on 2008-02-01
How did you create the virtual users?

pure-pw useradd ?

Did you remember to do "pure-pw mkdb" after to commit changes?

Did you enable virtual users and tell it which file to use as the database?
If you can login with your regular account it is probably not enabled.

[http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users](http://download.pureftpd.org/pub/pure-ftpd/doc/README.Virtual-Users)

---

### Post by alexv305 on 2008-02-01
I added users with the manage users button in the pureadmin window.

I used the default database for users but I had to manually choose them in pureadmin.

---

### Post by vinu76jsr on 2008-04-01
It may sound trivial but pureftpd seem to be able to accept virtual users only through command line and then we can edit there restriction and properties through pureadmin

well it seemed to be my case and wherever I searched it seems the same however I myself felt the same I even tried and the graphical login in ubuntu and reinstall pureadmin and pure-ftpd but there seems no solution but to supply user through shell

hope it might help and somebody please correct me if I m wrong

---

### Post by Endolith on 2008-06-22
I installed PureAdmin v0.4 from the autopackage ( [http://purify.sourceforge.net/index.php?page=download](http://purify.sourceforge.net/index.php?page=download) ) and it actually saves the user names and information now, but I can't log in.  I get this using gFTP on my other machine on the same LAN:

```
Looking up serverhostname
Trying serverhostname:21
Connected to serverhostname:21
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 21:35. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
USER joe

331 User joe OK. Password required
PASS xxxx
530 Login authentication failed
Disconnecting from site serverhostname

```

But it says "User  OK" no matter what username I try to log in with, so I'm not sure if it really recognizes the user or not.  The log file for PureAdmin says:

```

Jun 22 21:35:06 Serverhostname pure-ftpd: (?@clienthostname) [INFO] New connection from clienthostname
Jun 22 21:35:06 Serverhostname pure-ftpd: (?@clienthostname) [INFO] PAM_RHOST enabled. Getting the peer address
Jun 22 21:35:08 Serverhostname pure-ftpd: (?@clienthostname) [WARNING] Authentication failed for user [joe]
Jun 22 21:35:11 Serverhostname pure-ftpd: (?@clienthostname) [INFO] Logout.
```

---

### Post by Endolith on 2008-06-22
Adding this link allowed the user to log in!

```
 sudo ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/45puredb
```

I have no idea what "45puredb" is for, but it was recommended in this French thread:

[http://forum.ubuntu-fr.org/viewtopic.php?id=45764#p352234](http://forum.ubuntu-fr.org/viewtopic.php?id=45764#p352234)

Thanks, Google Translate!  

Then file transfers wouldn't work until I changed the owner of the default directory it created:

```
sudo chown ftpuser: /home/ftp/

```

But now I can transfer files from my other computer!  Now to see if I can forward ports and my friend can actually log in.

---

### Post by Endolith on 2008-06-22
It works.  Is there any harm in adding myself to the ftpgroup?

---

### Post by Endolith on 2008-07-07
I got PureFTPd running, using PureAdmin, and I can share files by putting them in /home/ftp and then using chown to change them to user ftpuser and ftpgroup (then virtual users in the FTP setup are controlling this system user, if I understand correctly).

I would like it better if I could create links in /home/ftp that point to other places on my hard drive, some of which are read-only for the ftpuser and some of which are read/write. Is there a way to do this with symlinks? When I change the owner of the link, it doesn't give any error, but the owner hasn't changed when I use ls.

---

