---
title: "IPtables to open ports"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by tstephenson on 2007-08-20
I'm trying to get ports 25, 110 and 143 open for a general user so I can get the mail server working on Wine.  The program will run as root but when I login as a normal user the ports are blocked.  I need these ports open for all users.  I am familiar with mail systems but I'm a complete novice when it comes to administering Linux.

Thomas

---

### Post by CheShA on 2007-08-20
If you;re running a gui, install firestarter, it's a really easy gui frontend for IPTables

---

### Post by CheShA on 2007-08-20
..but why on earth are you trying to run a windows based mail server on Linux?????? *NIX is KING of the mail server!

---

### Post by ruibernardo on 2007-08-20
> **tstephenson said:**
> I'm trying to get ports 25, 110 and 143 open for a general user so I can get the mail server working on Wine.  The program will run as root but when I login as a normal user the ports are blocked.  I need these ports open for all users.  I am familiar with mail systems but I'm a complete novice when it comes to administering Linux.

Thomas

Hi,

you want to run a mail server with wine? What for? You have the best mail servers in native Linux. Why use a windowz mail server here? Run wine as root? :confused:  Please don't!!! At the most, run it as a normal user.

My best advice is for you to spend some time browsing "[Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")" and search some good tutorial about mails servers, just to see how to do it right and to have some basic idea of achieving your goal. 

You will see that's not that hard if you try, but don't try it the Windowz way... *please*!

---

### Post by tstephenson on 2007-08-22
> **CheShA said:**
> ..but why on earth are you trying to run a windows based mail server on Linux?????? *NIX is KING of the mail server!

Because in a single easy to use package I have a mail server that includes a mailing list server, IMAP4, daemons for bayesian filters, graywalling, and anti-virus using Clamd.  People have been asking how they can use Mercury/32 on Linux and I'm trying to figure out the best way to do this.

---

### Post by tstephenson on 2007-08-22
> **CheShA said:**
> If you;re running a gui, install firestarter, it's a really easy gui frontend for IPTables

Tried that, it opens ports for root but not for general users it appears.  Not only that it blocked access to the Netware and Windows hosts.  Probably my problem using the application but I could not get it to NOT block what was open before.

---

### Post by tstephenson on 2007-08-22
> **epimeteo said:**
> Hi,

you want to run a mail server with wine? What for? You have the best mail servers in native Linux. Why use a windowz mail server here? Run wine as root? :confused:  Please don't!!! At the most, run it as a normal user.

My best advice is for you to spend some time browsing "[Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100")" and search some good tutorial about mails servers, just to see how to do it right and to have some basic idea of achieving your goal. 

You will see that's not that hard if you try, but don't try it the Windowz way... *please*!

I know how to protect my systems from intruders, I certainly do not have to be told that opening ports 25, 110 and 143 is going to do any particular harm.  I do know that running a mail server as root is more dangerous that running as a user but so far it looks like a normal user is not allowed to use low ports.  

I'm trying to run a Windows app on Linux since there are all sorts people asking for the abllity to run Mercury/32 on Linux.  it works quite well, it would be better if it were not running as root.  

Please answer the questions asked and not get into discussion not really pertinent to the question at hand.

---

