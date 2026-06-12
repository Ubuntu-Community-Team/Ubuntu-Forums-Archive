---
title: "Feisty wireless - so close I can...  taste it!"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by kolchak on 2007-04-23
I've been reading many of the posts here, but I may be getting lost in the details, so I thought I'd try posting myself.

I've built a new desktop that I want to locate in the attic (to keep it out of reach of the wee ones), and I want to use wireless so I can do most of my work via FreeNX.  I'm using a TRENDnet TEW-443PI (comment in the compatible card list is "works out of the box... easiest install ever... etc.), with a fresh install of 7.04. Before touching anything, the /etc/netwok/interface file looks something like this:
=====
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
=====

I used the GUI network manager to add my wireless info, and it was placed under the ath0 entry.  I also manually added a line for my channel, so the file now looks like this:
=====
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid MyIDHERE
wireless-key s:KEYSTRINGHERE
wireless-channel 11

auto wlan0
iface wlan0 inet dhcp
=====

If I specify ath0 when I scan, it works great; it sees my own wireless router, as well as my neighbor's.  On my wireless router, it even shows the computer in question as an attached device, with an IP assigned.  But I still can't connect - "NETWORK NOT AVAILABLE."

What am I missing?  THANKS!

---

### Post by Kobalt on 2007-04-23
If you use Network-Manager then you should comment (put # at the begining of the lines) this part of your /etc/network/interfaces file : 
> wireless-essid MyIDHERE
wireless-key s:KEYSTRINGHERE
wireless-channel 11
NM manages this all by himself : it will prompt you which networks are available and then ask for your wep/wpa key. 
Once you commented these lines restart your network with ```
sudo /etc/init.d/networking restart
```

---

### Post by hyperair on 2007-04-23
Go to System->Preferences->Hardware Information. Look for your WLAN adaptor, and check around the right panel for the driver it's using. Since your card is called ath0, I reckon it's using the acx range of drivers which just don't work with NetworkManager. So, you have to find some way to install and configure  your card with ndiswrapper. That will allow your card to work more stably and with NetworkManager support.

You can follow these instructions: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

It's pretty much the same with most other wireless cards. You have to use your own windows driver files though, they can be gotten from the manufacturer's website.

---

### Post by kolchak on 2007-04-25
Just wanted to thank you for your replies...  Due to work commitments, I haven't had a chance to get back to working on my own box.  In the meantime, I'll keep scanning this forum.

---

