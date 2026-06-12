---
title: "[SOLVED] Wireless not working on it's own - but does with a wired connection?!"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by paulsdavies on 2008-05-29
Hi,

First post, and my first few days with Unbuntu. Through this excellent forum I have got myself up and running with just one problem remaining...

My wireless connection appears to be configured OK, and appears to work when the computer is connected to the wired network interface. But I would like to use just the wireless connection, but when I boot up with no wired connection attached, the wireless connection does not work either.

Some background:

Ubuntu 8.04 Desktop
Edimax 54Mb PCI Wireless Card
Shuttle SN42GV2 PC.

I installed Ubuntu on the base system first, then added the PCI wireless card.

With a wired connection...
Wireless PCI card configured itself out of the box
All looks OK in Network manager - static addresses assigned for both wireless and wired (on same subnet)
I can ping the wireless IP address from this PC and other devices
WiFi Radar application can see mine (and many other) wireless networks
wfconfig all looks OK - no errors
if config looks OK - no errors

If I start up the PC without the wired connection, I can't ping (or anything else) to the wireless connection from any other device.

I tried removing the local route to the wired connection from the routing table (so only the wireless connection was in teh routing table) but no change - have reset it now.

Any ideas people? I have a feeling this is something quite simple - I just can't recognise it!

---

### Post by chili555 on 2008-05-29
I take it this is a desktop machine that you are not going to lug over to the coffee shop, library or university. Is this is correct, why do you need Network Mangler, Wifi Radar, Wicd, et al? I suggest removing every last one of those through Synaptic and simply *sudo gedit /etc/network/interfaces* and make it look like this:```
 auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-essid <ur_essid>
address 192.168.0.42
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
```Of course, substitute your particulars here. 

By commenting out *auto eth0*, it will not try to start automagically, and your wireless interface, eth1, will.

---

### Post by paulsdavies on 2008-06-01
Thanks very much Chilli555 - that sorted it.

You're right - it is a desktop machine - I only installed WiFi Radar as another validation that the wi-fi card was working.

Did as you say, and configured using the interfaces file which properly disabled eth0.

I did have another problem though, which was the wi-fi connection didn't work without the wired connection configured. Everything looked OK but couldn't connect. I eventually solved it by putting the WEP key in hex in the interfaces file instead of ASCII - so that is something for others to watch out for.

Thanks for your help - solved.

---

