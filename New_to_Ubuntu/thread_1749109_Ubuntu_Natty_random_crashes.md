---
title: "Ubuntu Natty random crashes"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by gidra on 2011-05-04
Just upgraded to ubuntu natty and I'm getting random system crashes without any type of warnings. The system completely fails, I can't even move mouse or get keyboard input, just have to reset from my pc reset button. I'm doing some serious projects on my machine and I can't afford this kind of behaviour. Any suggestions please? thanks

---

### Post by sadaruwan12 on 2011-05-04
Can you be specific with the details and please tell us about your PC spec as well it'll help us to determine the problem your having.

---

### Post by gidra on 2011-05-04
Thanks sadaruwan12 for your prompt reply. As far as the problem goes I can't really get more specific since ,as I already stated, the freeze occurs at random periods without any warnings. The computer just hangs there with no hardware response whatsoever (even sound hangs). The freeze also occurs in Ubuntu classic interface. 

I'm on an x64 machine, core i5, 8gb ddr3 memory, nvidia gpu with dual monitor setup. I also had never experienced this kind of behaviour with any prior versions of linux

---

### Post by Nickjpost on 2011-05-04
If it seems to occur at random, total system lock-up, I might suggest doing a backup and reinstall from live CD or USB. I currently am running Natty x64 on i5, 8GB ddr3, intel HD video card and have not had an issue as of yet. I upgraded on the official release date.

---

### Post by sadaruwan12 on 2011-05-05
I'm guessing that you're using x64 bit version of the distro any way I've come across lot of issue with the nVIDIA driver the latest recommended version So I suggest that downgrade to a earlier version as I've done the older version number is 173.x.x try doing this from the additional drivers wizard.

This resolved a big problem for me in 11.04 try this and see whether your problem gets solved.

---

### Post by NCLI on 2011-05-05
As a general precaution, you should always have some time on your hand when doing a system upgrade, just to be on the safe side. Doing it while working on a major project may not have been the best idea.

If downgrading the nVidia driver doesn't work out for you, you should probably downgrade to 10.10.

---

### Post by EGamerHDK on 2011-05-05
Yes, definitely try to activate the other drivers available in "Additional Drivers". Seems to be the answer to a lot of questions as of late.

**EDIT**: Just updating because I have more input now. I really think it's the video drivers because when your system "crashes" it just gets stuck at a graphical screen. Let us know.

---

### Post by amulet on 2011-09-23
I confirm I have precisely the same problem, working on 32 bit desktop with LAN. It can happen 3 or 4 times a day or not at all for 3-4 days! Totally random, and totally infuriating.  I don't have any propriety drivers listed in Additional Drivers, so can't roll back using that possible solution.

Any other ideas?

---

