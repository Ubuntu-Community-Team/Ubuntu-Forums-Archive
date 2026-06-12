---
title: "broadcom 1395 dell inspiron 1420 (not 1420n)"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by lankforddl on 2008-04-28
Hello,

I have a new:

Dell Inspiron 1420 (NOT 1420n)
Broadcom "1395" (NOT 1390)
Ubuntu 8.04 (Hardy)

I cannot get this darn internal broadcom 1395 to work. I have the driver bcmwl6.inf that came with the laptop. Does anyone have this broadcom 1395 working yet? 

I'm using USB network adapter for now and it works fine.

P.S. ndiswrapper, windows wireless drivers, ndisgtk, all installed properly, and functioning with the USB network adapter. 

Thanks to anyone with suggestions,
Danny

---

### Post by sam_delta on 2008-04-29
first goto
system>.administrator>hardware drivers drivers, and activate broadcom driver, if they are not listed, then try the following procedure


 procedure to reinstall b43 (drivers for broadcom) (just incase they where not listed under hardware drivers.

make sure you have network connection and do this

go to a terminal and type to remove

```
sudo aptitude purge b43-fwcutter
```

update your repos type
```
sudo aptitude update
```

to reinstall type

```
sudo aptitude install b43-fwcutter
```

itll ask you if you want to fetch some firmware, make sure you answer "Y" for yes

then restart pc, goto system>.administrator>hardware drivers drivers, and activate broadcom driver


tell us how it goes

sam

---

### Post by lankforddl on 2008-05-01
Hi Sam,

Thanks for the information and sorry for the slow response. I ran through the steps that you suggested nothing shows up in "hardware drivers."

Here's a cut of my iwconfig. 

danny@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

some more hardware info:
Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Broadcom Corporation BCM4310 USB Controller (rev 01)

Thanks again for the help,
Danny

---

### Post by lankforddl on 2008-05-01
This post here helped me fix the problem. It also worked with other model laptops using this same broadcom 1395 card. Ugh, finally! 

D


[http://ubuntuforums.org/showthread.php?p=4858467#post4858467](http://ubuntuforums.org/showthread.php?p=4858467#post4858467)

---

