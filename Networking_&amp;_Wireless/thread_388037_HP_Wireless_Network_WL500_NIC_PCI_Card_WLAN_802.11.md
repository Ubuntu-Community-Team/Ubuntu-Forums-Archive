---
title: "HP Wireless Network WL500 NIC PCI Card WLAN 802.11a/b/g"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by anafshalom on 2007-03-19
I have a 	HP Wireless Network WL500 NIC PCI Card WLAN 802.11a/b/g.
It appears in the Network window, and the lights are blinking, but I'm not connecting.

I think I'm using the latest version on Ubuntu.

Can I connect with this NIC card?

Reuven

---

### Post by teaker1s on 2007-03-19
```
gksudo synaptic
```
try installing "network-manager-gnome" and in System>Administration>Networking devices must be unconfigured.
remove ethernel cable 
reboot and look next to volume icon on top panel
click and see if you can see wireless networks

if you can't 
```
iwconfig
``` post output

---

### Post by anafshalom on 2007-03-21
> **teaker1s said:**
> ```
gksudo synaptic
```
try installing "network-manager-gnome" and in System>Administration>Networking devices must be unconfigured.
remove ethernel cable 
reboot and look next to volume icon on top panel
click and see if you can see wireless networks

if you can't 
```
iwconfig
``` post output
Can I solve this problem with no internet connection?

---

### Post by teaker1s on 2007-03-21
possibly, we need output of this command in terminal
```
iwconfig
``` post on this thread and I can tell you if your card is on

---

### Post by anafshalom on 2007-06-22
I'm reviving this old thread, because I'm having network problems again.  I tried to upgrade to Edgy with disastrous results.  I've just done a fresh install from live CD and now I can't get the wireless to work.

I've installed network manager-gnome and tried booting with Ethernet cable disconnected, and got no wireless connections.
here's the output from iwconfig:

damita@Damita-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"Damita-Ubuntu"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: Not-Associated   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=27/94  Signal level=-68 dBm  Noise level=-95 dBm
          Rx invalid nwid:1941  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Note in this location I don't have my own wireless connection, but there are several in the building to which I may not have access, but should they still not show up somewhere?

---

