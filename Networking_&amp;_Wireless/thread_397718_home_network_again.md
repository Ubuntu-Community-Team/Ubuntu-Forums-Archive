---
title: "home network again"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by jerf on 2007-03-31
hi all, 
new to the forum.

ok so i have a laptop that runs xphome while my main box runs dapper 6.06.  I  also have a tower that runs fedora6 and xp pro.  ive installed samba on the main box and would like to set up file share between the three but im stuck.  when i attempt to use gedit on samba files i get display errors and something about (null)

vi is a whole other monster that im not even ready to take on.

i should mention that, despite my ineptitude im partial to the terminal and want to avoid the crutch of gui's as much as possible, for my own amusement if nothing else.

currently im at the point where im supposed to set up a password and username for file sharing and thats where im stuck.  Any help is appreciated ofcourse.

---

### Post by spd106 on 2007-03-31
First you need to add a samba user so that you can connect to samba shares. Then you need to edit the smb.conf as root (sudo, or gksudo with gedit). You don't need to dive straight into vi/emacs, just use nano.

Have you read this wiki page [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)?

---

### Post by jerf on 2007-04-01
hi there 

cant really make sense of this how to..
where it tells us that we need to change things in the general tab for our network settings, i dont have the option of 'Windows Networking" 

im also unsure as to what my Domain is and how i find out..i figure the ip my router gives me is it but im not sure

still confused and would like to set up a network with my laptop running xp

---

