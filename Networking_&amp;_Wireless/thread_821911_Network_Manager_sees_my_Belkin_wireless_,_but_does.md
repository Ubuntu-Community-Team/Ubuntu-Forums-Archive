---
title: "Network Manager sees my Belkin wireless , but does not connect"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by rcraw0629 on 2008-06-07
Hey,

I have a HP Pavilion a230n tower with a Belkin USB(F5D7050)wireless stick. It has the ZD1211 firmware. iwconfig sees this as eth1. I'm getting the connection from my landlords 2Wire DSL Router/Modem. WinXp home and Pro have no problems. On Puppy linux using Pwireless scanner I can connect.It uses a secure key. Is there a wireless scanner similar to Pwireless for Ubuntu? 

rcraw0629

---

### Post by Unix_Slayer on 2008-06-07
> **rcraw0629 said:**
> Hey,

I have a HP Pavilion a230n tower with a Belkin USB(F5D7050)wireless stick. It has the ZD1211 firmware. iwconfig sees this as eth1. I'm getting the connection from my landlords 2Wire DSL Router/Modem. WinXp home and Pro have no problems. On Puppy linux using Pwireless scanner I can connect.It uses a secure key. Is there a wireless scanner similar to Pwireless for Ubuntu? 

rcraw0629

All you would need is knetworkmanager. If you know the secure key, it will show, and allow you to connect in there.

---

### Post by issih on 2008-06-07
if you are running ubuntu (rather than kubuntu) you should try using the network manager applet. By default that should be in the notification area up on the top right. It looks much like a network connection icon in windows (just don't tell mr gates I said that). If you right click on that, you ought to see an option to "enable wireless", ensure that is on, then left click on the icon.

You should see a list of networks that the card detects, simply click on the one you want to use, and that will being up a dialog for entering the type of encryption and the key.

If that isn't working you probably need to check your wireless card is working properly. To check it does see networks, enter:

```
iwlist scan
```

in a terminal window and see if it lists any networks.

One other good option to look into is replacing network manager with wicd, some people find that more intuitive.

---

### Post by rcraw0629 on 2008-06-09
Thanks for all the help. I got it working, I was not using the Hex key type. 

rcraw0629

---

