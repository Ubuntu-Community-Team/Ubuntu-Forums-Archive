---
title: "WiFi Installation"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by Vehendi on 2006-09-05
Hi,

I set up Ubuntu but now I'd like to connect to the internet. I have a Hercules Wireless G USB modem (HWGUSB2-54) and Ubuntu doesn't seem to autodetect it. What is the most easy way to install it?

---

### Post by NetworkGuy on 2006-09-05
Hi Vehendi,

I've checked the Wiki and came up with two different solutions for your cards chipset.  According to the Web, you are using a RT2500 chipset.  One Wiki entry reports problems and the second reports it works out of the box.

Please reply in this thread with the results of the following commands:  (These commands are issued from within the terminal.  Accessories --> Terminal I think. I don't have my box up and running right now to check)

```
lsusb
```
```
iwconfig
```
```
ifconfig
```

This will tell us if the card is seen, working, and configured correctly.  

And welcome to the community :)

---

### Post by lupine_nickt on 2006-09-05
RT2500 drivers are included - but out of date - in Ubuntu. The included GUI configuration tools don't work very well, either.

Solution [here](http://www.ubuntuforums.org/showthread.php?t=240669) (plug plug ;) )

---

### Post by Vehendi on 2006-09-05
> vehendi@vehendi:~$ lsusb
Bus 005 Device 002: ID 06f8:e000 Guillemot Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 041e:3100 Creative Technology, Ltd
Bus 004 Device 002: ID 054c:0155 Sony Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 06a3:0422 Saitek PLC ST90 Joystick
Bus 003 Device 003: ID 03f0:3104 Hewlett-Packard DeskJet 960c
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0419:0600 Samsung Info. Systems America, Inc.
Bus 002 Device 001: ID 0000:0000
vehendi@vehendi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vehendi@vehendi:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:2C:67:5D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29756 (29.0 KiB)  TX bytes:29756 (29.0 KiB)

vehendi@vehendi:~$

That's what I get.

I also heard of something called ndiswrapper.

@lupine: Which file do I download from your site and how do I install it?

---

### Post by Vehendi on 2006-09-07
bump

---

### Post by MenestrelX on 2007-05-30
I've been having the same trouble as you in using this USB wifi card on Feysty. Vehendi, have you found the solution to make it work ?

---

