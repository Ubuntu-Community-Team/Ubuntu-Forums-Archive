---
title: "Trouble connecting to Actiontec wireless gateway"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Jairus_k on 2007-01-14
Hey guys, I just downloaded Dapper Drake today, and I'm itching to explore it and learn more about it, but I can't connect to the internet on my wireless connection for soem reason... I've tried to mess around with the preferences for my network settings, but I guess I'm either completely stupid or just a noob, cause I can't figure out any way to get close to a connection. When I plugged in my ethernet cable from my desktop (Which is what I'm on right now) I got a connection right away, but it still was fussy when I tried to load up web pages. I really need to get my wireless internet working... anyone have any advice?

---

### Post by Floppyjoe on 2007-01-14
More information is needed:
Like how you are connecting to the internet? I'm assuming it is through a wireless router:
If so what is the name of your wireless adapter:See if it is [[COLOR="Blue"]supported[/COLOR]]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz") by Linux

Post the output of:
```
iwconfig
```

Post the contents of /etc/network/interfaces:
```
sudo gedit /etc/network/interfaces
```

---

### Post by Jairus_k on 2007-01-14
It's an actiontec GT 701-WG... I think.. that's all I could find on the bottom of the modem.

Here's what I got from iwconfig:
```

lo           no wireless extensions

eth0       no wireless extensions

eth1       IEEE 802.11b/g ESSID:"ACTIONTEC"  Nickname:"Broadcom 4306"
             Mode:Managed  Access Point: Invalid  Bit Rate=1 Mb/s
             RTS thr:off  Fragment thr:off
             Link Quality:0  Signal level:0  Noise level :0
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0        no wireless extensions

```

Here's the contents of /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider


```

Sorry if there's a typo or two, I had to type all that by hand..

---

### Post by Floppyjoe on 2007-01-14
Try this command in the terminal and see if scanning works:
```
sudo iwlist eth1 scan
```

If that shows you your router than you probably just need some simple setup.

---

### Post by Jairus_k on 2007-01-14
Nope, doesn't work. 

```

eth1      Interface doesn't support scanning : No such device

```

---

### Post by Floppyjoe on 2007-01-14
```
sudo gedit /etc/network/interfaces
```

Add the following to the interfaces file in the eth1 section:
Instead of channel 7 use the channel your router is using.
> wireless-essid ACTIONTEC
wireless-channel 7
wireless-mode managed

to get something like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ACTIONTEC
wireless-channel 7
wireless-mode managed

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider

then make sure your wireless interface is activated in System/Administration/Networking
then deactivate your wired interface 
then restart

---

### Post by Jairus_k on 2007-01-15
Okay, it's restarting..
Does it make a difference if it's running off of the live disc or not? I haven't been able to install it yet for some reason.. it couldn't partition my hard drive.. maybe that's because it's NTFS? Am I going to have to partition it myself before I can install Ubuntu?

---

### Post by Floppyjoe on 2007-01-15
I don't think you can make any configuration changes with the live CD.
I thought you had it installed.

---

### Post by Jairus_k on 2007-01-15
Oh my god, I'm so sorry... I'll try to get it installed right now!

---

### Post by Floppyjoe on 2007-01-15
When you go to install on a windows Xp partition you need to defragment the drive first: 
Then you need to temporarily remove the windows swap file space being carefull to write down the numbers that it was using.
Then you can install Ubuntu which will resize the partition of Windows and use the freed up space for Ubuntu.
Then you reenter the swap file info in Windows.


Be very careful when you do stuff like this.
It would be wise to backup important Data on Windows first.

---

### Post by Jairus_k on 2007-01-15
I've got Ubuntu installed, everything seems to be working fine, except for my wireless, of course... I changed the /etc/network/interfaces file, but I'm still having trouble. I put in my WEP key and my ESSID name, but even when I activate eth1, my wireless won't connect.. what else can I do to get this to work? I'm starting to go crazy without internet on my laptop ](*,)

---

### Post by Floppyjoe on 2007-01-15
What is the output of:
```
lspci
```

---

### Post by Jairus_k on 2007-01-15
Sorry it took so long. I had to type it out by hand again... I tried to make sure that there were no spelling errors though.
```

0000:00:00.0 Host Bridge: Intel Corporation 82855PM Processor to I/O Controller
(rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller
(rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
0000:02:00.0 Ethernet controller:  Broadcom Corporation NetXtreme BCM5605M Gigabit Ethernet (rev 01)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by Floppyjoe on 2007-01-15
This is your wireless adapter here:
> Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I have the Broadcom BCM 4318 in my laptop and use ndiswrapper to get it to work.

Here is a howto I found for that device:
[http://www.ubuntuforums.org/showthread.php?t=189070&highlight=Broadcom+4306+howto](http://www.ubuntuforums.org/showthread.php?t=189070&highlight=Broadcom+4306+howto)
Hopefully it wont be to difficult for you to follow and implement .

I found another one that may be easier to follow:Plus it has the drivers.
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306+howto](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306+howto)

Hope this helps!

---

