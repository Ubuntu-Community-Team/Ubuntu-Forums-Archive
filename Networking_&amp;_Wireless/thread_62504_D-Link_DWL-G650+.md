---
title: "D-Link DWL-G650+"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by garretg on 2005-09-04
Hi Sorry for making a post like this, i know there are a lot of info regarding this Wireless card but Im so confused I really cant figure what do to do.

I already check a lot of info and I cant really figure out what to do.

I noticed that Ubuntu was able to detect my card correctly.  But I cant it to look for my  DHCP server.  I configure it first using the System > Administration > Networking tool (it detects my access point correctly)  I tried several formats for the wep key, including plain text (in ordinary and xxxx-xxxx-xx format) hex (both ordinary and xxxx-xxxx-xx format).  but it cant seem to get ip address so when i ping google.com i can really can anything working...

I also tried using ndiswrapper but for some reason the same thing happens.

This is so frustrating.  I was able to get this thing working under FreeBSD 6 BETA3 but I want it to work in ubuntu.

Please help! or atleast point me in the right direction.

---

### Post by tehwa on 2005-09-05
Are you able to get an IP from the router when WEP is disabled on both ends?

---

### Post by celluloid on 2005-09-05
[QUOTE=tehwa]Are you able to get an IP from the router when WEP is disabled on both ends?[/QUOTE]
 All that was needed for my card to be detected was the ESSID

---

### Post by tehwa on 2005-09-05
Can you post the contents of ```
/etc/network/interfaces
``` and some examples of the WEP keys you tried.

---

