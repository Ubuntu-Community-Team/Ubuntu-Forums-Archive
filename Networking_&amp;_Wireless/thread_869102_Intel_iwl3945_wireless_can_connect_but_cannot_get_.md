---
title: "Intel iwl3945 wireless can connect but cannot get IP"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by tdeprato on 2008-07-24
My ethernet works fine.  My wireless shows it is connected using a WEP key. But I cannot get an IP. I have spent about 2 hours researching this and cannot seem to find anything to work. I did install another Network Manager as well.  

Also, if it is a clue my wireless light is not coming on, but I dont care.:)

Wireless info -----------
id:	
network
description: 	Wireless interface
product: 	PRO/Wireless 3945ABG Network Connection
vendor: 	Intel Corporation
physical id: 	
0
bus info: 	
pci@0000:03:00.0
logical name: 	
wmaster0
version: 	02
serial: 	00:1f:3c:20:b8:e5
width: 	32 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	iwl3945
latency	=	0
module	=	iwl3945
multicast	=	yes
wireless	=	IEEE 802.11g
-------------------------
SYstem Info 
id:	
mylinux
description: 	Notebook
product: 	6465CTO
vendor: 	LENOVO
version: 	ThinkPad T61
serial: 	L3G4697
width: 	32 bits
capabilities: 	smbios-2.4 dmi-2.4 smp-1.4 smp
---------------------

Hardy Heron 8.04
-----------------------------

---

### Post by NilsE on 2008-07-24
This is a tough one to diagnose.  The only time I had a hard time getting an IP address with wireless and wep was when I had the key wrong.  For some reason it got connected to the wireless router but no IP and it did not tell me that by prompting for the wep key or anything.

So, have you verified that the wep key works on Windows or any other platform?

Also, go into a terminal and try
```
sudo dhclient
```
 and see what that reports or if it helps.

Also, make sure the wireless connection in the network manager is on roaming not manual with dhcp selected..

And one more.  Make sure your /etc/network/interfaces file only has the following in it (back it up first just in case)
```
auto lo
iface lo inet loopback

```

---

### Post by tdeprato on 2008-07-25
Using WiCd I was able to connect to an unsecured network. I had to add this to my modprobe 

alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1

In a file called: iwl3945 

But I still cannot connect to a WEP network and get an IP.  I can connect just no IP. 

In someones opinion should I :

1. Reinstall intel drivers 
2. Try NDISwrapper 
3. Forget the newest Ubuntu as this is a problem that many people are having and no one can solve?

I have tried:
1. Changing network managers
2. Starting and restarting network interfaces after boot up
3. removing avahi and turing off multicast dns

Other sysmtoms:
1. In the Administration>>Network> Wireless Ubuntu will not erase the last info I put in. When I enable the wireless and use WICD I can edit the settings but I can no longer simply select ROAMING since removing the gnome network manager.

2. Ethernet works. 

3. Unsecure wireless works

4. Ubuntu constantly says-- Cant resolve Host name 

.......................................

Questions welcome. I would like to solve this for the whole community but there are too many random attempts and no one has been consistent and most solutions do not have follow-ups. 

Again WiFi is a central and key feature in any mobile desktop and it should be a priority.  This was not an issue in my previous Fiesty or Gutsy .....

---

### Post by skankster on 2008-07-25
> 3. Forget the newest Ubuntu as this is a problem that many people are having and no one can solve?

There were some iwl3945 issues. IIRC 2.6.24-20 kernel update checked in a fix to at least one iwl3945 issue - but I may be wrong. It does however introduce some other problems for some users (some people can't boot and some, inc. me, it breaks their wireless - not that that would be an issue for you). You could try upgrading to it? 

To do that enable Hardy-Proposed updates in your Software Sources and check for upgrades. If you have any problems, you can select 2.6.24-19 from the boot menu (Grub) and boot back into that. However, proposed stuff is stuff for testing so be aware of other potential issues. Also, you may want to make sure you know how to roll it back before you try.

---

### Post by Doronkatz on 2009-03-15
Hi guys
Not sure if I should post this under this thread or new one. Basically I am new to ubuntu I have a thinkpad x60 with jaunty installed. I have been using interprid before and my wifi worked fine.  Ad soon as I upgraded to jaunty I can't get my wifi to work. I have iwl3945 intel card. 

Now under normal boot I can't see wifi existing under network icon. When I boot under different module I get wifi signal and it lists all the hotspots but when I select one, whether an open access or wpa it tries to connect but nothig happens after a few seconds. Help guys I have been googling all over.  Thx

---

### Post by cd-r80 on 2009-03-15
I had to move to Intrepid to get my wireless work. But it was different NIC. (& update kernel).

---

### Post by ugm6hr on 2009-03-15
Please keep Jaunty issues in the development section.

Thread closed.

---

