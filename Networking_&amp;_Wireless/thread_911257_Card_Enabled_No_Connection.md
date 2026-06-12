---
title: "Card Enabled No Connection"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by acmariner99 on 2008-09-05
Hi all. I managed to get a successful wireless conection a couple of days ago using b43 and ssb, but after downloading the next set of updates (provided the updates had anything to do with it) and rebooting, I can only enable the card and cannot connect. My network settings are correct as far as I know. What suggestions do you have? I am running the 6.24-19 generic kernel and my lspci -nn is below. (I did have a successful connection at one point.)

06:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

---

### Post by knix on 2008-09-05
b43 still has some problems (including lower performance), so I use ndiswrapper. Here's my output ```
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

```


What I did:

install ndiswrapper (synaptic)
download Dell 1390 wireless card drivers (or get from CD)
extract .exe file.
retrieve DRIVER folder
open terminal
cd into DRIVER folder
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
ndiswrapper -l
modprobe -r b44 (ethernet driver)
modprobe -r b43
modprobe -r ssb
moprobe -r ndiwrapper
modprobe ndiswrapper
modprobe b44

b44 uses ssb, that's why you have to unload it. ndiswrapper has to load before ssb, so you have to unload and reload ndiswrapper.

insert the modprobe part in into your /et/rc.local, before the exit 0 line.

---

