---
title: "Problems on Dual Boot System"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by john.hall on 2009-01-05
OK, I really have 2 problems.

1.  I got a new motherboard.  At first, it recognized my USB wireless keyboard/mouse.  Now, however, the keyboard/mouse have power until it gets to GRUB (I can go into BIOS setup just fine), then loses power.  If I allow it to continue booting into Ubuntu or Windows, the power comes back on, but I cannot make a selection from the GRUB menu because I don't have power at that time.  I am currently having to use a wired keyboard just to use the GRUB menu.  Any ideas on what changed or how I can get power back during that time?

2.  I cleared my CMOS, then set the clock to the correct time.  Now when I boot to XP, I get a message box with no text or window title.  If I log in as administrator, it has Yes and No buttons.  If I log in as limited user, it has an OK button.  Either way, I get immediately logged back out, and I cannot do anything.  Clearing CMOS a second time doesn't fix the problem.  How do I log in to Windows?

Problem #2 isn't technically related to Ubuntu (at least, I don't think it is), but this forum is the most active one I have seen in a long time, and I'm more likely to get help here than anywhere else.  Thanks for all the help in the past, and thank you in advance for any help you can provide me now.

---

### Post by gn2 on 2009-01-05
If you have cleared the CMOS with the jumper, or removing the battery you will have set everything back to factory defaults.
You need to go through it all and check that all the settings are reset manually to what they were before, e.g. set Legacy USB support on.

Is the problem that you have set a BIOS password that is not recognised, or is it a Windows log-in problem?

---

### Post by john.hall on 2009-01-05
It's a Windows log-in problem.

And thanks, I will check that legacy USB support is on.

---

### Post by gn2 on 2009-01-05
> **john.hall said:**
> It's a Windows log-in problem.

Back when I used Windows I never used passwords, so I can't help with that problem I'm afraid.
Hopefully someone else will be able to assist.

---

### Post by suomalainen on 2009-01-05
In Ubuntu the time is set to UTC time. This will then reset the time in BIOS and effect the time as XP see's it. TO have both operating systems use the correct time you need to turn UTC time to "Off" in Ubuntu.

It's done like this:

In a terminal:
gksudo gedit /etc/default/rcS
Look for this line: UTC=yes
Change it to: UTC=no
And save it:
Then set the time if it is wrong in System/Administration/Time and Date

Hope this helps.

---

### Post by john.hall on 2009-01-05
UTC is off.  Actually, the Ubuntu clock is correct, even though the motherboard clock is incorrect.

I don't think it is a problem with the password.  I didn't change the password, and I am typing it in correctly.  The problem just happens to show up after I type in the password.

EDIT: I just reinstalled, and everything seems to be working correctly from the Windows side.  I also turned on Legacy USB Support, which allowed me to make selections in GRUB.  Thanks!

---

