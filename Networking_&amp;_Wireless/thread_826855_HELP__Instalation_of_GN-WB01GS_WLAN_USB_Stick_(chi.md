---
title: "HELP : Instalation of GN-WB01GS WLAN USB Stick (chip RT2571)"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by xx6xx on 2008-06-12
Hi, 
I'm ubuntu nooob, and need Your help.
I have to install usb wlan stick GN-WB01GS WLAN (on chip RT2571) on my notebook and have no bloody idea how can I do that ...
I've tried some HOW-TOs already, but non of them worked ...
I'm using Ubuntu 8.04 at the moment. In gusty this usb wlan stick worked without any problem, was installed automatically... HELP!



The usb wlan is seen by my OS as : "Bus 005 Device 006: ID 1044:8008 Chu Yuen Enterprise Co., Ltd" ...
HELP!

---

### Post by xx6xx on 2008-06-14
Any ideas ?

---

### Post by kortez on 2008-10-27
Somebody please help, I have the same problem.
The farthest I have gotten is with these links:
[http://linux-wless.passys.nl/query_part.php?brandname=Gigabyte+Tech](http://linux-wless.passys.nl/query_part.php?brandname=Gigabyte+Tech)

[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)
[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)
[http://linuxette.suinot.org/index.php/Ovislink](http://linuxette.suinot.org/index.php/Ovislink)

---

### Post by kortez on 2008-10-29
I have everything working now with the same usb stick, except my chipset is rt73. I used ndiswrapper and followed this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The only thing that might not be working properly is the speed; it says its the same speed at [http://www.speedtest.net/](http://www.speedtest.net/) (around 280 kbps down) as any other method of connecting to my router, but in the connection information it says the speed is 1 Mb/s.

---

### Post by xx6xx on 2008-11-02
thx, helped me as well, I'm greatful.

---

### Post by kortez on 2009-04-23
This wireless USB stick works flawlessly with 8.10 without any need to modify anything. I am going to test it soon with 9.04 although I cannot see why it would not work.

---

### Post by kortez on 2009-05-21
It works flawlessly in 9.04 too.

---

