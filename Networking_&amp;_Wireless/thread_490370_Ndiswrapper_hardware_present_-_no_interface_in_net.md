---
title: "Ndiswrapper: hardware present - no interface in network GUI - Feisty"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by gloucestershrubhill on 2007-07-02
Hello,

I am a very new user of Ubuntu, and would like to setup my 3com 3CRGPC10075 PCMCIA card (Marvel chipset). I have installed ndiswrapper and installed the driver:

```
joe@joelinux:~$ ndiswrapper -l
mrv8335x         driver present, hardware present
```

I have also modprobe'd ndiswrapper, and lsmod, lists it as inserted. However, it was not inserted after my last reboot - how can I permanently insert it at boot?

To the nub of the issue: even with it inserted, I get no interface in the network GUI - only ethernet and lo. It is in /etc/network/interfaces. The wireless network is at this stage without any security like WEP. I will add it later.

I have barely used ubuntu, so I would appreciate it if you could take me step-by-step. I don't even know what the terminal is! This was written for me by a friend with more experience.

Thanks for any help,

G.J.S.

---

### Post by TrueJk7 on 2007-07-02
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It sounds like you already know well what you are doing. 

The problems I had was the default driver kept loading @ start up so I had to do the /etc/modeprobe.d/blacklist (not @ computer so directories may not be accurate) and add the driver to it. My case was "blacklist bcm43xx"

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3)

As far as that not showing up in the network GUI. I've fixed it a few times however I am never that certain what exactly I did to remedy the situation

---

### Post by gloucestershrubhill on 2007-07-03
OK. I could try blacklisting the driver but how do I know which is the correct driver?

BTW, I don't think the driver does load because the light on the card has yet to illuminate in ubuntu.

---

### Post by gloucestershrubhill on 2007-07-03
OK, well I blacklisted the driver you mentioned and added ndiswrapper to /etc/modules and it loads at boot. No errors with ndiswrapper in /var/log/messages/ but there is no sign of an attempt to connect to a network.

If I do ifup wlan0 it says something to the effect of "no such connection". I don't have an internet connection on the Ubuntu box, so it's a little difficult to post output.

---

### Post by #Reistlehr- on 2007-07-04
to get it to start, you need to do, after you boot:

sudo depmod -a
sudo modprobe ndiswrapper

i figured that much out, but i cannot get it to automatically start the ndiswrapper module on boot either.

---

### Post by kevdog on 2007-07-05
Ndiswrapper creates by default an interface on wlan0.  So you need to modify your /etc/network/interfaces file accordingly to have an entry for wlan0

Second, you can not run wired and wireless internet at the same time.
Third - there may be a conflict in your /etc/iftab file.  If you post it we could take a look
Fourth- please post lshw -C network right after booting, and then after getting wireless up and running.  I would be helpful to see if there is a driver reassignment
Fifth-did you add ndiswrapper to the /etc/modules file?

---

