---
title: "Verizon wireless disconnect problem?"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by pv101 on 2008-01-10
I've been searching the forums on this topic and found a lot of help. I have a script which shuts down my eth0, eth1 interface, and then runs wvdial to launch the ppp0 connection.
I've been able to get the ppp0 link up and working, and I can get to the internet just fine, but it only works for a few minutes and then seems to disconnect. 


Not sure if anyone has been able to get a fix for this or not, but here are my scripts:

#!/bin/sh
modprobe usbserial vendor=0xc88 product=0x17da
ifconfig eth1 down
ifconfig eth0 down
wvdial

This launches my Verizon link up, and I get an address. This is my wvdial.conf config:

[Dialer Defaults]
Stupid Mode = on
Modem = /dev/ttyUSB0
Baud = 921600
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = #########@vzw3g.com
Password = vzw
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Auto Reconnect = on
Carrier Check = no
Idle Seconds = 0
[Dialer shh]
Init3 = ATM0
Check Def Route = on
[Dialer pulse]

---

### Post by dark_harmonics on 2008-03-07
I have this exact same problem. It almost seems like wvdial gives up and disconnects. I wish there was a way to tell it to stop doing that. It gets all the ip information and then 5 minutes later crashes. I have been just restarting it every time so that i can do schoolwork on the way home from work.

---

