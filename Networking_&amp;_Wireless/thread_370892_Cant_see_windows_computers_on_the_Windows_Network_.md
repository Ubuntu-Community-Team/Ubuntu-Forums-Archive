---
title: "Cant see windows computers on the Windows Network in Ubuntu"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by steve101101 on 2007-02-26
Hey. I am trying to connect to my windows computers that are on the same network as my ubuntu computer. I have set up samba, however, i cannot see the computer when i search for it. It is like it nolonger exists on the network. My windows XP computer can see my ubuntu computer's shared folder though. 

Please help.

---

### Post by steve101101 on 2007-03-01
In order to fix this for me you have to do the following...

All you have to do is:

edit /etc/nsswitch.conf

code: 

#sudo gedit /etc/nsswitch.conf

change the line that says...

hosts: files dns to 

to this:

hosts: files dns wins

Then Install winbind

Code:

sudo apt-get install winbind


Thanks to javiwwweb.

The original is posted here ----> [http://ubuntuforums.org/showthread.php?t=88206]("http://ubuntuforums.org/showthread.php?t=88206")

Hopefully this works for all of you. also this will allow you to use the computer names (netbios names) instead of ip to mount folders, ect.

---

### Post by steve101101 on 2007-03-01
The only negative to this solution is that finding the network and changing folders through nautalis    can take a little more time than usual since it increases the amount of possibilities that the computer searches for. BUT seeing all the windows computers all the time is invaluable.

---

