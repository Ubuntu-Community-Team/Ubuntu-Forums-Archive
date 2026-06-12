---
title: "usb huawei e 180 problem"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by inter-m on 2009-10-05
i tried to install and connect to the internet using huawei E180... after puting it in the usb i was prompted by the wizard i did all steps then it connected to the internet... everything seemed fine but when i used firefox and other internet apps they didn't work cuz there was no actual internet connection... any help is appreciated...

---

### Post by fleamour on 2009-10-05
Does this help?

[http://chankle.org/blog/index.php?/archives/24-Using-Huawei-E180-modem-in-linux-RHEL5.html](http://chankle.org/blog/index.php?/archives/24-Using-Huawei-E180-modem-in-linux-RHEL5.html)

---

### Post by skclewis on 2009-10-19
I'm having a similar problem.  I followed the instructions fleamour provided in the link.  I'm still new to Ubuntu and not sure if I created the script file right.  Anyone give me some help on how to write the script?  The modeswitch and other files have been installed and seem to be working but the modem is not recognized and I don't have the ppp0 connection when I do the ifconfig.  Really would like to get it running.  Thanks.

---

### Post by mr_skater99 on 2009-11-15
my e180 worked perfectly on 9.04.

Fresh install of 9.10 and i have the same behaviour as above - however if i unplug the modem and plug it into a different usb port - it works fine.

But I have to do this each time the laptop starts.  Didn't have the issue with 9.04 - and yeah i've tried different usb port combos.

---

### Post by dependancyhell on 2009-11-15
The Huawei modem works out of the box.  I've got half a dozen of them, and they're all fine.

However, I can confirm this behaviour. 

It's a problem with network manager, which is pants.

As a previous poster stated, unplugging your modem and putting it in another USB port works.

More reliably, however, seems to be using wvdial to connect instead of networkmanger.

If you want to use wvdial:

```

sudo apt-get install wvdial

```

then, as root, open /etc/wvdial.conf and use something like:

```

[Dialer Defaults]
    Init1 = ATZ
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Stupid Mode = 1
    ISDN = 0
    Modem Type = Analog Modem
    Phone = *99#
    Modem = /dev/ttyUSB0
    Username = web
    Dial Command = ATDT
    Password = web
    Baud = 9600

    [Dialer tmobile]
    Init1 = ATZ
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Init3 = AT+CGDCONT=1,"IP" "T-Mobile"
    Stupid Mode = 1
    ISDN = 0
    Phone = *99#
    Modem = /dev/ttyUSB0
    Modem Type = Analog Modem
    Username = web
    Dial Command = ATDT
    Password = web
    Baud = 460800

```

Changing tmobile, and the username and password to match your ISP.

To connect, in a terminal type "sudo wvdial".

---

