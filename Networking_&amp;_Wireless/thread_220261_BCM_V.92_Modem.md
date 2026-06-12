---
title: "BCM V.92 Modem"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Slingshot on 2006-07-21
Hi all,

       I have a Dell Inspiron 8600 with a BCM94212 V.92 56K daughter board. I have installed the sl-modem drivers and can connect to my isp only via a strange method.

In order to get wvdial to get a dialtone, I have to open the gnome sound mixer, select the modem and disable the offhook switch, then enable it again. I have to do this each time I connect.

I have downloaded the command set for the modem for dell support and modified the init string without success. 

My wvdial.conf
```
Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 M1 L1 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Check Default Route = true
Idle Seconds = 0
Modem Type = Analog Modem
Stupid Mode = 0
Baud = 460800
New PPPD = yes
Modem = /dev/modem
ISDN = 0
Carrier Check = no
Stupid Mode = 1
```

Before trying Ubuntu I was using Gentoo and using kppp without problems, so im not sure if I configured wvdial correctly. I also have tried gnome-ppp, but it looks like its a gui for wvdial, so I had no success with it.

Thanks.

---

