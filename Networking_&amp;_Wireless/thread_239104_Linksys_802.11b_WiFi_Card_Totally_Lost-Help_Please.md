---
title: "Linksys 802.11b WiFi Card Totally Lost-Help Please!"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by gigi1234 on 2006-08-18
Hi'yall,

I have never used wireless before and am somewhat of a newbie too. Got a Linksys Wifi PCMCIA card, 802.11b, because I read that it works with Dapper.

The device is recognized under the device manager, but that's it. I don't have the slightest idea what to do to get it to work.

Do I need a driver? What is ndiswrapper? I have tried reading some forum posts but nothing seems to make sense to me. 

Could someone at least give me a good place to start?

Thanks!

---

### Post by meng on 2006-08-18
Not familiar with this particular card, but when you say "that's it", do you mean that it isn't recognized as a network interface by System > Admin > Networking?

---

### Post by byen on 2006-08-18
I have a Linksys WPC11 card and it works out of the box. If this is the same card that you have... then just follow meng's advice you should be set.. just  select the wireless network that you would like to join via the drop-down menu in System>Admin>Networking>Wireless>Properties and you should be ready to fly...
Let us know if the card is the same and if you can get it running..
Goodluck

---

### Post by gigi1234 on 2006-08-18
Yes it is the same card, Linksys WPC11. If I go to system->administration->networking, I see that "the interface wlan0 is active". So that is good right?

But I have no idea what to do in the "properties" section.

I would likely use the connection at any number of hotspots all over town. How do I know what the "network name" is? Does this mean every time I am at a new location I will have to reconfigure the network settings? 

I am totally mystified by this process. 

BTW the card works in XP-I tested it today down at my local library.

---

### Post by meng on 2006-08-19
Sounds promising for you. It's nice to know the ESSID of the network you wish to connect to, although it may not be strictly necessary for connecting to open networks. Obviously if there's a WEP key you'll need to specify it. Some folks swear by network-manager which has a gnome applet (nm-applet), but I couldn't get this to work for me, and I just use the tools that come with default install.

---

