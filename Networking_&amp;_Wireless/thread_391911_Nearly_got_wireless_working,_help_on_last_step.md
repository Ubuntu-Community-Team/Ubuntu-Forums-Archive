---
title: "Nearly got wireless working, help on last step"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by super.rad on 2007-03-23
ok so i've followed this guide [http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980") and it seems to have worked (i can ping my router) at the moment im connected to a wired network. My question is how do i set it to use the wireless now? im using network manager and their's no option of wireless on it, i was going to go into system > administration > networking and deactivate the wired connection and enable the wireless but i seem to remember reading that it will cause ubuntu to stall on boot.
Sorry for going on and thanks to anyone who can help

EDIT: Sorry forgot to add, im using a static ip address

---

### Post by mouseboyx on 2007-03-23
You probably need to install the drivers for the wireless card using ndiswrapper or whatever its called. OR. Do you even have a wireless card?

---

### Post by super.rad on 2007-03-23
yes i have a wireless card (Belkin PCI RT61 Chipset) and i have followed that guide and installed the drivers, my question was how do set it to use wireless instead of wired

---

### Post by raja on 2007-03-23
You can enable wireless from the network menu - it wont cause a problem. What do you get as output for ```
iwconfig
```

---

### Post by super.rad on 2007-03-23
```
jimin@jimin-ubuntu:~$ iwconfig
lo        no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by raja on 2007-03-23
Doesnt look like you have a working driver. You might have to go through the steps to get a working driver again.

---

### Post by super.rad on 2007-03-23
Ye just noticed it hasnt got the network name or anything, i found this thread [http://www.ubuntuforums.org/showthread.php?t=240669]("http://www.ubuntuforums.org/showthread.php?t=240669") had a read through it and from what i understand i add the repositorie then download the rt61 driver, but what im not sure about is will i still need to configure it all or do i just download it and it will work. Also i saw on another thread that network manager doesnt work if you're using wireless with static ip's, is this true?

---

### Post by raja on 2007-03-23
Getting wireless to work can sometimes be a pain. I would recommend you to take some time with this site. -https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#iwconfig
I am not sure about a problem with network manager and static IPs.

---

### Post by super.rad on 2007-03-23
cheers i'll look through that tomorow, off to bed now had enough for one night. Thanks for all the help

---

### Post by chili555 on 2007-03-23
With respect to my esteemed colleagues, I believe you *do* have a working driver for your interface ra0. This:```
ra0  RT61 Wireless  ESSID:""
Mode:Auto  Channel:0
```suggests to me your interface is all tuned up and ready to fly. It wants to know to whom should it associate. I would do:```
sudo iwlist ra0 scan
```to see if you get scan results. Then you will know the ESSID and the access point MAC address to command ra0 to connect to. You will also know if there is encryption to be set up.

You will want to do, in order:```
sudo iwconfig ra0 mode managed
sudo iwconfig ra0 channel auto
sudo iwconfig ra0 essid <what_you_found>
sudo iwconfig ra0 ap 00:13:10:62:8D:7F
sudo dhclient ra0
```Substitute your scan findings here. Let us know.

---

### Post by Frak on 2007-03-24
I created a script [here]("http://ubuntuforums.org/showthread.php?t=392017") that will alow you to automatically install the driver and configure it.

I hope it helps.

---

### Post by super.rad on 2007-04-02
thanks, im back at home for easter holidays but once i go back to uni i shall try that

---

### Post by Alabaster on 2007-04-02
I've been struggling with network-manager as well. It doesn't let you use static IP. In fact, it is pretty damn useless. I have a computer I am trying to set up as an access point with an internet connection and I can manually configure eth0 to use a static IP address, but as soon as you touch it using the default Ubuntu networking tool network-manager simply ignores it.

---

### Post by Frak on 2007-04-05
> **Alabaster said:**
> I've been struggling with network-manager as well. It doesn't let you use static IP. In fact, it is pretty damn useless. I have a computer I am trying to set up as an access point with an internet connection and I can manually configure eth0 to use a static IP address, but as soon as you touch it using the default Ubuntu networking tool network-manager simply ignores it.
Don't use the networking-tool. The driver wasn't made to support the options of anything exept the rt61.dat file.

---

### Post by Alabaster on 2007-04-10
What would you suggest I use instead?

---

### Post by Frak on 2007-04-10
Editing the rt61.dat file with vi or vim in binary name (vi OR vim -b /path/to/rt61.dat file)

---

