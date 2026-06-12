---
title: "3G and ONLY 3G is wanted"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by stardustdk on 2007-10-26
Hey all.

I figured how to configure my Huawei E220 USB modem to work with "3" in Denmark, BUT..... :confused:

I want to make sure that my wvdial.conf is configured, so i ONLY connect to 3, that mean no 2G network - meaning no roaming -  to me, please . 

I am running Ubuntu Gutsy.

My wvdial.conf is configured like this:

[Dialer 3]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
Phone = *99#
username=any
password=any
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","bredband.tre.dk"
Dial Attempts = 3

Best regards

Stardustdk

---

### Post by stardustdk on 2007-10-26
More info:

I have goggled that its is a AT+COPS that is needed, haven't found a successfully way to make it work with Google :(.

If you have a way to configure wvdial.conf  to make my wish working, please show me ;).

I do also use Gnome-PPP, is there a way to make my wish working with that, or is that configured via wvdial?

 
Best regards

Stardustdk

---

