---
title: "[SOLVED] Logon to Windows Network"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-10-21
I followed the directions for Broadcom card. I finally showed 5 bars in the wireless icon.
Then I could see the laptop which has windows 2000 with a shared folder.

I tried to logon using the usual windows name and password and was unsuccessful.

Before I put Ubuntu on the laptop I'd like to confirm that the network is actually working,

I need to use the network to share an internet connection between the desktop with a 
modem and the laptop.

Another issue is that it takes 3 or 4 clicks on the network manager to actually connect.
Is that normal?

---

### Post by jludeman on 2007-10-22
Some confusion as to how to log on.

Resolved this way:

went to the menu places connect to server

service type - windows share

typed in box server the address - in my case 192.168.11.3

nothing seemed to happen but look on my desktop is 192.168.11.3

double click opens a file window showing my windows directories

 double click on shared folder asks me for authentication required

no idea what to enter - bad dialog design

username same as windows

domain whatever linux thinks it is

password same as windows 

aha! viola I'm into windows shared folder bwa hah a never mind!

---

### Post by jludeman on 2007-12-01
Fixed my intermittent broadcom problem by following this excellent how-to.
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

