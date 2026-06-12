---
title: "Can't get Wifi to work when any kind of security is enabled on my router... help!"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by onebrokenneck on 2008-05-25
I am new to ubuntu so sorry in advance if this is a newbie problem. I am using a Netgear WG311 v3 wireless card to try to connect to my Linksys WRT54GC wireless router. I used the ndiswrapper to install the Windows XP drivers from the Netgear install CD. ubuntu recognizes the card and the card is picking up my wireless network. When I try to switch from a wired connection to wireless, it prompts me for the security password. I type in the password and it says for a while "Waiting for Network Key for the wireless network 'Linksys'...". It does this for a few minutes while the little swirly black ball logo is spinning away. The little balls change to green. It then switches to my wired connection with no pop-up errors of any kind. I have tried this using WEP, WPA, and WPA2 but all result in the same thing. No wireless connection. I did a test of turning off my wireless security completely and the card connected to the network on the first try. Someone please tell me what I am doing wrong. I saw in some other posts people listing the settings below so I included those if they are a help to anyone. Thanks in advance to anyone that can help!

 *-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:32:72:b5
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.52+NETGEAR,02/22/2005,3.1.1.7 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:7e:05:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.103 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s

---

### Post by onebrokenneck on 2008-05-26
Someone here must be able to give me some kind of insight on how to fix this problem...

---

### Post by Janus23 on 2008-08-08
I am having the same problem with a Netgear router.  The wireless connection worked fine for a few days after an upgrade to Hardy on my Dell Inspiron 1420n, and configuring after the upgrade wpasupplicant, etc.  After a few days, however, the connection wouldn't establish without manually configuring the network, and then manually connecting.  Now the connection won't establish at all using security.  I disabled WAP personal (TKIP) and MAC filtering, and the connection works fine. Can anyone help?

---

### Post by graysky on 2008-08-08
See if [this post](http://knoppmyth.net/phpBB2/viewtopic.php?t=18719&highlight=) or any of the references can help you.  BTW, I that card uses RT61 so no need for niswrapper as all.

---

### Post by swisscow on 2008-08-08
Again, don't know if this would help but you could install wicd and use that instead of network manager.

I was having wireless network drop offs for no reason. Changed a week ago, all fine since.

Beware, installing wicd will remove network manager, but as you have a working wired connection that shouldn't matter for you.

---

