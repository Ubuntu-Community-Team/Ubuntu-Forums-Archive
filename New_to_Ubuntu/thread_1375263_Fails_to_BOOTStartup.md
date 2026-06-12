---
title: "Fails to BOOT/Startup"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Kastrale on 2010-01-07
This afternoon, I had an issue with starting up the laptop.
 I'm running Ubuntu on a Toshiba Satellite A300. No signs of hard drive failure, no signs of exact physical damage to the hardware. It's been running fine so far, and I haven't had any problems until this.
 
 When the incident happened I had shutdown the session, and rebooted after a couple minutes. Pressing the power button led to no response. The power light and satellite light came on, but I got no response from the monitor, no display, and no response on touchpad and keyboard clicks. Didn't see GRUB load.
 
 I had to plug it back into the wall and connect an external monitor before the laptop responded and loaded GRUB. Worked fine, but no records of errors. Or at least I dunno how to find the records. No loss of data, as far as I know, and no corruption.
 
 I pulled the plug, pulled the monitor, haven't been able to recreate the problem.
 
Does anybody know what the reason for the problem may be, and how I may be able to prevent it from happening again? It seems the blackscreen error is common, but I can't find another poster who has the exact same problem.

I can't run fsck without damaging mounted drives apparently. And the hardware check for video seems to run through fine.

---

### Post by Rubruquis on 2010-01-07
If I understood correctly, when you pressed the power button, you didn't get any response from the computer except the power and satellite lights coming on.
I don't think it is an ubuntu related problem. It may be a BIOS or a hardware problem. Thing like these happen from time to time. You shouldn't make it a problem if it doesn't happen often.

---

### Post by nwadams on 2010-01-07
hey

if grub hasn't loaded I think its possibly a bios issue. (If anything at all). Try updating your bios.

---

