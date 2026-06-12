---
title: "Ubuntu is running in low-graphics mode"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by itsols on 2010-06-11
After my upgrade to 10.04 (from 8.04), I had to do a miracle and get my computer back in working order. After the initial upgrade, I could not boot and I discovered that the graphics system on my Dell Inspiron 1150 had issues with Ubuntu. But now that's FIXED.

Strangely though, in the last one week, my system has hung up at least 6 times while working. There seems to be no apparent reason for this 'seizure' but it suddenly surprises me with a message like "Ubuntu is running in low-graphics mode" and a supporting description.

Often when this happens it gives me options like 'reconfigure' graphics... Unfortunately it does not seem to get anywhere ahead.

I really love the new look and feel of this version. But it's also bogging me down.

Any help please!

---

### Post by pizza-is-good on 2010-06-11
Do you have the driver for your GPU installed?

Check in System >> Administration >> Hardware Drivers

---

### Post by itsols on 2010-06-11
What do you mean by driver for GPU? I'm a little lost there :)

---

### Post by Mark Phelps on 2010-06-13
If the Google search I did for your Dell is correct, you have motherboard-based Intel graphics -- for which Hardware Drivers will not show anything.

Also, if you're getting a graphical desktop, by definition, a driver for your "GPU" must already be loaded.

FYI, the GPU is the Graphics Processing Unit -- essentially, the video chip.

I don't know what model Intel chip your machine uses, but Intel graphics had majro problems in Ubuntu 9.10 and that continues into 10.04.  My best advice at this point is for you to do a search in the video subforum to see if anyone has posted any solutions for Intel graphics problems yet.

---

### Post by itsols on 2010-07-23
First, thank you for the advice.

It is rather unfortunate that my low-graphics (screen of death) shows up at least 4 times a week.

Anyway, I think I figured a way out.

First, my observation: During a day's work, the screen goes berserk and the beautiful warning appears about my screen in 'low graphics mode'. The only thing that works is that I select the first option to continue in low graphics mode. Then I find myself having to log-in and restart my apps. The borwser restores its sessions... My work is generally lost... BUT after that selection, the machine does not crash, unless of course I reboot.

So my question: Is it therefore possible to simply start the computer up in low graphics mode? This way, I shouldn't be seeing the warning.

I hope I'm correct here - smiles...

NOTE: If someone has the slightest idea that my RAM or video is insufficient, please withdraw that thought, as we have a super-duper PC at college (where I teach) and we have the same issue.

Cheers!

---

