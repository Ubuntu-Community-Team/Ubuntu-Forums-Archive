---
title: "How Easy is Ubuntu to Network"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by blfer on 2005-09-26
I am new to Ubuntu. How easy is Ubuntu to netowrk with existing Windows and other Linux boxes? Please remember that I am a complete novice at this. Thanks in advance.
blfer :???:

---

### Post by Zelut on 2005-09-26
It should be simple to network.  I had 3 Ubuntu machines on my network and one windows machine and we could see each other just fine.  The more complicated you get the more you might have to adjust, but simple networking shouldn't be a problem at all.

---

### Post by blfer on 2005-09-26
O.K. Let me ask a really stupid question then: How easy is easy? Do I have to know "ANY" programing or have any programing skills, or is it as simple as naming the networks the same on all of the boxes? Thanks in advance.

---

### Post by blfer on 2005-09-26
Sorry, forgot to ask this earlier. Are there ant "How to---s" to network computers together? Thanks.

---

### Post by blfer on 2005-09-27
Well, anyone? Please?

---

### Post by davidknibb on 2005-09-29
Well - it's fairly straightforward - no need to program but you will need to install some specific software.
I'll tell you how I did it on my system.

Firstly, two Win XP deskops networked using a Netgear router on Broadband.  This was set up and working.

Next. connect your Ubuntu m/c to the router using the appropriate cable.
You have to make sure that eth0 is configured/activated by going to Sytem->Administration->Networking (in Breezy - the menus are a bit different in Hoary)
and clicking the right boxes.

At this stage you can connect to the internet using whatever browser etc.

But you cannot yet see the Windows machines and they cannot see Ubuntu machine.


What follows is a brief description - but make sure that you read it in detail in an appropriae book/guide on Debian.
You have to makr sure that samba and samba-client are installed on the Ubuntu machine 
Then configure them with the command
dpkg-reconfigure -plow samba samba-common 
(as root) and answer the questions.  you need to know your network name.
Go to the Networking tab again as above and tick 'enable windows networking'

Add your self on the Ubuntu maching as a user

smbclient-a <your user name>

you will be asked for a passwd.

On the Ubuntu machine testto see if the server is avaiable

smbclient -L <server-name>   (your machine's name)

If it connects you'll see some info.

You are then all set up to go.

David

---

### Post by manicka on 2005-09-29
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto)

---

