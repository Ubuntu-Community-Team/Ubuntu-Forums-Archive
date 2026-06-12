---
title: "Broadcom 4306 not finding wireless AP"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by RedBoot on 2006-08-04
I've loving Dapper installed on my laptop, but I'm having NO luck trying to get my wireless Broadcom 4306 to sense or connect to any wireless signal (they are strong.)
I've studied the 'WifiDocs/WirelessTroubleShootingGuide' and tried forums posts 185841, 197102, and even 195448 (which was for Broadcom 4306.) But no luck. And I'm trying to avoid NDISwrapper; I am hoping to get this working by using the driver that comes built into Dapper.
During install, it detected both the wireless and ethernet NICs, but did not sense a wireless network, even when I input the SSID. So I proceeded to install using the wired card.
It seems that the driver is installed, but it still can't sense any wireless connection. 
I installed Network-Manager-Gnome, but the only thing I see from it is an applet on the Desktop Panel which reports "No network connection."

Any suggestions?

Here are some of the commands I've used and results obtained. 
eth0
IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4306"
Mode: Managed  Access Point: Invalid   Bit Rate=1 Mb/s
RTS thr: off   Fragment thr: off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@edubuntuLT0:/home/redboot# **lshw -C network**  
*-network: 0 DISABLED       
description: Wireless interface       
product: BCM4306 802.11b/g Wireless LAN Controller       
vendor: Broadcom Corporation       
physical id: 2       
bus info: pci@03: 02.0       
logical name: eth0       
version: 03       
serial: 00:90:4b:ec:40:0b       
width: 32 bits       
clock: 33MHz       
capabilities: bus_master ethernet physical wireless       
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-386 
link=no multicast=yes wireless=IEEE 802.11b/g       
resources: iomemory:b0204000-b0205fff irq:177
  

root@edubuntuLT0:/home/redboot# **lspci -v |grep Broad**
0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
root@edubuntuLT0:/home/redboot# lsmod |grep bcm
bcm43xx               124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac

******* Here tried to setup channel; Note I also had assigned ESSID manually.**
root@edubuntuLT0:/home/redboot# **iwconfig eth0 channel 11**

root@edubuntuLT0:/home/redboot# **iwconfig eth0**

eth0      IEEE 802.11b/g  ESSID:"thelab"  Nickname:"Broadcom 4306"          
Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid          
Bit Rate=1 Mb/s          
RTS thr: off   Fragment thr: off          
Encryption key: off          
Link Quality:0  Signal level:0  Noise level:0          
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@edubuntuLT0:/home/redboot# **iwlist eth0 scan**
eth0      Interface doesn't support scanning : No such device

---

### Post by Dave Klinzman on 2006-08-04
I found when I upgraded that there was a conflict with ndiswrapper and the driver that comes with Dapper, bcm43xx.  There is a lot of info regarding this on the Wiki but the bottom line is that if both try to get configured, neither will work - and one of them MUST work to make wireless connections.  I would recommend ndiswrapper using the latest card driver from the mfg.  Hope this helps.  Good Luck!

---

