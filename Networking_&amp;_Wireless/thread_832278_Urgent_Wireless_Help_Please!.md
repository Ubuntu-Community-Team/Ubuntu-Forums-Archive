---
title: "Urgent: Wireless Help Please!"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Xhed on 2008-06-17
hello, i have just recently installed Ubuntu 8.04 on my laptop, everything is working really great so far. The only thing I have been having major problems with is connecting to the internet wirelessly. I have a 01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) wireless card. I have tried everything that seems possible to try to get this to work, I've tried downloading Linux and windows drivers, emulating windows drivers, etc. I've been browsing forums and websites for hours and can not find a solution. So please, if there us anything i can do please help me!
Also, I am fairly new at Ubuntu so use as basic terms and procedures 

Thank You

---

### Post by rlzyoner on 2008-06-17
Have you tried ndiswrapper 
In my experience that is the handiest way to use wireless cards that use restricted windoze drivers.
If you have tried this, please post the output of 

ndiswrapper -l

---

### Post by Xhed on 2008-06-17
Yes, I did try ndiswrapper, or at least I think I did
And I dont know what you mean by post the output :/

thanks

---

### Post by geezerone on 2008-06-17
> **Xhed said:**
> ...And I dont know what you mean by post the output :/

thanks

Open a terminal and type ```
ndiswrapper -l
``` Copy and paste the output on here, mine shows: *net111v2 : driver installed *for example.

---

### Post by Xhed on 2008-06-18
this is what i get
```
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
```

---

### Post by unutbu on 2008-06-18
Please post
```
ndiswrapper -l
```
where the last bit is "minus ell" (the letter l), not "minus one".

---

### Post by Xhed on 2008-06-18
ohhhhh sorry, here it is

```
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
netathwx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

---

### Post by Dizzle7677 on 2008-06-18
I have the same card. Here's how I set it up.

1. Remove Network Manager - Network Manager Gnome with Synaptic

2. Ndiswrapper v1.5.2 is usually installed automatically. If not, install the new one from the ndiswrapper website(v1.5.3)

3.install the associated ndis packages (ndisgtk, ndiswrappercommon,ndiswrapper-utils)

4.Install Wicd network manager [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

5.gedit /etc/modules and add 'ndiswrapper' to the list.
 and 'Modprobe ndiswrapper' in the terminal.
6.used the windows driver @ [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz) 
7.Install the driver sys->admin->windows w drivers

8.if everything went well.go to sys-admin-Network and set the AP,keys,etc for the wireless connection. Watch for the Unlock button stuff.

Make sure it's clicked with a check next to the connection.

9.Go into app-Internet-Wicd and set the prefs and autoconnect in the AP drop down list.
10.add this line before wlan0 to /etc/network/interfaces

'pre-up /sbin/ifconfig wlan0 hw ether [MAC ADDRESS]' Get the mac addy from ifconfig. without the quotes.


Voila!
p.s.-Avahi-ipd I also removed b/c it causes funkiness for me. I have no use for network printers,etc. also deselect the avahi daemon[multicast dns] if possible under Services.

---

### Post by Dizzle7677 on 2008-06-18
> **Xhed said:**
> ohhhhh sorry, here it is

```
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)
netathwx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

Don't use the atheros.cz drivers. Are you running the 64-bt version?

---

### Post by Xhed on 2008-06-18
I'm sorry, but i don't know how to Remove Network Manager and thats the first step so I'm kind of stuck, lol...thanks again
also, im pretty sure i have a 32 bit system

---

### Post by Dizzle7677 on 2008-06-18
System -> Admin-> Synaptic package manager.

---

