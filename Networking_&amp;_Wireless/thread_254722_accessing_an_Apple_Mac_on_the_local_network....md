---
title: "accessing an Apple Mac on the local network..."
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by mmcmonster on 2006-09-10
Hi.
  I have an apple mac on the same local network as my PC which dual boots Windows XP and Ubuntu 6.06.

In Windows XP, the computer can "see" the mac.  When I double click on the mac, it asks me for a user name and password, after which I can access that user's information on the apple Mac over the LAN.

In Ubuntu, I can't seem to find the computer in Network Servers.

---

### Post by mmcmonster on 2006-09-10
As an added peace of information, under WindowsXP, the iMac shows up as:

My Network Places -> Microsoft Windows Network -> Workgroup -> *ComputerName*.

---

### Post by tbonius on 2006-09-11
I assume you are trying to access the MAC with the SMB browser.  In Ubuntu you would choose the connect to server option.. and type smb://ipaddress-of-mac-computer

If you want to enable the generic SMB network browser.. double check that you have SAMBA installed.. and edit your smb.conf to make it part of the workgroup name called "WORKGROUP" where the MAC computer exists.

T

---

### Post by mmcmonster on 2006-09-12
Does capitalization count in the workgroup name?  I'll let you know how this works out in a couple days. (When I'm in front of the system with the problem.)

I am sure samba is installed.  It's installed by default in 6.06, right?
I do think it stinks that Ubuntu can't do this "out of the box".

---

### Post by tbonius on 2006-09-12
The libsambaclient is installed by default.. and it can do SMB connections right out of the box.  The point of setting up the whole Samba package is to make sure your SMB service is functioning within the parameters of your network.

---

