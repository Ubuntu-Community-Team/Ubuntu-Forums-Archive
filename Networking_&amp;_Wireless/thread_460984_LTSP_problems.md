---
title: "LTSP problems"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by Diego Antony on 2007-06-01
Hi, i have a similar problem. I tried all of Ram1 posted ([http://ubuntuforums.org/showthread.php?t=76889](http://ubuntuforums.org/showthread.php?t=76889)) but it still don´t work to me. I have ubuntu 6.06 with ltsp 4.2.

I had downloaded sis190 driver from sis website, i´ve unpacked file at /root/sis190_20041220, created the makefile on this folder:

(root@gandhi:~/sis190_20041220# ls -la
total 88
drwxr-xr-x 2 root root 4096 2007-05-31 09:43 .
drwxr-xr-x 26 root root 4096 2007-05-31 09:39 ..
-rwxrwxrwx 1 root root 150 2007-05-31 09:27 Makefile
-rw-r--r-- 1 root root 1902 2004-12-20 01:32 readme.txt
-rw-r--r-- 1 root root 254 2004-12-20 01:42 relnote.txt
-rwxr-xr-x 1 root root 62989 2004-12-20 03:12 sis190.c
root@gandhi:~/sis190_20041220# )

with the exactly same content posted here, and when i type make it show me whats above:

root@gandhi:~/sis190_20041220# make
make: Nada a ser feito para `default'.
root@gandhi:~/sis190_20041220#


Does any one can help me?

PS.: i had to install make, linux headers and gcc 3.4, but nothing happened

---

### Post by Diego Antony on 2007-06-01
Hey Guys, i typed #modeprobe sis190 and its gets no error message, but at my diskless client, linux try to install 3com 3c59x always, even with just my sis190 network enabled and plugued.

That make me think that i have to modify a configuration file, i tryed to modify /etc/dhcp3/dhcpd.conf like this

# Add these two lines to the host entry that needs kernel parameters

option option-128 e4:45:74:68:00:00; # NOT a mac address
option option-129 "NIC=sis190 IO=0x300";


but i don´t know if it is correct...

my kernel is

root@gandhi:~# uname -r
2.6.15-26-386

any idea????
_______________

---

### Post by chili555 on 2007-06-01
I have no idea if modifying dhcpd.conf is the correct way; the best way to find out is try it! My suggestion is two-fold. First, amend */etc/modprobe.d/blacklist* to add a new line:```
blacklist  3c59x
```Then I suggest amending */etc/modules* to add a new line:```
alias eth0 sis190
```This assumes your ethernet interface is eth0, substitute the correct interface if it's not.

Post back and let the other sis190 people know how it works.

---

### Post by Diego Antony on 2007-06-01
thank you for your reply Chili555, but i have both nics on my enviroment. doing this my clients with 3com will still working?

i have 10 clients with sis190 and 8 with 3com.

---

### Post by Diego Antony on 2007-06-01
And doing this my local network sill still working? this is apply just for ltsp clients?

---

### Post by chili555 on 2007-06-01
Are you saying the LTSP *clients* try to load 3c59x when their NIC card is sis190? Or are you having this issue with the *server?*

---

### Post by Diego Antony on 2007-06-01
is exactly what i am saying " LTSP clients try to load 3c59x when their NIC card is sis190". 

u have an idea about it?
 :) tks

---

### Post by Diego Antony on 2007-06-04
Anyone???? :/

---

