---
title: "HOW TO: Install AirCrack-ng on Ubuntu 9.04 (Jaunty Jackalope)"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by ramoj02 on 2009-06-20
Before you install AirCrack-ng you need to make sure that your Wifi card is compatible with AirCrack-ng. Click [here]("http://www.aircrack-ng.org/doku.php?id=compatible_cards") for more information about compatible WiFi cards.

To install AirCrack-ng on Ubuntu 9.04 (Jaunty Jackalope):

1. Open terminal and type:

sudo apt-get install aircrack-ng

2. After installing it, type:

sudo apt-get install macchanger

3. After installing it, type:

sudo aptitude update

4. You're done!

---

### Post by taavikko on 2009-06-21
This hardly is a subject to be discussed in this forum?

Installation is easy, but what after that?

---

### Post by Linux_nss on 2010-04-06
Hi ,,I use ubuntu 9.10
when I execute 
yaseribrahim@yaseribrahim:~$ sudo apt-get install aircrack-ng
[sudo] password for yaseribrahim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack-ng
yaseribrahim@yaseribrahim:~$ 


and I crack the WEP key by BT4 ,but I want to do that again by ubuntu 9.10 
my driver : 
yaseribrahim@yaseribrahim:~$ sudo su
[sudo] password for yaseribrahim: 
root@yaseribrahim:/home/yaseribrahim# airmon-ng


Interface    Chipset        Driver

wlan0        Realtek 8187L    rtl8187 - [phy0]

root@yaseribrahim:/home/yaseribrahim# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:" "  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:6F:4A:9E:33   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@yaseribrahim:/home/yaseribrahim# airmon-ng stop wlan0


Interface    Chipset        Driver

wlan0        Realtek 8187L    rtl8187 - [phy0]
                (monitor mode disabled)

root@yaseribrahim:/home/yaseribrahim# 


I can't ...


Thanks

---

