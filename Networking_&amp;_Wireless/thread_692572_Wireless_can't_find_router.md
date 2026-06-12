---
title: "Wireless can't find router"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by WaddlzInMN on 2008-02-09
Hello,
I have a LinkSys WPC54 v2 wireless adapter. I can ping the device but I can't ping the LinkSys Router which is set up as a DHCP server. I know the router works. I have gone through the user doc's and walked the steps to find where my internet connection is broken (which is how I found how to ping my device, and verify it is set-up and working). But when I:

ping -c 4 192.168.1.1

I get "Destination Host Unreachable".

Any thoughts? I will admit I am not sure if my network is configured correctly in Ubuntu (v7.04). My network is WEP encrypted (hexadecimal), but I have the encryption passphrase entered correctly and the SSID is correct. I don't have anything set up in DNS tab and the General tab just has the default unbuntu Host name.

Upon further review...of the documentation. I came across a suggestion to open up my network. When I removed the WEP encryption, my wireless started working. Now I just to figure out what encryption method WILL work. I can't have my router open to the public, too many freaks out there.

---

