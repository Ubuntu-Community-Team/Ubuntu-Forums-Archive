---
title: "T60 won't hibernate after upgrade to 10.10"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by netipot on 2010-10-26
When I close my T60 thinkpad lid it used to hibernate and awaken when opened using 10.04, but about two weeks after upgrade to 10.10 it will not awaken. I get a blank screen with this message,
Device 0000:02:00.0 already exists at 000:02:00, cannot hot add
atombios stuck in loop for more than 1 sec aborting
atombios stuck excuting ED7A(len86,W54,PS0)@0xEDAD
Same thing happens when I use my keys Fn F4. This started happening right after I hooked the T60 up to a monitor.
Also I can no longer get into nautlus without it opening f-spot to import. I am working around it by opening trash or my computer to get into nautilus.
Any ideas?

Harold

---

### Post by metalf8801 on 2010-10-30
I also have a Lenovo T60 Thinkpad and it can't hibernate either since I did a clean installed of Ubuntu 10.10. However, I was not having this problem with Ubuntu 10.04. 

Here's the error message that comes up when I try to put the computer into hibernation
[34112.688052] pciehp 0000:00:1c.0:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add 
[34112.688055]  pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:02:00
[34112.200026] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting 
[34112.200030] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing ED7A (len 86, WS 4, PS 0) @ 0xEDAD


PS I'm not having a problem with nautlus, but I don't have F-spot installed so that I might be why. 

Does anyone have any idea what this error message means? 

Thank you 
Dan

---

### Post by metalf8801 on 2010-10-30
> **netipot said:**
> When I close my T60 thinkpad lid it used to hibernate and awaken when opened using 10.04, but about two weeks after upgrade to 10.10 it will not awaken. I get a blank screen with this message,
Device 0000:02:00.0 already exists at 000:02:00, cannot hot add
atombios stuck in loop for more than 1 sec aborting
atombios stuck excuting ED7A(len86,W54,PS0)@0xEDAD
Same thing happens when I use my keys Fn F4. This started happening right after I hooked the T60 up to a monitor.
Also I can no longer get into nautlus without it opening f-spot to import. I am working around it by opening trash or my computer to get into nautilus.
Any ideas?

Harold

Netipot have you filed a bug report on Launchpad?

---

### Post by netipot on 2010-10-31
I haven't filed a bug report yet. I will. To clarify, I can't wake up from suspend. That is when I get the error message. The first day after the upgrade it worked fine. I thought I helped myself when I went into power management and changed my preferences to hibernate upon closing the lid. When I did that, it worked, though I prefer suspend because it is faster. However when I booted up the next day I found that I can't wake up and all I get is a blank screen. So we must have very much the same problem. Have you filed a bug report yet?

---

### Post by netipot on 2010-10-31
Hey, I got rid of f-spot and that solved my nautilus problem. I was forced to embrace shotwell. Oh well.

---

### Post by netipot on 2010-11-20
To let any one who might stumble onto this thread you may be able to get your laptop to suspend by going into terminal and installing acpitool,
[FONT=Courier New]sudo apt-get install acpitool[/FONT]
then type,
[FONT=Courier New]sudo acpitool -s [/FONT]

---

