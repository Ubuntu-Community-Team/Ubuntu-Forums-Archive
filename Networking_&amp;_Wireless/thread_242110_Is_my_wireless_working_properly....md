---
title: "Is my wireless working properly...?"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by patleamon on 2006-08-23
I have a usb wireless dongle based on the zydas 1211b chipset (safecom 5400).  Found good instructions in the ubuntu help wiki and seems to work... sometimes.  Mostly it works but sometimes it takes ages to do anything or my network seems to dropout.  I figure this might be a poor signal, but I'm not really sure how to tell.  I tried installing network-manager-gnome but it doesn't seem to pickup my wireless connection.

iwconfig tells me that my link quality is usually around the 70-80 mark and the signal level is between 35-45.  Is this reasonable/marginal/bad/terrible?  

I seem to get a really high count in the "Tx excessive retries" field too.    After being on for a while it's not uncommon for it to be in the 10's to 100's of thousands.  Is this normal or is something going wrong?

---

### Post by wieman01 on 2006-08-23
You may have to disable "IPV6". Have had the same problem before but was finally able to resolve it after disabling the mentioned:

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+disable]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+disable")

---

