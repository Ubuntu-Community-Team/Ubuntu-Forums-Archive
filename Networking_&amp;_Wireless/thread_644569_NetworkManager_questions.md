---
title: "NetworkManager questions"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by domiflichi on 2007-12-19
Hello,

I've got a couple of questions about the NetworkManager Applet (0.6.4 in Ubuntu 7.04 Gnome):

First, let me give a couple of specs on my computer - Dell Inspiron 6400 - Internal wireless, Netgear WG111 v2.

K, here's my problems/questions:

1. Is there a way in the NetworkManager Applet to disable *one specific* network connection/card? I looked at the built-in help, and it says that you can just uncheck the box by your network connection/card, but the only network adapter I can do that with is the wired connection. I guess what I really should be asking here is there some way to tell the NetworkManager to *not* manage a certain adapter? I've been playing with aircrack-ng and everytime I put my WG111 in monitor mode, it goes into managed mode a minute later, and I found out after some searching that it was the network manager doing this. Which brings me to my next question

2. If there is not a way to do the above, is there a better network manager (I tried KNetworkManager, but could not see a way of disabling a single adapter) i should be using that allows me to do what I want? (Selectively manage network adapters?). Which brings me to my next question:

3. If there is not a better program/way to do what I want, is running the following command the best way to temporarily stop the network manager from taking over my card:

```
sudo killall NetworkManager
```

This is my worst case scenario as this kills my internal wireless card too...which is undesirable because I would still like to use it to browse the internet while having my other NIC (the WG111) in monitor mode.

---

### Post by Junglizer on 2007-12-19
In the command line run (assuming that eth0 is what device you want to disable)
```
root@box~# ifconfig eth0 down
```
If it is a wireless device, use **iwconfig** instead.

---

### Post by Junglizer on 2007-12-19
Are you putting it into monitor mode through the Network Manger? If you're going to that trouble, I'd recommend doing it all through the command line, or whipping up some scripts that you can run whenever you wish to maintain this setup.

---

### Post by Junglizer on 2007-12-19
Though, the best bit of advice I can give is to not use the gui at all, but if you (like me) like to surf the web on occasion, I would higly recommend the Fluxbox window manager, or possibly Xfce windowmanger (xfce is nice b/c you can have icon's on the desktop. You can do that in fluxbox, but that just is dumb, it takes away from its sole reason of existing imo)

---

