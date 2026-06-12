---
title: "Issue with Belkin 54G Wireless Network Card"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by HWADIAGF on 2007-03-12
Hi,

  I almost feel guilty requesting help with this after scouring the forums and the internet for the last few days seeing the masses harassing you guru's on how the fix their many ubuntu wireless issues. However, I'm coming to the end of the line and if I can't get this fixed, changes will have to be made I guess. :(

 Please let me know of any additional information which may be helpful.

I have:

Ubuntu 6.10 (obtained via the 6.06 cd then upgrading)
Belkin F5D7010 rev03 based on the broadcom 4306 chipset
(manufactured in the UK) Definately not faulty, been used on XP for years.
I also, do not have the original cd for this device. However, I did obtain bcmwl5.sys. Which i read somewhere is where you could obtain the firmware for the card from.

I'm so twisted in circles right now, I'm lost in some twisted abyss and don't know where to start. If i were to start from scratch what do you think I should do?

Thanks very much in advance for any help you are able to provide.

James.

---

### Post by siciliancasanova on 2007-03-12
If you start from scratch, this is what I did and it worked right away.  I have a Broadcom 4318

[Here]("http://www.ubuntuforums.org/showthread.php?t=381594") is where I posted how I did it.  Although, I was rather lucky.

---

### Post by HWADIAGF on 2007-03-12
I don't seem to be able to find a driver for my card on that site. It is also important to note my card is manufactured in the UK, most of those drivers are US specific. Do all wireless cards have this kind of trouble in Ubuntu? Does anything just get plugged in and work?

Thanks for your help

James.

---

### Post by siciliancasanova on 2007-03-12
Oh, sorry... basically the process from Installing the WINE to using NDISGTK to install the driver is what I was referring to.  The part where you install the driver from Linksys, that was relative to me.  All you have to do is find your driver on the net and download it.

Yes a lot of people are having problems with wireless.  I have only been using Ubuntu for a week but have noticed that they are planning on including a lot more drivers in the next distribution.

---

### Post by HWADIAGF on 2007-03-12
Hi again, just an update.

Your method has got me closer than ever before, but I'm still not quite there I'm afraid.

I installed the driver as recommended and my output it:

[INDENT]ndiswrapper -l[/INDENT]

Installed drivers:
bcmwl5          driver installed, hardware present 

So that appears to be correct. However, still no internet for me.

Any ideas?

James.

---

### Post by siciliancasanova on 2007-03-12
Have you now configured your wireless in **System - Administration - Networking** ?

---

### Post by HWADIAGF on 2007-03-12
Indeed.

---

### Post by siciliancasanova on 2007-03-12
What's your output when you enter```
iwconfig
```

?

---

### Post by HWADIAGF on 2007-03-12
I'm not going to lie is doesn't look pretty...

l> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Hopefully this means something to you though. :)

James.

---

### Post by siciliancasanova on 2007-03-12
If you have a driver that is installed correctly AND configured your SSID it should be showing up on this line...```
eth1 IEEE 802.11b/g **ESSID:""** Nickname:"Broadcom 4306"
```

Here's a look at mine:```
eth1      IEEE 802.11b/g  ESSID:"licari"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:0A:AF:DC   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=30/100  Signal level=-75 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:6  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

In **System > Administration > Networking** did you disable the Network Interface Card and Enable the Wireless Connection?

---

### Post by HWADIAGF on 2007-03-12
Oops, I made a mistake. My wireless was off at the time, as i was checking something. Here, is the output with the card setup.

> lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"Belkin_Pre-N_196864" Nickname:"Broadcom 4306"
Mode:Managed Frequency=2.484 GHz Access Point: Invalid
Bit Rate=1 Mb/s    Tx-Power=15 dBm
RTS thr:off Fragment thr:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

Hope this sheds some light...

P.s. Thanks for your continued help and quick responses.

James.

---

### Post by siciliancasanova on 2007-03-12
Ok, whatever computer is hardwired to your router... login to the router from the browser (192.168.0.1 on my machine, may be different for you) and change the network so that it is an Open and unsecure network.  So in your wireless settings you will only need to have the ESSID.

Also go to **System > Administration > Synaptic Package Manager** and search wifi-radar and install this program.  It claims in the code that was put in the output that:```
Mode:Managed Frequency=2.484 GHz Access Point: Invalid
```

Your access point is invalid.  If in the wifi-radar it shows any access points in the list then that means your driver is installed correctly.

---

