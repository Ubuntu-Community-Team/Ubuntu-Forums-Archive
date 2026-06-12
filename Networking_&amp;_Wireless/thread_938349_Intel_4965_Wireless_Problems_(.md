---
title: "Intel 4965 Wireless Problems :("
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by PhoenixMaster00 on 2008-10-04
After it not seeming to show up aat all in the Network controls even though drivers were installed when lshw -C Network was put through the terminal i decided to see if Intrepid would do any better and it does... Slightly it still doesnt work :( some information for you potential helpers out there

*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:21:21:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

it says its called wmaster0 but according to Network tools that is an unknown interface. Any help would be greatly appreciated

---

### Post by PhoenixMaster00 on 2008-10-04
anyone?

---

### Post by kforum on 2008-10-05
something is broken, it should be called wlan0, wmaster0 is more of a placeholder(in a sense)...
so im not really sure what you did.
can you describe what happened? as in, you installed the distro, fresh boot, then... etc...

i have the iwl4965, never had any problem with it, specially sine 'the amazing' version 8.04.
but maybe i can help you.

also, it would be nice to know what kinda settings your router is using atm.

cheers. ^^;

edit: can you type iwconfig, and show me the output?

---

### Post by PhoenixMaster00 on 2008-10-05
yeah i put the wireless card in myself so i may have connected it up wrong? if that is possible. 

iwconfig shows

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

im hoping i have just connected it wrong but any direction/help is greatly appreciated.

edit: and i have a zoom router that connects perfectly to an ipod touch, xbox360, mac mini, and two other laptops.

---

### Post by PhoenixMaster00 on 2008-10-05
bump

---

### Post by kforum on 2008-10-05
> **kforum said:**
> 
can you describe what happened? as in, you installed the distro, fresh boot, then... etc...



im going to quote myself, this info really is needed  to know if you screwed something up or if its a ubuntu-sort-of issue.

also, hardware info... so this is a laptop, or what?
you said you connected it yourself, as in... a desktop with pci and you plugged it in?

info-info-info.

things are usually simple in ubuntu, i believe first timer's uneasiness is usually what gets in the way.


cheers;
:guitar:

---

### Post by PhoenixMaster00 on 2008-10-05
> **kforum said:**
> im going to quote myself, this info really is needed  to know if you screwed something up or if its a ubuntu-sort-of issue.

also, hardware info... so this is a laptop, or what?
you said you connected it yourself, as in... a desktop with pci and you plugged it in?

info-info-info.

things are usually simple in ubuntu, i believe first timer's uneasiness is usually what gets in the way.


cheers;
:guitar:


Sorry yeah im new to Linux. Its a laptop the original wifi card has no linux support so i bought a new one. its PCI-E with 3 connectors and 3 wires although the original PCI-E had 2 connectors and a spare wire was kind of hanging around

As for how i got Ubunutu 8.10 i did a fresh install 7.10 then updated and upgraded to 8.04 then upgraded again to 8.10

---

### Post by PhoenixMaster00 on 2008-10-05
bump

---

