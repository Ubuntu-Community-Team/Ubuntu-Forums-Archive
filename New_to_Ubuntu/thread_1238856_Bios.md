---
title: "Bios"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by fslezak on 2009-08-12
I have a computer that crashed and I accedentally backed up the broken BIOS instead of restoring the good BIOS.

Is there a way for me to get the old BIOS back on the main chip?

Thank you for your help.

---

### Post by Revolutionary101 on 2009-08-12
Did the backing up process delete or overwrite the "good bios" file? If it did it will be close to impossible to recover it.

---

### Post by philcamlin on 2009-08-12
does anything happen when you turn on the pc?

---

### Post by fslezak on 2009-08-13
I have no idea. My machine might not have got my command. How do I figure this out?

The power light blinks very fast and the monitor is blank.

---

### Post by halitech on 2009-08-13
sounds like you just bricked your computer. what motherboard? there *might* be a way to restore it

---

### Post by wizard10000 on 2009-08-13
> **halitech said:**
> sounds like you just bricked your computer. what motherboard? there *might* be a way to restore it

Meh.  Just reset to defaults using the jumper on the motherboard.

---

### Post by halitech on 2009-08-13
> **wizard10000 said:**
> Meh.  Just reset to defaults using the jumper on the motherboard.

depends on the motherboard, I have seen a few with that option but normally if you screw up the bios, your toast unless you replace the bios.

---

### Post by fela on 2009-08-13
Yes, try to look for the jumper settings to reset the CMOS chip. If you can't find it, you can also (make sure computer is unplugged lol) just take out the CMOS battery for a few (say 10) minutes and then put it back in again. That's all assuming the fault is that the BIOS configuration is bad. If it's a actual bad BIOS file that you flashed it with, then I'm really not sure what to do about that.

Please keep me posted about this one! I hope you find a way of fixing it, I hate to see hardware go to waste, especially because of bad software.

---

### Post by Wim Sturkenboom on 2009-08-13
He destroyed his BIOS, not the settings. So removing the battery will not help at all (unless there is something that I don't know).

Some BIOS chips have a backup BIOS stored that you can copy back. Read the manual of the motherboard.

---

### Post by pricetech on 2009-08-13
Let's start with more information.  What brand of computer is it ??  If it's a "white box" system, what brand is your motherboard ??

It sounds like you flashed the BIOS with bad code.  Did I read that correctly ??

If not, then a buggy configuration may be all that's wrong with it and restoring to defaults might fix it.

---

### Post by LewRockwell on 2009-08-13
Re: BIOS...baked, broiled, simmered, fried, and toasted...rare, medium, or well-done?

mildly interesting...

however, it should be pointed out that if we had received specific information relating to the equipment(make, model, build/part number(s), operating systems installed, etc)...then we might have ALREADY offered one or more viable corrective actions and/or solutions...

not to mention someone might have a good, unbricked mobo to send to you if yours is trash...

once again, thwarted by the "no info monster"

argh...

{{sigh}}

.

---

### Post by fslezak on 2009-08-15
It is Ubuntu 8.04 LTS. The motherboard is a Gigabyte GA-8IPE1000 Pro, P4 Titan. The BIOS is a Dual BIOS, with a PhoenixBios D686 BIOS as main and a Gigabyte DualBios BIOS as a backup. The speaker beeps with the power light. There is a CMOS_CLR "3 solder position" There was also a BIOS_WP with a "3 solder position." The hard disk is a 80 gig SATA disk.

---

### Post by LewRockwell on 2009-08-15
> **fslezak said:**
> It is Ubuntu 8.04 LTS. The motherboard is a Gigabyte GA-8IPE1000 Pro, P4 Titan. The BIOS is a Dual BIOS, with a PhoenixBios D686 BIOS as main and a Gigabyte DualBios BIOS as a backup. The speaker beeps with the power light. There is a CMOS_CLR "3 solder position" There was also a BIOS_WP with a "3 solder position." The hard disk is a 80 gig SATA disk.

Note this is the page for revision two boards:
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1689](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1689)

according to Gigabyte's website and a few other sources, they claim to have a utility called "Xpress BIOS Rescue" which might help you out

this utility supposedly comes with the media shipped with the motherboard

Identifying your motherboard:
[http://www.gigabyte.com.tw/Support/Motherboard/FAQ_List.aspx?FAQID=2234](http://www.gigabyte.com.tw/Support/Motherboard/FAQ_List.aspx?FAQID=2234)

Here's an old thread where Bill Parrish is investigating how the "Xpress BIOS Rescue" supposedly works:
[http://www.hardforum.com/showthread.php?t=1196073](http://www.hardforum.com/showthread.php?t=1196073)

keep us posted on this!

.

---

### Post by sandyd on 2009-08-15
Most motherboards have a BIOS backup somewhere on them. IM not going to post the link here, because the software is conterversial, but search on google for killcmos

---

### Post by fslezak on 2009-08-16
rrrrrr.... I think I corrupted my backup, too. The system might have not gotten my command. I dunno. I think it's bricked. By the way, I can't see anything on the screen. Static?

---

### Post by LewRockwell on 2009-08-16
> **carlee said:**
> Most motherboards have a BIOS backup somewhere on them. IM not going to post the link here, because the software is conterversial, but search on google for killcmos

don't use killcmos...

.

---

### Post by LewRockwell on 2009-08-16
when you first hit the power button...

what EXACTLY happens?

(to describe this accurately it may require several cyclings of your machine, don't just say the screen is blank if there are...in fact, characters/letters/numbers/words/etc scrolling across your screen)

what happens when you have a DOS boot floppy inserted when you turn it on?

any difference?

.

---

### Post by fslezak on 2009-08-16
There is NOTHING on the screen. The machine runs for a second with the Hard Disk Read on for a second and then the power light blinks quickly and I had to unplug the speaker since it kept beeping with the power light on. By the way, I do NOT have a floppy drive, but I have a AntiVirus Boot disk. Should I try that instead?

P.S. I selected Remote Desktop Sharing to On. Did that affect something?

---

