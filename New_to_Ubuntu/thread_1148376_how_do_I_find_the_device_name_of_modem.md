---
title: "how do I find the device name of modem"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by gandaran on 2009-05-04
how do I find the device serial name of a hsf conexant pci modem? it's supposed to be something like tty*
I installed the conexant driver from  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php) but cont get it to work with efax-gtk

---

### Post by jerrrys on 2009-05-04
i do not run a pci modem so dont know if any of these commands will give you the desired information, but passing it on anyway...open terminal and...

lspci   or   dmesg   or   lsdev   or   lshal

---

### Post by lkraemer on 2009-05-04
Probably the easiest way is to use wvdial to find it.
Assuming that you have the proper drivers loaded for your
winmodem you can at least try this:

Open a Terminal Window and DO:
```

sudo wvdialconf /etc/wvdial.conf

```

Then if you want to dial out you can use:
```

sudo gedit wvdial.conf

```
to add your phone number, password, etc. to finish up.
Add Stupid Mode and New PPPD.......

SAMPLE wvdial.conf file
[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 1234321
Password = yourpassword
Username = [email]yourlogin@ISP.net[/email]

wvdial will test all serial, and usb ports looking for the modem.
It will tell you it found the device on /dev/ttyUSB0 etc.

Once you have wvdial working just use Synaptic and install Gnome-PPP and configure it.
You will like the way it works.

lkraemer

---

