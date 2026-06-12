---
title: "dial up issues in ubuntu 7.10"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by gauthamsrinivas10 on 2009-10-24
i am using live CD of ubuntu 7.10 
i dont find System => Administration => Networking in the live CD 
and  I dont find GNOME too
while i tried to establish dial up connection for BSNL WLL LG LSB 260 B modem...i hv installed the driver of the modem which is an exe file by using wine software ...
and i hv given all those commands given in the forums ,
the modem is recognized but the internet connection is not established
When I use wvdial it states that 

Waiting for Carrier

No Carrier Found

What to do now?

I am able to connect to the internet in windows. But I am not able to connect using wvdial in ubuntu. Can anybody help me? 

I put an extra initialization string while connecting in windows. modem >> advanced.

I don't know where to add this in wvdial. your help would be very useful. pls somebody who uses wvdial please respond.

---

### Post by overdrank on 2009-10-24
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by lkraemer on 2009-10-25
First, you need to configure wvdial.  Open a Terminal Window and do:
```

sudo wvdialconf /etc/wvdial.conf

```

Then, after wvdial finds your modem, it will add information to
the wvdial.conf file.  Something similar to:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
;These next few lines will be different on your system 
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 1234432
Password = yourpasswordhere
Username = yourloginhere@ISP.net

```

If this doesn't help you need to start here:

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Post #4 - Starting at "These work wonderful with wvdial, etc."

lk

---

### Post by lovinglinux on 2009-10-25
Is there a special reason to use Ubuntu 7.10? This version already reached end of life, so is no longer supported. In less then a week there will be a new Ubuntu release, Karmic Koala 9.10, but you can also install other supported versions. See the available versions and end of life dates at [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by halitech on 2009-10-25
typically using wine to try and install hardware drivers doesn't work very well as it doesn't allow interaction with the hardware. Maybe if you tell us the make and model of the modem we can help you get things going natively.

```
lspci
```will give us the info we need

---

### Post by samh785 on 2009-10-25
sudo apt-get install gnome-ppp

that worked for me in 7.04

---

