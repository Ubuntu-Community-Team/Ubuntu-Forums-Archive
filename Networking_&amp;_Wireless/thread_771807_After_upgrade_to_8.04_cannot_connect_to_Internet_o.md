---
title: "After upgrade to 8.04 cannot connect to Internet on Windows machines"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by VictorR on 2008-04-27
I have a small LAN at home with one Ubuntu and one-two Windows computers. Ubuntu has a USB ADSL modem (SpeedTouch 330) and provides Internet access to other (Windows) computers via network card and a passive hub.
Everything worked fine in Gutsy, until I upgraded it to Hardy Heron couple of days ago.
Now I have troubles seeing Windows shares, but most important, Windows machines have no longer access to the Internet.
All machines can ping to each other, Internet works for Ubuntu. 
Any ideas?

---

### Post by superprash2003 on 2008-04-28
you probably might need to setup ICS again like how you did in gutsy

---

### Post by VictorR on 2008-04-28
I set up a DHCP server on my Ubuntu computer, so at least all computers are in the same local network now with proper IPs.

Can anybody point me to an article about how to share USB modem connection via Ethernet?

I did it on Feisty, and seems, Gutsy just inherited all the settings correctly, but Hardy did not. I don't remember where I found it.

---

### Post by jetsam on 2008-04-28
There's a how-to here by SpaceTeddy:
[http://ubuntuforums.org/showthread.php?t=713874]("http://ubuntuforums.org/showthread.php?t=713874")

---

### Post by VictorR on 2008-04-28
> There's a how-to here by SpaceTeddy:
[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

The above assumes that I should have two Ethernet cards in my computer, but I did it without second card.

---

### Post by jetsam on 2008-04-28
Right.  I was thinking you could adapt it because of this line:

> In the following, i will refer to the network device that is connected to the internet as eth1. It is not compulsory that the internet device is called that - other possible names are: eth0, ath0, ppp0, ... and many more.

You must have an addressable internet enabled interface or you wouldn't be able to use the internet from the Ubuntu machine, no?

I could be wrong, and I can't help much more...  usb modems and iptables for routing are outside of what I actually know much about.

---

### Post by VictorR on 2008-04-29
Finally got it!
Thanks to SpaceTeddy for his HowTo and with the help from Ubuntu documentation (yelp file:///usr/share/gnome/help/serverguide/C/serverguide.xml#ip-masquerading-iptables) all computers can now access the Internet.
The hardware configuration is as below:
Internet <--> USB ADSL modem (SpeedTouch 330) <--> Ubuntu 8.04 <--> Ethernet card <--> passive 8 ports hub <-->>>>> two other computers (Windows 2000, XP or Vista)

---

