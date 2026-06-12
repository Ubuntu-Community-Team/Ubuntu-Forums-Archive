---
title: "Hardy is not detecting wireless network card on boot"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-04-25
This is strange hardy is not starting the wireless network card on boot.

I have to fully boot and then unplug the usb network wireless dongle and then plug it back in and after that restart the network.

How can I make hardy detect the network card on boot?

Thanks.

---

### Post by DanlG on 2008-10-12
I've had this problem on three different computers. One with a USb wireless dongle, one with a pcmcia card, and another with a built in wireless interface.

I've always gotten them to work by messing around with things, but recently I came across a simple solution posted by someone here:  Add the line
pre-up sleep 10
in your /etc/network/interfaces file.

The computer with the USB dongle needs sleep 20, but you get the idea.  My guess is that linux is trying to bring up the wireless device before it has initialized

---

