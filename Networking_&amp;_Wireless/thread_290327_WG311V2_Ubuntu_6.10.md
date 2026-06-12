---
title: "WG311V2 Ubuntu 6.10"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Dansaycool on 2006-11-01
Hi, i've just installed Edgy Eft and now i'm trying to get my Netgear WG311V2  wireless card working too, in dapper drake I got it working but since the new install I cant seem to remember how I did it.
I'm really not sure where to begin?

please help 
thanks dan

I just checked the sys log and found this:

Nov  2 09:42:10 Server1 kernel: [42949391.290000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Nov  2 09:42:10 Server1 kernel: [42949391.300000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
Nov  2 09:42:10 Server1 kernel: [42949391.300000] acx: reset_dev() FAILED

I found this website that might be of some help but not sure really

[http://sourceforge.net/forum/forum.php?thread_id=1451461&forum_id=257272](http://sourceforge.net/forum/forum.php?thread_id=1451461&forum_id=257272)

thanks again 
dan

---

### Post by sidiasus on 2006-11-06
It sounds like Ubuntu doesn't have the firmware files for upload.
try this...
[http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)
The ones you want are listed under "For ACX111 there are..."
grab one of those and copy into /lib/firmware/(your kernel version)/acx/default/
Be sure to rename the file to tiacx111c16

Let me know how that works for you.

---

### Post by Dansaycool on 2006-11-08
thanks dude a million, copied the file and then restarted the computer. The little blinking light flicked on for the 1st time in months and you should have seen the smile on my face, ubuntu recognises it is the networking section too. How come stupid little things like this arn't checked and corrected before release? It would take like 10 seconds to fix right?

Thanks anyway 
dan

---

### Post by andrea.tagliasacchi on 2006-12-24
Thanks man. 

I cross-installed kubuntu on my daddy machine and i had the same problem.
With cross installation i mean installing on the 2.5" hard disk using my laptop ( Acer TM803Lci) and then moving the HD to my daddy's ( Acer Asprire 1300).

When i plugged in my wireless card nothing happened, just a similar error in dmesg.
With your correction i am now able to update the system through wireless directly from my daddy's. 


Thanks again.

---

