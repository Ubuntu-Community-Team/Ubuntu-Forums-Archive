---
title: "Problem compiling driver for RTL8723e"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by pmjs1115 on 2014-05-07
Just tried to compile the driver for the RTL8723e on the latest kernal update for 12.04 LTS [I have to do this for each new kernal]. It failed when I did the modprobe.

Attached is the command line output from "make clean" to the "modprobe rtl8723e"

This has worked through many updates. Don't know what to do other than replacing Ubuntu with a newer edition.

Suggestions are welcome.

Paul

---

### Post by pdc on 2014-05-08
not a common issue but here [http://ubuntuforums.org/showthread.php?t=2127626](http://ubuntuforums.org/showthread.php?t=2127626) is mentioned

---

### Post by chili555 on 2014-05-08
> **pdc said:**
> not a common issue but here [http://ubuntuforums.org/showthread.php?t=2127626](http://ubuntuforums.org/showthread.php?t=2127626) is mentionedExactly. See post #6.

---

### Post by pmjs1115 on 2014-05-09
Thanks for the pointers. Before I dive in, can you think of a reason that the latest kernel update should have activated this problem?

---

### Post by chili555 on 2014-05-09
> **pmjs1115 said:**
> Thanks for the pointers. Before I dive in, can you think of a reason that the latest kernel update should have activated this problem?Without more details, I can only speculate. Did you install the backports package? That's one approach to building drivers that's different from compiling from source code. They do not do things quite the same and sometimes conflict. 

If backports is not the issue, then I don't really have enough information to even guess.

---

### Post by pmjs1115 on 2014-05-09
Interesting! I just did a reboot with my Ethernet unplugged, and the wireless came on just like it should. Sort of what the other poster eperienced, except I did nothing after the compiles and failed modprobe. Rebooting just made it work. [I had prefviously booted with the Ethernet connection because I didn't think the wireless was working.]

Thanks for all your help. Maybe this will help some other poor soul.

Paul

---

