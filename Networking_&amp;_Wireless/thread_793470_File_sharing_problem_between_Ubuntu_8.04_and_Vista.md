---
title: "File sharing problem between Ubuntu 8.04 and Vista computers"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by chooch on 2008-05-13
Hi guys,
After hours of trying to work out this problem, this is what happens now:
My Ubuntu machine display my 2 Vista computers, but when I click on them, I don't see any shared folders.
Needles to say that everything worked before I installed Ubuntu.
On the other side, I fixed the problem I had; The Vista computers now have full access to the shared folders on my Ubuntu computer. 
I'm trying to fix this problem for HOURS, so please help [-o<

---

### Post by superprash2003 on 2008-05-13
have you tried typing smb://(ip address of vista) under location in places->computer

---

### Post by chooch on 2008-05-14
yes, didn't work

---

### Post by Iowan on 2008-05-14
I just discovered [this]("http://ubuntuforums.org/showthread.php?t=780274") post... so now I think it's the cure for all Hardy Samba problems.  It would possibly help if you could have accessed the machine by IP address... try it anyway.

---

### Post by chooch on 2008-05-14
it doesn't work. what else should I do?

---

### Post by chooch on 2008-05-20
?

---

### Post by Iowan on 2008-05-20
Windows boxes have firewalls either turned off, or set to allow filesharing? I don't have either Vista OR Hardy, so please excuse a dumb comment... I have better luck connection via Places>"Connect to Server" - dunno if that option is still in Hardy, apparently sharing options have changed.

---

### Post by chooch on 2008-05-21
firewalls off,windows computers have no problem between itself. connect to server doesn't work either.

---

### Post by sinofemp on 2008-11-24
same problem here....
somebody please help......:confused:

---

### Post by TutonicMonkey on 2008-11-24
I can confirm this issue too. Here is my post on the topic and what I have attempted. 

[http://ubuntuforums.org/showthread.php?t=986574](http://ubuntuforums.org/showthread.php?t=986574)

Still no luck :confused:

---

### Post by gabriel2007 on 2008-12-25
I have the same problem,

it's a bug

of Samba with Gnome as with KDE based distros work perfectly, it's not ubuntu 8.xx, it's all the linux distros.

you can browse all the computers in the network but you don't see any shared folder on vista or server 2008 computers, on windows xp computers or 2003 server you can see all with Gnome.

if you type smb://vista_computer/the_shared_folder 

you will see all the files within it, it's a hassle though


greetings

---

