---
title: "Wireless card dissapears from Kinfocenter"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by fragility14 on 2007-09-21
Ok, so I have had an ongoing network problem for a while now. What happens is my network center continues to show my wireless connection, but the internet stops working. When I try to reconnect I cannot get past 27% (configuring network device). Generally, I have to reset both my computer and my router a random number of times in varying orders and it will start working again. However, today is different, and it will not do any such things.

Sometimes sudo ifdown -v wlan0/sudo ifup -v wlan0 will make it start working again, but generally it connects once briefly then is disconnected again.

What I have noticed today, is that if I go to kinfocenter the only things there are eth0-avahi and lo.

if I type in the ifdown/ifup commands it shows on the list of network interfaces, (if I put in just ifup it says it is already configured) but then when I try to actually connect it stalls at 27% and dissapears from the kinfocenter list and won't be there again until another ifdown/ifup cycle. If I type in ifconfig wlan0 always shows up.

I am wondering if it has to do with inet6 settings, being as that is what it says under wlan on ifconfig, and if I type in dmesg it repeatedly says wlan cannot find ipv6 routers or whatever it is called.

I am using a marvell libertas wireless card, but being as it was previously working, and when I type in ndiswrapper -l (I think is the command) it shows the driver as being there and installed.

I have no other ideas and this is driving me nuts, what is weird is it had just gone for a few days without any problems. 

Please get back to me with any help...

btw does anyone have a command to reset my wireless cards settings to default?

---

### Post by fragility14 on 2007-09-21
let me explain this in a more concise manner:

- my marvell libertas wireless card is installed and was working
- it can see networks as it normally could
- it cannot get past the "Configuring Device" (28%) part of the connecting process
-in KInfoCenter Network Devices it does not show wlan0, however, if I put in the command sudo ifdown wlan0 then sudo ifup wlan0 it will show wlan0, however, it disappears from the list when I try to connect to a wireless network.

I was having a problem where it would do this same thing and either the router or computer needed to be reset an indeterminate amount of times. Today it would not start working again, no changes were made previous to when the internet stopped working this morning. Somewhat regularly the internet will stop working but the wireless network will still show itself as being connected, however, it will not be able to reconnect without resetting either the computer or the router (resetting xorg does not do the trick)

I messed with some various things that maybe I should not have in trying to get this to work, but it doesn't appear that I have actually changed anything, however I am interested in a command which would return my wireless card to default settings (because as soon as I succesfully installed the wireless card it worked and did not need any settings changed)


here is the information my computer gives me about the wireless card


>  -network
description: Wireless interface
Product: 88W8310 and 88W8000G [Libertas] 802.11g Client Chipset
Vendor: Marvell Technology Group LTD
Physical ID: 7
Bus info: PCI@00:07.0
logical name: wlan0
version: 07
serial 00:11:d8:b7:70:93
width: 32 bits
clock: 66 mhz
capabilities: bus=master, cap list, ethernet physical wireless
Configuration: broadcast=yes driver=ndiswrapper driverversion= 1.38 firmware=marvell,11/16/2004 2.7.1.2
latency=32 link=yes multicast=yes wireless=IEEE 802.11g 


and I am also able to find out all of the information relating to the wireless network that I am unable to connect to.



I am convinced this is more than anything a problem of the wireless card disappearing from the devices list when I try to connect...very bizarre behavior...

---

