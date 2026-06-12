---
title: "[SOLVED] Yet another &amp;quot;My wireless card doesn't work&amp;quot; topic"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by thevictor390 on 2007-08-17
I have an old desktop computer with no internet connection other than wireless with a fresh install of Ubuntu on it.  The card is a Belkin F5D7000, listed as ra0: in the network utility and as ralink in the wiki on compatible cards.

The device is working enough that I can tell it the ESSID (different from the SSID?) and WEP password of the network (it's open), but no programs can access the internet.  I'm totally stuck; the iBooks I've installed Ubuntu on did not have any problem with their airport cards, so I have no experience troubleshooting wireless.  Any help would be appreciated, as this is the only way I can get that computer online right now (besides booting into Windows of course, which does work with the card).  I have the original driver CD if that helps, and please keep in mind that I'm new to Linux... something which I'm trying to fix.

---

### Post by dmizer on 2007-08-18
do you get an ip address?

can you ping by url or ip address?

---

### Post by thevictor390 on 2007-08-18
How would I check? Is it something like ipconfig on Windows?  Sorry but I'm completely new to this.

---

### Post by dmizer on 2007-08-18
no problem.  to check for an ip address, use this command:
ifconfig

if you get an ip address, try pinging google:
ping [www.google.com](www.google.com)

if that doesn't work, try pinging google by ip address:
ping 208.67.216.230

---

### Post by thevictor390 on 2007-08-19
Wow.   Apparently the "ESSID" is different from SSID.  I took a look at my iBook with working wifi and saw that it just had "any" under ESSID.  I tried that, and voila! Everything works! I hate it when it turns out to be some stupid assumption I made.  So what is ESSID anyway? I think I'm set right now to just use any network available, which is fine, since theres only one it will pick up.

---

