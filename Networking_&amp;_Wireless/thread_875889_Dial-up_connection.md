---
title: "Dial-up connection"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by adudutz on 2008-07-31
How to connect to the net using a usb modem? my modem is already detected, but how to connect?????? :confused:

---

### Post by wheezy-weasel on 2008-07-31
Hi,

I have ended up using wvdial to connect to vodafone with a huawei e172.

Advice on how to was provided in my thread [here]("http://ubuntuforums.org/showthread.php?t=873021").

---

### Post by adudutz on 2008-07-31
correction: I think my modem is detected as /dev/modem/. So, what does it mean and how to connect from it????

---

### Post by adewale on 2008-07-31
okay i use dialup also. What i basically do is first detect my modem
sudo wvdialconf
Then edit wvdial.conf
sudo gedit /etc/wvdial.conf
Which returns

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = wap
Username = wap

My modem is detected as /dev/ttyACM0
Then i save it 

Then i open a terminal and connect by typing 
sudo wvdial

---

### Post by adudutz on 2008-08-03
Well, I've used gnome-ppp to configure my modem connection, while I also have installed the driver. It can connect, but the speed is horrible. I think this is because the 'brake' Linuxant implemented on the driver (I'm using USB HSF Conexant modem).

Any way to solve this rather than paying??

PS: I'm using the latest ubuntu (8.04)

---

### Post by s_dub757 on 2008-08-09
i am having problems with my USB Modem also.
Sierra wireless Aircard 595U USB Modem.
I Need Help Configuring it.

---

