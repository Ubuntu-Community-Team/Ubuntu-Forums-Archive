---
title: "ubuntu wifi help"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by TUNDRA35 on 2008-03-22
hey everyone i am very new to linux and am loving it. But no matter what i try i cnat get it to work. ive tried wifi radar and ndiswrapper.

i have a HP pavilion Zv6000 wth a Broadcom card.

ive someone could just walk me through(rememeber im a noob lol) i would rly luv it.

thanks you

oo and i ran iwconfig in the terminal and it knows my card is there. but i cant connect.

---

### Post by Eiríkr on 2008-03-22
It'd be very helpful for us on the boards to better understand your situation if you could post the results of each of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

And also let us know *exactly* what happens, and post what you see on screen in the terminal, when you restart your network like so:
```
sudo /etc/init.d/networking restart
```

Cheers,

Eiríkr

---

### Post by TUNDRA35 on 2008-03-22
> **Eiríkr said:**
> It'd be very helpful for us on the boards to better understand your situation if you could post the results of each of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

And also let us know *exactly* what happens, and post what you see on screen in the terminal, when you restart your network like so:
```
sudo /etc/init.d/networking restart
```

Cheers,

Eiríkr
 this is wat i got,


ifconfig,
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:BC:51:3A  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0. 0 b)  TX bytes:0 (0. 0 b)

          Interrupt:20 Base address:0x400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



iwconfig,
lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"

          Mode:Managed  Access Point: Invalid   

          RTS thr: off   Fragment thr: off

          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

sudo /etc/init.d/networking restart

Password:
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by kevdog on 2008-03-22
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Take a look at that wiki page -- its pretty thorough

---

### Post by TUNDRA35 on 2008-03-22
> **kevdog said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Take a look at that wiki page -- its pretty thorough

i know i tried this but i dont have internet access on ubuntu.

---

### Post by kevdog on 2008-03-22
Your going to need internet access somehow -- a second computer -- put the files on USB and transfer them.

---

### Post by TUNDRA35 on 2008-03-22
> **kevdog said:**
> Your going to need internet access somehow -- a second computer -- put the files on USB and transfer them.

ok well i can use this computer cause then i can boot it into Windows Xp and i have a USB drive so. how do i do this??

---

### Post by TUNDRA35 on 2008-03-23
anyone?

---

### Post by Eiríkr on 2008-03-23
Since you have the one machine dual booting, you probably don't need a USB drive.  In Windows, make a note of where you save the files mentioned in kevdog's post.  Then reboot into Ubuntu, open Nautilus (your file browser), and navigate to the [font=courier]/media[/font] directory.  Your NTFS (Windows) partition should be there.  Open that up and find the files you saved, then copy them over to somewhere else in your Ubuntu filesystem, maybe [font=courier]/home/USERNAME[/font] for example.

HTH,

Eiríkr

---

