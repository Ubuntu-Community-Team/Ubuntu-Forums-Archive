---
title: "Network Manager doesn't do anything"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by pwaller on 2006-10-31
I have searched around a fair amount,

I have edited /etc/network/interfaces
I have edited /etc/dbus-1/system.d/(nm-applet|networkmanager).conf

And the nm-applet icon in the tray still won't do anything. It just lists 'enable wired connection'
'enable wireless connection'
'connection info' (greyed out, can't be pressed)
'about'.

I'm guessing there is supposed to be more to the networkmanager than this, for example, somewhere to enter wireless keys?

I even tried upgrading to 0.6.4 by compiling from scratch but this also had no effect.

I'm currently manually configuring the wireless essid and key through a terminal with iwconfig. This is bugging the hell out of me, it's a waste of my time. Why can't I get it to work automatically?

I should probably mention I'm running edgy, and all of my packages are up to date. I was previously using 'whereami' but would rather use something more simple with a graphical interface.

Thanks in advance

---

### Post by bran on 2006-10-31
you need to go to System>admin>networking  and dsable the interfaces through the default app in the properties tab of each interface.

---

### Post by featherking on 2006-10-31
that will have the same effect as editing the /etc/networking/interfaces file. What is in that file, could you post the contents?

---

### Post by pwaller on 2006-11-01
Two lines:

auto lo
iface lo inet loopback

---

### Post by pwaller on 2006-11-02
No-one has any ideas?

---

### Post by pwaller on 2006-11-03
Another problem I have is some service or other keeps messing with my manually configured settings. If I ifconfig eth0 to some IP address, it will lose it as soon as I remove & reinsert the network cable.

---

