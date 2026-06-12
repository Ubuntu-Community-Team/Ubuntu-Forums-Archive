---
title: "Bluetooth NOT Working"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by kiran1247 on 2014-05-19
Hi,

Can someone please help me in resolving "bluetooth" issue ?

I'm using UBuntu 12.04.2 LTS

Bluetooth path : /etc/bluetooth

root@kiran:/etc/bluetooth# ls -lthr
total 28K
-rw-r--r-- 1 root root  262 Aug  6  2008 input.conf
-rw-r--r-- 1 root root  248 Aug  2  2009 serial.conf
-rw-r--r-- 1 root root  120 Jul 13  2010 network.conf
-rw-r--r-- 1 root root 1.5K Aug 25  2010 audio.conf
-rw-r--r-- 1 root root  258 Dec 22  2011 proximity.conf
-rw-r--r-- 1 root root  297 Mar 22  2012 rfcomm.conf
-rw-r--r-- 1 root root 2.5K Mar 22  2012 main.conf

root@kiran:/etc/bluetooth# lsmod | grep blue
bluetooth             211812  10 rfcomm,bnep


root@kiran:/etc/bluetooth# rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@kiran:/etc/bluetooth# 


When I open preferences >> Bluetooth --> I can see everything disbaled.

It says " No Bluetooth Adapaters found". Why ?

But I have bluetooth installed on my machine. And I'm unable to enable bluetooth , why? Any reason ?

Please do help me in fixing this issue.
And let me know if you need any additional information on this.

Thanks
Kiran

---

