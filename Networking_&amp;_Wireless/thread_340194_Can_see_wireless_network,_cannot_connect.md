---
title: "Can see wireless network, cannot connect?"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Monstroxus on 2007-01-16
I have a laptop with a broadcom wireless card, after following some instructions as mentioned here on the forum, I got it "working".

The "wireless light", (antenna light logo thingy on the laptop itself) blinks now (before it didn't do anything), and the "gnome network manager" shows the wireless networks available. Yay!

However... when I attemp to connect, the following happens... the connection logo turns and turns and finally stops, and mentions that there is no connection. :(

So simply said, it can see the wireless networks, but cannot connect.

I tried this in a hotel and a Starbucks kind of place, where you just can connect without any password and such.

Anyone any idea how to fix this?

Thanks!

---

### Post by discord on 2007-01-17
the ubuntu gnome network manager did not work for my broadcom chipset using ndiswrapper. I made instructions somewhere on launchpad. search for bugs reported by discord. Anyways you can manually set the network ssid

by

sudo iwconfig wlan0 essid "networkname"
sudo dhclient wlan0

---

### Post by featherking on 2007-01-17
[http://live.gnome.org/NetworkManagerHardware]("http://live.gnome.org/NetworkManagerHardware")  Lists the hardware supported by Network Manager, the broadcom chipset is listed, but apparently not under ndiswrapper. The driver they list links to some other driver? perhaps only that driver is compatible with NetworkManager, i dont have a broadcom so i am just making a suggestion?...

---

### Post by discord on 2007-01-17
bull broadcom 4311 works with my ndiswrapper in edgy!

---

### Post by kidamnesiac on 2007-01-17
I'm having the same problem with a different card and so are lots of other people...

[http://www.ubuntuforums.org/showthread.php?t=340223](http://www.ubuntuforums.org/showthread.php?t=340223)

---

### Post by kidamnesiac on 2007-01-17
bump

---

### Post by Monstroxus on 2007-01-17
Thanks for these suggestions, I gonna try them and see if there is any positive result.

---

### Post by discord on 2007-01-25
follow my instructions i got my 4311 working i have a dell inspiron e1505 [https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

