---
title: "No Network?"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by sebz2005 on 2005-11-05
My network card fired on me prior to my installation of Ubuntu. I have then added the card after the installation. What do I do to get Ubuntu to see my card?

---

### Post by mxyzptlk on 2005-11-05
go to system > administration > network and take alook if your device is there

if so you must configurate it

please post here 

kind of network
dhcp or static
shared connection or no
type of card

and all information related to your network devices

---

### Post by sebz2005 on 2005-11-05
Um... Where's the administative panel? I can't find it!
Ethernet Network
Static IP
Not Shared
NetGear FA311

It seams that I need to download the network drivers. Hmz....

---

### Post by Lambert on 2005-11-05
The top panel you should see System. Click there and you should see Administration in the menu. If you don't see this you can hit alt+f2 and type in network-admin.

Look for ethernet connection, click on properties and fill in the blanks.

You can als In a terminal type

```
ifconfig
```

you should see something like eth0. If so your hardware is present. You just need to configure it to your network settings.

---

### Post by sebz2005 on 2005-11-06
All I see is (localhost,127.0.0.1)
But I don't have apache. I need the network connection to get the installations files.

---

