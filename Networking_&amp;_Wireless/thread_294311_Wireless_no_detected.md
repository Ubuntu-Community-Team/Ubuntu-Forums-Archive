---
title: "Wireless no detected"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-11-06
I just got a new laptop (Acer Aspire 5050) From compusa, and after research that SHOULD mean I have a  atheros wireless card....but after installing edgy no wireless cards are detected....

jduvall@acer-5050:~$  sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

jduvall@acer-5050:~$  sudo ifup eth0
ifup: interface eth0 already configured

---

### Post by .t. on 2006-11-06
I don't have an atheros card, but the information from the following commands will be of help:

dmesg | grep -i ath
iwconfig

---

### Post by Elvish Legion on 2006-11-06
jduvall@acer-5050:~$ 
jduvall@acer-5050:~$ dmesg | grep -i ath
[17179599.256000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
jduvall@acer-5050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jduvall@acer-5050:~$ 



Sounds like my wireless card isn't being detected

---

### Post by elektronaut on 2006-11-09
Just a guess, as I'm also having [a strange problem with my wireless card]("http://ubuntuforums.org/showthread.php?t=295113"): Maybe it's a hardware issue and the card has to be activated by some switch or in the BIOS?

---

### Post by FrodoB on 2006-11-09
Could you please explain the situation more clearly?

What type of Atheros card is it? (USB< PC CARD, Mini-PCI, etc.)

---

### Post by Elvish Legion on 2006-11-09
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:~$ dmesg | grep -i ath
[17179678.220000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179679.340000] ath0: no IPv6 routers present
ubuntu@ubuntu:~$

---

### Post by FrodoB on 2006-11-09
So it looks like ath0 is up, but it is not getting any usable signal. Is there a know good access point nearby?

---

### Post by Elvish Legion on 2006-11-10
When I reboot my computer ath0 was gone....

And yes the network is useable.

---

