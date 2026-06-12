---
title: "Wifi works from Network settings but not Network Manager"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by MarkFlegg on 2007-02-02
Hello:

I've recently installed Ubuntu 6.10 Edgy Eft on my laptop.

I'm using a Syntax Wireless USB-400 dongle, which uses the Prism 3.0 chipset. I have this working using ndiswrapper and the EU3USB.sys and EU3NIC.inf driver files.

If I go through System:Administration:Networking I can see the wireless interface and connect to my network with no problem (WEP is working fine).

However, it refuses to show up in the Network Manager monitor applet. My ethernet connection shows up in both places and works fine.

My /etc/network/interfaces looks funny to me (blank lines stripped to save space):
[INDENT]auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
iface wlan0 inet dhcp
auto wlan0
iface wlan1 inet dhcp
wireless-essid Borshoeloopienet
wireless-key F05C5473B96E93259E8F33B5B5
auto wlan1
auto eth0[/INDENT]

I tried eliminating wlan1 and putting the config information in wlan0... wireless networks started showing up in the Network Manager but I lost the ability to connect.

Any ideas of what to look at next will be greatly appreciated!

---

### Post by jpeddicord on 2007-02-02
The Network Manager version in Edgy does omit some cards, namely Atheros and some Prism chipsets. It might be fixed in the future through the Backports repository, although I'm pretty sure the GNOME developers are focused on fixing it in GNOME 2.18 (Ubuntu 7.04) rather than trying to patch the current revision.

So, unfortunately you just have to live with it for now. :-k

---

### Post by pegazuz on 2007-02-02
> **jacobmp92 said:**
> The Network Manager version in Edgy does omit some cards, namely Atheros and some Prism chipsets. It might be fixed in the future through the Backports repository, although I'm pretty sure the GNOME developers are focused on fixing it in GNOME 2.18 (Ubuntu 7.04) rather than trying to patch the current revision.

So, unfortunately you just have to live with it for now. :-k

Since I have an atheros chipset, I take this to mean I better stay with Kubuntu 6.06 to keep my wireless network connection and not plan any upgrade to 6.10 soon. 

 I was wondering why I saw several posts recommending beginners to stay with 6.06 when starting out.  At what point would you recommend a beginner consider doing an upgrade?

---

### Post by MarkFlegg on 2007-02-03
> **jacobmp92 said:**
> So, unfortunately you just have to live with it for now. :-k

Good to know, thanks for your reply. It's not that big of a deal, really. I've got wifi working, and I imagine I'll be able to get into public networks no problem by finding them in wifi radar and then manually entering them in Network Settings...

---

### Post by stavaroti on 2007-02-07
Hi,

I am a noob, so please forgive me for any errors.  I just installed network manager and it installed fine.  However network manager only displays the wired connection but no wireless connection.  Any help would be appreciated.  I just installed ubuntu, the newest stable release 2 days ago, and i think that have version 6.10

---

### Post by wudsta on 2007-02-07
You need to disable all the connections in Network Settings in order to allow Network Manager to handle them (basically uncheck all the "enable this connection" options for all your connections).

I also commented out everything from /etc/network/interfaces  apart from;

auto lo
iface lo inet loopback

Network Manager now works perfectly.

Don't know if thats any help.

:)

---

