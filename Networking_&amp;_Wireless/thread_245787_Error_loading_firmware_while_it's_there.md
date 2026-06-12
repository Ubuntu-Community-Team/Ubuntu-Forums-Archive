---
title: "Error loading firmware while it's there"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by Vinze on 2006-08-28
Hey, somehow I removed the firmware for my network card before, I put it back but it still doesn't work. 
If, during boot time, I press CTRL+ALT+F1 I see a firmware helper error message saying the was an error loading tiacx100c11, but it is present in /lib/firmware/`uname -r`/acx/1.9.8.b/ and there are links to it in /lib/firmware/`uname -r`/acx/default/ . Strangely, I see no error messages about the other firmware in those folders. What can be the problem?

**Edit:** Apparently it's not there, but according to [this post](http://sourceforge.net/mailarchive/message.php?msg_id=13859088) > tiacx100c11 or tiacx100 and tiacx100r11 would be acceptable.  The c
 stands for combined, while the other 2 are just the split out portions
 of the firmware.

I have those, but apparently Ubuntu does not think they are acceptable. What should I do now?

---

