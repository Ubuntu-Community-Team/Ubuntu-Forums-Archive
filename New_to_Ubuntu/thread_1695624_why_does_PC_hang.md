---
title: "why does PC hang?"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by granmed on 2011-02-26
My PC has dual operating systems, Windows XP and Ubuntu-10.10. 
 
In both of them the PC hangs within 10-15 minutes even if I do not put 
any memory intensive job. What could be the reason(s)? 
 
Thanks.

---

### Post by cascade9 on 2011-02-26
Overheating, power supply issues, bad RAM, bad drivers, random hardware breakage....take your pick.

---

### Post by EpiLePTiC FaiRY on 2011-02-26
Do you have any hardware monitoring tools to check temperatures? You should run a memtest (it'll be on your installation CDROM) and see if it dies doing that. I would definitely borrow a PSU for test purposes if it's a desktop if the above comes up peachy.

---

### Post by granmed on 2011-03-02
> **EpiLePTiC FaiRY said:**
> Do you have any hardware monitoring tools to check temperatures? You should run a memtest (it'll be on your installation CDROM) and see if it dies doing that. I would definitely borrow a PSU for test purposes if it's a desktop if the above comes up peachy.


Thanks for your reply.
I did memory testing. It passed with no errors. 
However, in Windows using "PC helth advisor"
software, I found several suggestions, like registry 
clean up, disk defragmentation, remove temporary files,
driver updates, etc. But the software is not free.

---

### Post by granmed on 2011-03-02
> **cascade9 said:**
> Overheating, power supply issues, bad RAM, bad drivers, random hardware breakage....take your pick.

Thanks for your reply.
I did memory testing. It passed with no errors. 
However, in Windows using "PC helth advisor"
software, I found several suggestions, like registry 
clean up, disk defragmentation, remove temporary files,
driver updates, etc. But the software is not free.

---

### Post by cascade9 on 2011-03-02
If you are getting the same problem with windows and a linux distro, the its not software, its hardware.

---

### Post by mastablasta on 2011-03-02
> **granmed said:**
> Thanks for your reply.
I did memory testing. It passed with no errors. 
.
 
 
hello, i suggest you open up the box and see if any device has bulged capacitors (check motherboard and graphcis card):
[http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)
 
they should be flat on top.
 
next thing to do is to see the temperature. you can use SpeedFan software in windows to do that. 
 
If any component is overheating you can first try to clean the heatsink with vacuum cleaner as well as fans (if you use laptop blow some compressed air in it or use vacouum cleaner set not too high).
 
hope this helps. this is definatelly ahardware issue but it's hard to say what it is without actually opening it up.

---

