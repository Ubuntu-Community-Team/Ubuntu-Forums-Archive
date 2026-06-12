---
title: "WPA on Intel 2200 Wireless, 6.10 Edgy"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Vode on 2007-03-20
Hi, um - first post and all that.
I'm running Ubuntu 6.10 on my laptop and although with the help of the sticky post about security I do have a working network connection I have to run a restart command each time I've started up and also it's identifying my connection as eth1 not "wlan" and this is something that confuses me. Can someone tell me why this is and what I can do to change it if possible for clarity's sake?

I'm running with the wext driver although there is apparently a driver for my intel 2200 wireless bundled with ubuntu, what do I replace wext with in my network interfaces file to use this driver instead? I tried ipw2200 but that failed so I'm back to wext for now.

First post from a first user, I apologise for any stupidity herein.

---

### Post by Vode on 2007-03-21
Any responses to this?

---

### Post by wieman01 on 2007-03-21
See post #2 in the support thread (see my signature). There is a solution/workaround posted.

---

### Post by Vode on 2007-03-21
Thanks, that worked, I tried that initially but I accidentally put rc5.d not rcS.d... Looking at it again I saw my error and used the correct command. Worked perfect, but I don't have permission to delete the incorrectly placed file apparently (in the rc5.d folder).

Any clue about why it's showing up as eth not wlan, is this something I can adjust?

---

### Post by wieman01 on 2007-03-22
> **Vode said:**
> Thanks, that worked, I tried that initially but I accidentally put rc5.d not rcS.d... Looking at it again I saw my error and used the correct command. Worked perfect, but I don't have permission to delete the incorrectly placed file apparently (in the rc5.d folder).

Any clue about why it's showing up as eth not wlan, is this something I can adjust?
You should be able to delete the file using "sudo"... could that be the problem?

As for question number 2, the wireless interface may have different name depending on the hardware you have. My laptop PC's is referred to as "eth1" as well as I am using an Intel chipset. Really depends, don't worry too much about it. :-)

---

