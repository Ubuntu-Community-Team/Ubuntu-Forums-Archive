---
title: "Finally got unsecured wireless to work, sheesh"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by xml2k on 2007-01-02
Here's what I have:
Dell Inspiron 5100
UBUNTU Edgy
Motorola WN825G Wireless Card. Broadcom Chipset 4306, rev 3

What Did Not Work:
Kernel Driver bcm43xx
Network Manager
I could only connect to my secure WPA2 Personal Access Point (AP) using this combination and never to an unsecure AP such as are present in Cafe's and Libraries. Network Manager seemed to only want to connect to a secure network.

What Did Work:
Latest ndiswrapper 1.33
No Network Manager
bcmwl5a.inf
Following community doc "WifiDocs/Device/Broadcom 4311 rev 01 (ndiswrapper)"
I ended up using bcmwl5a.inf after noticing after loading both bcmw15.inf and bcmwl5a.inf that only the bcmwl5a.inf gave additional device information -
bcmwl5a : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

I used the device (14E4:4320) to determine which .conf file to copy in step 5

I use Wifi Radar only to only see what AP's are available, then I use the standard network tool in menu System/Administration/Networking to change the ESSID to one at the free wifi site, where I am now typing this posting.


Cheers, I hope this helps

---

### Post by davetrainer on 2007-01-05
I think I have the same problem and I've been stuck for 2 days. I see my SSID in wifi-radar, but it just says connected - ip (none). In the regular network manager, I can enter my SSID but can't get an IP. I have to open a terminal and sudo ifdown eth1, sudo ifup eth1 if I ever want to get an ip, after I enter the SSID. This is wickedly frustrating. Why can't I hit connect in wifi-radar and just get DHCP???    ](*,)

---

### Post by kerry_s on 2007-01-05
Ya, wireless in ubuntu sucks. I had to switch my laptop to pclinuxos(minime) and now don't have to do nothing to set it up, i just plug it in & done. Selecting my network & entering my wep was also a cinch. I like ubuntu but i'll go with simplicty.

---

