---
title: "HELP - denied permission to save changes to a system file"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by paul86uk on 2008-10-26
hello,
basically im setting up a network boot server ive found documentation on how to do this, but when i try to edit the dhcpd.conf to setup the dhcp server and its link to the tftp when i click save it comes up with an error sayying i do not have permision to edit this file.

im using (i think) ubuntu 8.04 gutsy heron, simply because im new to linux and having a gui makes things alot easier than diving in to a command line OS with no experience of one.

i had to install dhcp3d server which i got from launchpad.net and installed fine using the package manager, im thinking that because of that it has installed with some kind of root only permisions that my account doesnt have even though ive been into the users and groups manager and added my account to every relevant group (ie. dhcp root ltsadmin etc) and still im being denied permision..

can someone please provide me with a command line based method of installing the package under my own username(if possible) instead of 'root'.  or alternatively a way to fix this...

---

### Post by Sub101 on 2008-10-26
to edit the file do:

```
sudo gedit "....filename...."
```

---

### Post by Iowan on 2008-10-26
You can use "sudo nano filename" or "gksudo gedit filename".

---

