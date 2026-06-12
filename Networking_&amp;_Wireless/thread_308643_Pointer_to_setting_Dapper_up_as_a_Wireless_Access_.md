---
title: "Pointer to setting Dapper up as a Wireless Access Point"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by ronald.higgins on 2006-11-28
Ok, so as the topic suggests, i'm looking for a pointer to setting up Dapper as a Wireless AP.

I've got 2 Interfaces on the Box, Wired & Wireless. Wired INT plugs into the cable modem and I'd like to use the Wireless INT as an  AP and eventually route traffic via the Wired INT.

The Wireless INT is a BT Voyader 1040, i believe it's a Broadcom chipset, and as such is not a Prism chipset which is required too run HOSTAP(D).

Can anyone suggest another proggy similar to HOSTAP(D) that might support my Wireless Card's chipset?

regards

ronald

---

### Post by BeachBum on 2006-11-28
I believe hostapd will support any wi-fi hardware that supports master mode, though unfortunately there aren't too many chipsets that are master mode capable.

Try: 
> sudo iwconfig athX mode master
where athX is your wi-fi interface, and see if its a vaild mode.

Otherwise, I've never come accross any other access point software besides hostap.

Instead, you can set up an ad-hoc network (most, if not all, wi-fi hardware supports this), where your "ap" box shares its internet connection with other computers.  I'm trying to get this working myself, but have made little progress as I need to get the card working first... 

I've heard of some users setting up internet connection sharing through Firestarter for a more GUI based apporach;
> sudo apt-get install firestarter 

Or you could use IP tables to set up the routing, look for it on the forums.

It looks easy and is worth a try.

Good luck.

---

### Post by ronald.higgins on 2006-11-28
> **BeachBum said:**
> I believe hostapd will support any wi-fi hardware that supports master mode, though unfortunately there aren't too many chipsets that are master mode capable.

Try: 

where athX is your wi-fi interface, and see if its a vaild mode.

Otherwise, I've never come accross any other access point software besides hostap.

Instead, you can set up an ad-hoc network (most, if not all, wi-fi hardware supports this), where your "ap" box shares its internet connection with other computers.  I'm trying to get this working myself, but have made little progress as I need to get the card working first... 

I've heard of some users setting up internet connection sharing through Firestarter for a more GUI based apporach;
 

Or you could use IP tables to set up the routing, look for it on the forums.

It looks easy and is worth a try.

Good luck.

Thanks for some tips, much appreciated. Installed Dapper as a LAMP box so there is no pretty GUI to install FireStarter ;) .

I am able too connect to the Linux Box via wireless from my laptop in Ad-Hoc Mode but that is pretty much where i got stuck. Once in ad hoc mode i'm not sure how i would go about using the Linux Servers wired INT to gain the connectivity.

I tried setting up DHCP on wlan0 but it doesnt seem too assign an IP when connecting via ad-hoc .

PS. got the network card going with ndiswrapper so wired is eth0 & wireless wlan0

---

