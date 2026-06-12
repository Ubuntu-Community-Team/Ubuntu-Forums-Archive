---
title: "Wireless won't connect in Feisty"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by ziadoz on 2007-04-22
Hi,

I'm running Feisty from a fresh install on my Compaq Presario 5214EA laptop. Under Edgy I had to use ndiswrapper and network manager to gain access to my wireless network, once they were setup wireless was fine and I could select any network and connect with no problems. 

Under Feisty however I can't seem to connect. My wireless is a broadcom 4311 (I think) and is setup as wlan0 using ndiswrapper 1.42. It scans for networks fine, and my network (and my neighbours!) shows up in network manager. However I just cannot connect to my network at all. On one occasion it said it was connected, however it clearly wasn't since I had no internet access and had not put in my WPA key phrase for the connection.

Is there anyway around this problem? I've tried different versions of ndiswrapper (1.37) and network manager (0.6.3) and other wireless applications (wicd, wifi-radar) too. Also is there anyway to report this issue, seems like a problem others are experiencing too and really needs fixing.

Thanks

---

### Post by jørgen on 2007-04-22
I have the same problem, in Edgy wireless worked out of the box. Feisty finds all my networks and I can connect to them, but internet isn't working :confused:

---

### Post by High Roller on 2007-04-22
Same problem here.  BCM4318.  I used ndiswrapper + the standard driver and it sees the router and knows to ask for the WPA2 password but fails to connect.  Just sits there spinning and eventually stops trying.

The reverse-engineered BCM43xx drivers work but they're slow and only connect at 11kb/s.  I'm using a linksys WMP54GS wireless PCI card.

---

### Post by ziadoz on 2007-04-22
Heres to hoping it gets fixed soon. My laptop is a pretty looking brick without wireless. :p

---

### Post by ziadoz on 2007-04-22
Sorry for the double post. But I compiled a new kernel (2.6.20) and my wireless now works like a charm.

---

### Post by danieltellez on 2007-04-22
I've got  the same problem.

I had used wicd and network manager. With wicd (the last option) i can see my wireless network but i cannot connect to. 

I have a dlink DWL 122 and feasty distro.

---

### Post by H.E. Pennypacker on 2007-04-26
This problem has been addressed in the BCM4318 thread by compiz.  The solution appears to be uninstalling ndiswrapper, and installing the latest ndiswrapper version from source.

---

