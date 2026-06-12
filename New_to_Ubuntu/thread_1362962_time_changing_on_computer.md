---
title: "time changing on computer"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ericgds on 2009-12-23
Hi. I am using a live cd and it seems that everytime I go back to windows vista after using ubuntu live cd the clock on my computer is reset to the wrong time.  Can anyone help me with this.  Thanks.

---

### Post by taurus on 2009-12-23
Does your BIOS use local time or UTC?

---

### Post by ericgds on 2009-12-23
Well I'm ashamed to say I have no idea nor do I know how to check this.

---

### Post by taurus on 2009-12-23
How far off is your clock after you use Ubuntu LiveCD?  Which timezone are you in?

---

### Post by ericgds on 2009-12-24
I'm in pacific time and I think ubuntu puts me about 8 hours ahead of this.

---

### Post by admiralspark on 2009-12-24
is the date wrong also? Meaning that, if the little system battery (can't remember the proper name) is dead, the time will reset itself every time Windows is loaded. I've had that problem with our PC using windows, every time the power goes out it resets the time and date.

---

### Post by ericgds on 2009-12-24
I don't believe the date is altered.

---

### Post by taurus on 2009-12-24
Sounds to be like PT and UT, 8 hours ahead/behind.  Is your BIOS using localtime or UT?  When you first turn on your machine, you need to press one of those special keys (F2, F12, Esc, etc.) to get into the BIOS.  You have to do it quick before GRUB starts up though.

---

### Post by Garyhans on 2009-12-24
Every time I use the live cd then reboot to my normal install the time is changed and I have to reset it. Use to that. It isn't a Bios Issue here.

---

### Post by Geoff918 on 2009-12-24
> **Garyhans said:**
> Every time I use the live cd then reboot to my normal install the time is changed and I have to reset it. Use to that. It isn't a Bios Issue here.

No, it's merely that most servers use UTC (Greenwich Mean Time, England).

Ubuntu assumes that your system is set to UTC. PT is -8:00 from UTC. You'll find the minutes undisturbed and the hour being different. You can set Windows to auto-sync, or just manually adjust.

---

### Post by ericgds on 2009-12-24
OK. Nice to know it's not caused by a problem with my computer. I suppose it's not too hard to change the time manually but if someone wouldn't mind showing how to set windows vista to auto sync that would be great.

---

