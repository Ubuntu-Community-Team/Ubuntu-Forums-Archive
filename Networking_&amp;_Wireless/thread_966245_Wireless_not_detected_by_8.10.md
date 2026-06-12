---
title: "Wireless not detected by 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by gewitty on 2008-11-01
I downloaded 8.10 yesterday and tried the live disk on a couple of machines (a desktop and an Asus eee laptop). Whilst it loaded OK on both, my wireless network is not detected automatically, as it has been in all previous versions of Ubuntu. In tried to manually configure the connections, but still got no joy. Is there something significantly different about the way 8.10 handles wireless?

---

### Post by carstanje on 2008-11-01
Same here! Did an update from hardy. It seems the Networkmanager has changed, everything looks different. Scanning wifi networks doesn't work anymore. Doesn't work for me both on ubunta as kubuntu. Weird!

Can anyone help? Am I missing some packages?

---

### Post by Hyper Tails on 2008-11-01
What is your wireless network adaptors?

you seem to lack info on your card

---

### Post by carstanje on 2008-11-01
lspci tells me this:
3:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

Is this what you ment?

Before the upgrade to 8.10 Intrepid my wireless was working fine, including detecting all the available wifi networks

---

### Post by virtix on 2008-11-01
Same problem here: w/Broadcom BCM4328. I tried Network Manager, wicd, and manual. 

Could it be possible that the upgrade to 8.10 hosed the ndiswrapper work I did for 8.4?

-bill

******************************************

~$ lspci
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Hewlett-Packard Company Device 1366
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
	Memory at f2000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-0d-ff-ff-00-b6-e6
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb
	
	
	
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:48:a5:c2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:21:00:0d:e6:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:8f:9a:2a:4f:5f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes  
billy@mxunit-ubuntu:~$ 

	
	
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.


******************************************

---

### Post by Ayuthia on 2008-11-01
> **virtix said:**
> Same problem here: w/Broadcom BCM4328. I tried Network Manager, wicd, and manual. 

Could it be possible that the upgrade to 8.10 hosed the ndiswrapper work I did for 8.4?

-bill

******************************************

~$ lspci
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Hewlett-Packard Company Device 1366
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
	Memory at f2000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-0d-ff-ff-00-b6-e6
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb
	
	
	
~$ lshw -C network
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:21:00:0d:e6:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11


If you compiled ndiswrapper manually, you will need to recompile ndiswrapper to make it work.  This is because the kernel version changed.  The other additional change that you would need is to blacklist the wl driver.  It is a new driver (Broadcom STA-wl driver) introduced to Intrepid that might work with your card.  To blacklist it, you will need to do the following:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

@gewitty- This will not fix your problem.  You have a different card.  Unfortunately, I do not have any experience with it.  Sorry.  There are several others out here that have that card so hopefully they can provide some advice.

---

### Post by virtix on 2008-11-01
Ayuthia,

Thanks! The backlist worked. That and a restart did the trick.


bill

---

### Post by gewitty on 2008-11-02
Just spotted this post on another forum. It refers specifically to the problem as it affects the Asus, but may be a clue as to where the source of the issue lies. I'm not sufficiently expert to understand if all the reported failures are down to a kernel problem, but maybe someone with better knowledge might comment.

This issue does seem to be getting reported quite widely now, but so far I have not come across any 'official' comment or suggestions about how to fix it. 

[http://tinyurl.com/6dyzym](http://tinyurl.com/6dyzym)

---

### Post by paul_v on 2008-11-04
I'm getting the same problem here when I upgraded a previously wifi working Dell Lattitude laptop. The weird thing though is that I can detect and connect to other wifi points and indeed, it's still detecting 5 wifi SSIDs within range of here - just not my own one, which strikes me as a bit weird.

Is it perhaps a problem with the new kernel and the encryption algorithm. My router is using WPA2 AES encryption, whereas the others appear to be using WPA1 TKIP encryption. However, it was working on this wifi with 8.04

---

### Post by StefkeDB on 2008-11-04
Upgraded from 8.04 to 8.10.  Normally I see 5 networks. With 8.10 only 1, and my own is not there.  Only after clicking on 'Connect to Hidden Networks' I can select my own.  When connected to my own network he suddenly 'sees' the other available networks.  I would like my pc to connect without me having to make any action.

---

### Post by kjaggu on 2008-11-05
Same problem here. 

I am not so knowleagable about network connections. I cannot connect to any wifi networks while all other connections are working fine. 

I have a Compaq Presario C733TU laptop. If need be, please advise me on how to identify the wireless network card for my system. 

Warm regards,
Jagadeesh

---

### Post by carstanje on 2008-11-06
> **gewitty said:**
> Just spotted this post on another forum. It refers specifically to the problem as it affects the Asus, but may be a clue as to where the source of the issue lies. I'm not sufficiently expert to understand if all the reported failures are down to a kernel problem, but maybe someone with better knowledge might comment.

This issue does seem to be getting reported quite widely now, but so far I have not come across any 'official' comment or suggestions about how to fix it. 

[http://tinyurl.com/6dyzym](http://tinyurl.com/6dyzym)

Gewitty: The wireless card in the problem mentioned is an atheros, not an Intel as we discuss here. The fix described in that post won't solve your problem.

---

### Post by carstanje on 2008-11-06
> **kjaggu said:**
> Same problem here. 

I am not so knowleagable about network connections. I cannot connect to any wifi networks while all other connections are working fine. 

I have a Compaq Presario C733TU laptop. If need be, please advise me on how to identify the wireless network card for my system. 

Warm regards,
Jagadeesh

1. Open a terminal
2. Type lspci
Every line shown is a piece of hardware on your pc. One of these lines should contain something with wireless or wifi. This line is your wireless network card. You will see a vendor and a product type. If you can't figure it out, copy & past your lspci output here.

---

### Post by Hyper Tails on 2008-11-06
looks like you could use ndiswrapper

here the 64-bit driver:
[http://blakecmartin.googlepages.com/...-64-0.2.tar.gz](http://blakecmartin.googlepages.com/...-64-0.2.tar.gz)

heres the 32-bit driver:
[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

to install ndiswrapper:
```
sudo apt-get install ndisgtk
```

exact the folder and open the inf file in it

Sorry I don't have time now because I got classes

---

