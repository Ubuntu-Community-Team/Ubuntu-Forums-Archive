---
title: "Huawai E169G setup"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by dmh650 on 2008-04-19
Hey peoples, I have just got my hands on a Huawei E169G from Three UK.

Excellent device and works wonderfully on WIndows and Mac OS X but I have had some troubles getting it to work on Gutsy.

I have followed the instructions for the E220 on the page below (and a few others).

[http://ubuntuforums.org/showthread.php?p=1774427](http://ubuntuforums.org/showthread.php?p=1774427)

I have managed to get the device to appear in wvdial, dial and get an IP address. The program just stays there until I hit ctrl+c.

While it claims it is connected I still cannot surf the internet even though it shows up in ifconfig with the ip address.

Does anybody have any bright ideas?

---

### Post by dmh650 on 2008-04-20
Well I managed to get it to work in the end.

Thought I would post a follow up with a mini guide.

Here are the steps that I take to get it working.

For the first time you need to edit /etc/wvdial.conf file looks like this
```
# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
```

Once that is done you only need to follow these to get it to work each time

1. Plug the stick in.
2. Eject the virtual cd-rom drive under Places > System
3. Execute these commands

```
sudo rmmod usb-storage
modprobe usbserial vendor=0x12d1 product=0x1001

```

4. Reboot
5. Execute
```
wvdial hsdpa
```

If you see an IP adress you are connected.
If you still have problems accessign web pages make sure your wireless card is switched off.

Hope this helps anybody.

P.S. I am posting this from it while listening to Groove Salad, it's awesome.

---

