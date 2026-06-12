---
title: "Can only ping IP addresses, not website names"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by mccoy2 on 2014-12-13
I thought I was unable to connect to the internet, even though my wireless status shows it is connected. After Googling (on another device) I have done some tests that I found on some forum threads on this site and found the following:
ping [www.google.com](www.google.com) -c 5
Ping: unknown host [www.google.com](www.google.com)

But when I ping this address, it gets to the site:
ping 173.194.42.244 -c 5
64 bytes from 173.194.42.244: icmp-seq=1 ttl=51 time=984 ms

Also, when I open a browser and type [www.google.com](www.google.com) it says "This web page is not available" (Google Chrome)
But when I type 173.194.42.244 in the address bar, Google opens.

I am very new to lubuntu and don't know how to configure it, so please give me detailed steps. I have had lubuntu on this notebook for about 6 months and internet was working fine and stopped working about a week ago. I cannot recall anything changing or any significant (or any other) changes to the notebook, except copying a lot of backup files to it from a usb drive. No settings or software changed to my knowledge.

Your assistance will be greatly appreciated.

---

### Post by schragge on 2014-12-13
It clearly looks like a DNS (Domain Name System)  problem. See [uhelp]community/NetworkManager[/uhelp].

Start nm-applet (It looks like two arrows &#8645; in the systray area). Click on *Information*. Notice the IPs in *Primary DNS:* and *Secondary DNS:*. Close. Click on nm-applet again. Click on *Edit*,  select your connection, click on *Edit* again, select the tab *IPv4 Settings*. Enter 8.8.8.8 into the field *Additional DNS servers*. Save. Click on nm-applet icon again. Click on *Information* again. Check that 8.8.8.8 appeared as one of DNS servers.

This will add [Google Public DNS server]("http://en.wikipedia.org/wiki/Google_Public_DNS") as a temporary workaround. You will still need to investigate what caused the name resolution stop working on your system.

---

### Post by mccoy2 on 2014-12-13
I can't find the nm-applet (the two arrows you mention) in the systray area. 

IPv4 settings was set to Automatic (DHCP).

I have changed the additional DNS servers and saved. I can still not open [www.google.com]("http://www.google.com"). 

Edited to add: Wait, it started working after I rebooted the PC. Thanks so much!

---

