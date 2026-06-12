---
title: "Can't Enable wireless"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by abasel on 2015-05-02
I am currently trying Elementary OS but have tried a number of other distro too.

> sysadmin@L-HS-01:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


> sysadmin@L-HS-01:~$ sudo ip link set wlan0 up
[sudo] password for sysadmin: 
RTNETLINK answers: Operation not possible due to RF-kill
sysadmin@L-HS-01:~$ 


> sysadmin@L-HS-01:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


There is a switch on the Compaq nw8440 laptop but its one of those soft-type switches and it won't switch on under linux.

> sysadmin@L-HS-01:~$ lspci -v | grep Wireless
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Any ideas;  I have read a number of postings but none have helped.

---

### Post by jeremy31 on 2015-05-03
Have you tried resetting the BIOS?

---

### Post by abasel on 2015-05-03
Hi, had checked the BIOS and it all looked fine but did the reset and yes that seemed to fix it. Thanks a ton! :guitar:

---

