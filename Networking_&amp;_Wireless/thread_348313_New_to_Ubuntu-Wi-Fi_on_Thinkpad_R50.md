---
title: "New to Ubuntu-Wi-Fi on Thinkpad R50?"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by PhreQuencYViii on 2007-01-28
I tried searching and looking at howtos and stuff, and I still can't figure out how to get the wireless working on my Thinkpad R50. I've used Ubuntu before and I'm good with computers, but don't know anything about Linux. I stuck Ubuntu on my laptop because I was bored of Windows and wanna learn how to use Linux! For now I just need my Wi-Fi working for home. I have a Dlink router that uses a shared WEP key, but I also need to know how to get the Wi-Fi to work at the school, which is unsecured. Thanks!

---

### Post by flossgeek on 2007-01-28
Just go to System>Administration>Networking, fill in your required details and should be fine. See [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29)

Of course there is extra software which can help you have a easier life with your roaming needs. You could try Network Manager - [https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29](https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29)

---

### Post by PhreQuencYViii on 2007-01-28
I got all that info filled in now, but I still don't get any internet. It's wifi0 right? I have eth0 (Must be the ethernet port) ath0 (no idea), lo (No idea) and wifi0 which I guess is the wifi card. When I look at device manager it says the WiFi is an unknown device, do I need to install drivers or something?

---

### Post by flossgeek on 2007-01-28
What Wireless Card do you have? 

I presumed it was an Intel as I have an IBM Thinkpad R50e which has an Intel wireless card. Try this guide to troubleshoot [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by PhreQuencYViii on 2007-01-28
Looks like its a Atheros AR5212, or at least thats the vendor and chipset. It's a built in Mini PCI in the laptop.

---

### Post by chili555 on 2007-01-28
The harder way is madwifi and the easier way is ndiswrapper, both of which are waiting right in that Search button up there.

Good hunting and post back if you need more help.

---

### Post by PhreQuencYViii on 2007-01-28
Arg! I can't figure out how to get it to work with either. I just wanted to get this set up for school and stuff but apparently I can't. I've pretty much wasted all of today trying to get stuff working and I'm starting to get really frusterated so I guess I'm gunna have to throw Windows back on. Thanks for the help though.

---

### Post by bomanizer on 2007-06-28
Hi,

I recently bought a R50. The laptop didn't come with a wifi card, so I bought a cheap broadcomm mini-pci -card. Of course, the IBM bios didn't accept this card, but I did the no-1802-hack (details here: [http://www.command-tab.com/2006/02/26/unauthorized-wireless-cards/]("http://www.command-tab.com/2006/02/26/unauthorized-wireless-cards/")). Works like a charm. Previously I tested the network manager with a linksys pcmcia-card and it worked ok with ndiswrapper. After installing the mini-pci the network manager connected right away, because I was left with the driver from the first test :)

I'm running Feisty, installed with the alternate-cd.

---

### Post by t4thfavor on 2007-06-28
with an atheros card you will get two interfaces wifi0, and ath0
you will want to use ath0. Atheros cards are among the best supported cards for linux, be thankful you have one.

EDIT: Didn't realize how old this thread was, I doubt he will be back after 5 months.

---

### Post by PhreQuencYViii on 2007-06-29
Lol, didn't know I'd get a response. I still never got it working but might try again with the new Ubuntu.

---

