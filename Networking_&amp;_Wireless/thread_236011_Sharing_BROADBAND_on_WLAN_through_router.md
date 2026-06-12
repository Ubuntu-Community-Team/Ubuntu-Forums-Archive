---
title: "Sharing BROADBAND on WLAN through router?"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by tablist56 on 2006-08-14
hi there folks...im pretty sure i got my wireless working but i still cant use the net on my laptop through a wlan or wifi.

i have pinged my router and that was fine.
i pinged the internet and a get a time out.

what could be wrong?

Intel Proset/Wireless says "You are connected to tablist56" which means im connected to the network yet my net is still not working?

if i right click, properties on my wireless connection it says...

124 packets send, 2 recieved.
signal strength - 5 bars
speed - 54 mbps


can somone please help me???

thanks to anyone who contributes. its much appreciated.

---

### Post by tablist56 on 2006-08-14
im using a motorola sb4200 surfboard modem and a d-link DI-524 802.11g 2.4 ghz router.

---

### Post by tablist56 on 2006-08-14
in the internet protocol properties i have check both boxed to obtain ip and dns automatically. using motorola sb4200 and dlink DI-524 and also have firewalls off.



any experienced people who can give good help here?

---

### Post by mozetti on 2006-08-14
Which network jack on the back of the Dlink router did you plug the modem cable into? Basically, you connection should look like this:
```
Phone jack<-->sb4200<-->WAN port on Dlink router<--
--->Computer hardwired to LAN 1-4 on Dlink router (if you have hardwired PCs)

--->Laptop connected via WiFi
```

If the network cable coming out of the sb4200 isn't connected to the WAN port on the router then you won't be sharing the internet.

---

### Post by tablist56 on 2006-08-14
i have usb cable connecting my cable modem to desktop which is my primary internet connection.

i have connected another ethernet cable from the cable modem to the WAN port on the router. laptop connected to router via wireless. it says "connected" and i get packets sent/recieved but no net?

i can ping my router but not the internet. i tried to ping yahoo and that didnt work.

are there any settings that should be done on my desktop or are all the settings soley on the wireless laptop provided cables are connected correctly?

---

### Post by NetworkGuy on 2006-08-14
> i have usb cable connecting my cable modem to desktop which is my primary internet connection.

i have connected another ethernet cable from the cable modem to the WAN port on the router. laptop connected to router via wireless. it says "connected" and i get packets sent/recieved but no net?

Even though the sb4200 allows you to connect both the Ethernet and the USB connections, your ISP may not allow them both to be active at the same time.  Usually ISP's will only give you one IP address.  

From what I read about your config, your desktop needs an IP address and your wireless is trying to get another.

Try plugging your desktop PC into your wireless router instead of your modem.  Reset your moden and your wireless router and see if everything connects up.

---

### Post by bensexson on 2006-08-14
How are you sharing your connection from the desktop?

---

### Post by tablist56 on 2006-08-15
you will be pleased to hear that it all worked!!!!!!!

thanks guys :)

i also had to power cycle my router and modem to get it to work.

i can both share files and share internet aswell.


thanks again to everyone who contributed!

---

### Post by tablist56 on 2006-08-15
by the way am i supposed to leave my firewall off now while both computers are on the internet and when i share files???

i think i had to turn both firewalls off and all the virus protection stuff too.

is there any security measures i can take?


thanks

---

