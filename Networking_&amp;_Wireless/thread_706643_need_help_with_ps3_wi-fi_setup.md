---
title: "need help with ps3 wi-fi setup"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by babyblow10 on 2008-02-24
ok i installed xubuntu 7.1 yesterday and im trying to get my internet set up via wireless router....i go to network connections but their is only wired and modem settings i dont see nothing for wireless can someone help me

---

### Post by babyblow10 on 2008-02-24
i typed in iwconfig and no wireless extensions for lo and eth0 so im guessing it doesnt recognize the ps3 wireless

---

### Post by lumberjack on 2008-03-30
Since you have a brand new install of 7.1, I'd say you don't have an updated kernel that addresses the wireless driver.  There is a good tutorial on how to install kernel 2.6.24 on psubuntu.com forums, and can be found at 

[http://psubuntu.com/forum/viewtopic.php?t=2349](http://psubuntu.com/forum/viewtopic.php?t=2349)

I spent today updating the kernel and now the wireless network card is recognized.  now i'm trying to figure out how to connect to my encrypted wireless router.  good luck to you.

---

### Post by scher2jb on 2008-07-09
ok ive got game os v 2.41.... yes tonight they released it, and a fresh install of ubuntu 7.10 working well.... besides the wifi.  did everyone with ubuntu on the their ps3 die off, cause it seems the last post for all of the threads ended in june of this year...  i could use someones help.

j

---

### Post by manbish on 2008-07-11
I have ps3 2.36, xubuntu 7.10 and a belkin usb FD5 7050 with zd1211rw driver.  I followed the advice on the troubleshooting guide by setting the dhclient.conf and my router to opendns and runnning the commands in the terminal starting with

lshw -C network

to find the logical name of my device.

The guide is at

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28ipv6%29#ifconfig](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28ipv6%29#ifconfig)

I don't have security on my router, but I have the MAC address filtering switched on.

---

