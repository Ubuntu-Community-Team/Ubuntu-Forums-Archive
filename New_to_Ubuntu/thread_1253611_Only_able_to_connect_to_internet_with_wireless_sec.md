---
title: "Only able to connect to internet with wireless security turned off"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by hnarwan on 2009-08-30
Hi All,

I'm running Jaunty on my laptop. The problem i'm having is when i try to connect to the internet via my wireless Belkin router i'm only able to connect when i disable wireless security.

When it's enabled, even when i supply the correct password the connection isnt made - I've also tried to manually create the connection and supply a wireless password - nothing seems to help.

thanks
Hardeep

---

### Post by keplerspeed on 2009-08-31
What sort of security? WPA, WPA2 or WEP? Is the SSID set to broadcast?

Also what is your wireless card in your laptop/driver its using?

---

### Post by hnarwan on 2009-08-31
Hi, 

It's WPA2, the SSID is broadcasting - the connections icon in the panel shows it up. If i put in my password manually (when it asks for it) or if i create a connection and specify it there the same thing happens...

---

### Post by matthewbpt on 2009-08-31
What wireless card do you have? If you dont know paste the output of 'sudo lshw -C Network'.

---

### Post by hnarwan on 2009-08-31
Hi, 

Below is the output:

  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:b1:08:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:e1:d9:a9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.3 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:1d:12:61:eb:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I'm not sure why it only works when i have security disabled on my router.

I cant access the internet when i have a cable plugged in either, not sure what to do now.

thanks
Hardeep

---

### Post by hnarwan on 2009-09-17
Hi Guys, 

Any ideas about this? 

I have no clue why this isnt working, as i say i'm not able to connect via my wireless connection or a wired connection UNLESS i disable security on the router.

thanks
Hardeep

---

### Post by HarrisonNapper on 2009-09-17
Consider leaving your wireless security (pwd part) off, but enable MAC address filtering and put in your MAC address so that only your computer can connect (you can also add other MAC addresses). This will boost your security as well as allow it to connect (hopefully)

---

### Post by hnarwan on 2009-09-17
thanks for that suggestion, how do i get my mac address on this ubuntu machine?

---

### Post by LewRockwell on 2009-09-17
some routers will report the mac addresses of the wireless devices attached to them

you'll need to consult your documentation and/or check out your router's different interface input screens and settings

.

---

### Post by LewRockwell on 2009-09-17
> **hnarwan said:**
> thanks for that suggestion, how do i get my mac address on this ubuntu machine?

actually it is going to be the mac address of your wireless card/device```
description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:04:00.0
logical name: wmaster0
version: 01
serial: 00:23:4d:e1:d9:a9
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k ip=192.168.2.3 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```looks like it might be **00:23:4d:e1:d9:a9**

.

---

### Post by LowSky on 2009-09-17
reboot the router, reset up the wireless protection you want to use and see if that works, it has for me in the past.

---

### Post by LewRockwell on 2009-09-17
still, you should be able to also utilize your router's security features

once you become more familiar with all the various router controls and settings you'll probably figure it out

in the meantime the mac address should keep others out

(you've changed the default username, machine name, SSID identifier, and password...haven't you!?!)

.

---

### Post by LewRockwell on 2009-09-17
> **LowSky said:**
> reboot the router, reset up the wireless protection you want to use and see if that works, it has for me in the past.

sorry, made the assumption that had already been attempted, but had not solved the trouble-call

.

---

### Post by hnarwan on 2009-09-17
thanks fellas - that's done it. I can now connect after adding my laptop's mac address to my router, no other wireless devices can cannot which is what i wanted.

I'm still a little confused as to why i couldnt get WPA security working. I tried on another router next door (which i know the password to) but again that didnt work. So it looks like unless i get this working i can only use this laptop at home, no point taking it hotels etc unless i'm going to ask them to add my MAC address to thier router!

---

### Post by achase79 on 2009-09-17
I had this problem with Jaunty that I had a passcode set up but i had to put in the hex string for the passcode.

---

### Post by HarrisonNapper on 2009-09-18
Make sure to download network manager, also. That should at least help for when you visit hotels and things like that. My network monitor (as opposed to manager) doesn't work at all for my wireless card.

```

sudo apt-get install network-manager

```

That will add an applet to your notification area on the taskbar and help in detecting available networks in roaming mode. Which reminds me; might want to make sure roaming mode is enabled on your network monitor (again, as opposed to manager).

---

### Post by philinux on 2009-09-18
I'm using wicd which I find much better than network-manager for wireless.

---

