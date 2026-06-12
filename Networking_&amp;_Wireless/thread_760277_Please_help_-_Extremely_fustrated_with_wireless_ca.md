---
title: "Please help - Extremely fustrated with wireless card...Won't Work"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by imari2542 on 2008-04-20
I installed Ubuntu 7.10 a few days ago and thumbs up at the easy mostly flawless install.

I have 1 problem and it is the with D-Link wireless card. It is a D-Link Air DWL-520 Wireless PCI ADapter(rev.E1). 

I've tried reading the help guides, multiple wireless postings on the forum, followed some of the guides and the NDIS wrapper but to no avail.

I am extremely fustrated that I can't get this card to work when others have.

Can someone PLEASE help me?

I typed in:

 lshw -C network

This is what I got:

  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=0.0.0 latency=32 module=hostap_pci multicast=yes wireless=IEEE 802.11-DS
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:da:14:0b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

Apparently it shows my wireless card is disabled???

I typed in iwconfig and here is what I got:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What do I need to do next?

---

### Post by MrFSL on 2008-04-20
When looking for an answer I suggest searching the following:

ubuntuforums.org
help.ubuntu.com
wiki.ubuntu.com

Here are some helpful links:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

And especially:

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)


I'm not complaining... but you will really get answers quicker if you search these resources first. :)

Hope this helps.

---

### Post by imari2542 on 2008-04-20
Actually, I have printed and read those many times but I must not be doing something right.  I will review them again.  

I've also printed out some other things I came across but I'm just not "getting it" 

I especially tried following step-by-step the 
[https://help.ubuntu.com/community/Wi...ice/DWL-520vE1](https://help.ubuntu.com/community/Wi...ice/DWL-520vE1).  I've tried numerous times in between suggestions I've read in other posts.
but when I type in the commands everything goes downhill at step 3 
I just don't understand what I am doing wrong.

I've been working for days on this and I think my brain is just mud now.

Thanks

---

### Post by Bandit60 on 2008-04-20
See what you have in /etc/network/interfaces

It should show your card ID with essid and WEP or WPA

I have a D-Link WDA-2320 PCI with an Atheros chipset. I started off using Ndiwrapper, and it would not work for me. I un-installed it, and tried Network Manager, and it worked fine.

Go to System/Administration/Network and make sure your Wireless connection is there. If not, add it. Select properties and choose Enable Roaming.

You should have the Network Icon in your top bar. If not, right click on it, and select add. Drag Notification area from the utilities section. Right click on it, and make sure Enable Network and Enable Wireless are checked. 

Left click on the icon, which should show signal strength bars, and it will show available networks. You should be able to select yours, and enter the WEP/WPA to connect.

Then go back to Terminal and check ifconfig and iwconfig.

---

### Post by imari2542 on 2008-04-20
Here is a copy of the /etc/network/interfaces


auto lo
iface lo inet loopback




iface ath0 inet manual
wpa-driver madwifi
wpa-roam /etc/network/wpa_supplicant.conf

iface default inet dhcp

It looks like I'm missing the essid.  I'm not sure how to add it but I'll try to figure that out.

I did what you suggested and did actually get the wireless network to appear but it said it connected 0% and there were no orange bars.

I also uninstalled the ndiswrapper which I hadnt thought to do, thanks for letting me know about that.

I'll keep plugging away.....

---

