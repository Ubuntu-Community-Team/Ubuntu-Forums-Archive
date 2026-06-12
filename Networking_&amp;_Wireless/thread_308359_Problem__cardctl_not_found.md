---
title: "Problem : cardctl not found"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by DarkAngel88 on 2006-11-27
Greetings everyone !!

I have a... special problem !!  

I just did a fresh install of Ubuntu 6.10 and I'm using my Prism2 wireless card (which is PCMCIA) to access the internet without any problems.  When I type "iwconfig", I can see wlan0, which is my Prism2 card using the hostap drivers.  Only problem, when I'm trying to eject the card using cardctl eject, I get an error saying :

```
sudo: cardctl: command not found
```
The thing is that before doing a fresh install of 6.10, I was using the same thing and was using the cardctl command without any problems.

So my question is... is cardctl a part of a special package that I have to install manually ??  Where can I get it ??

Would be great if someone can help me on this !

Thank you !

---

### Post by drphilngood on 2006-11-28
See the _4.1.2. Non recognized card_ section of the [WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

Hope this helps.

---

### Post by FrodoB on 2006-11-28
The package is:

pcmcia-cs

I believe.

---

### Post by DarkAngel88 on 2006-11-28
> **FrodoB said:**
> The package is:

pcmcia-cs

I believe.

You got it right !  A simple apt-get install pcmcia-cs did the work !

Thank you very much !

---

### Post by yeehawjared on 2006-12-02
money.. works for me too. thanks :)

---

### Post by hakre on 2007-11-11
my friend using sidux did not help the installation of that package. afterwards the command is still not found. i assume this is sidux related but how can it be?

---

### Post by costis on 2008-07-08
sidux uses /sbin/pccardctl :D

---

