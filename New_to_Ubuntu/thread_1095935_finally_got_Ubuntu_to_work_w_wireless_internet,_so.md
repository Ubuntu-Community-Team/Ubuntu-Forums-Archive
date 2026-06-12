---
title: "finally got Ubuntu to work w/ wireless internet, some more questions."
date: 2009-03-14
forum: New to Ubuntu
---

### Post by meteora184 on 2009-03-14
Two questions:
1:
I unstalled Ubuntu 8.04 with their convenient DVD I purchased. IT dual boots w/ XP.  When I finally got a connection going, I updated my Computer (Via update manager) and now, when i turn on the Computer, it has two versions of Ubuntu, 8.04.16 (something like that), and 8.04.28 (forget the exact numbers).
How would I get rid of the older version (8.04.16).

2:
When i startup Ubuntu, it usually has a loading screen.  My PC just shows a black screen for 30 or so seconds, then goes straight to the login screen.  How would I be able to set it so it shows the loading screen.

---

### Post by davmac on 2009-03-14
1) Next time it is booting up jot down the numbers. Once started, fire up Synaptic ( System -> Administration -> Synaptic Package Manager ) and then search for the text - it'll be something like "2.6.27-7". You can then uninstall it.

2) While you're in Synaptic check that you've got usplash installed. If it is then I'm not sure what else you can try.

Regards,

Dave Mac

---

### Post by ugm6hr on 2009-03-14
I would recommend you keep your current kernel as well as 1 old version, in case you discover a hardware compatibility issue with the new kernel, or something gets corrupted.  Not necessary, but it is nice to have a security blanket.

If you just want to remove it from the displayed list, you can edit /boot/grub/menu.lst to not display it, but you can at least still manually boot into it by editing the grub line manually.

As for the splash screen, have you ever had it work?  Some graphics cards misbehave when using the splash screen (an ATI card I have will not display splash screen using TV out).

You can check the relevant line in /boot/grub/menu.lst and ensure it says **splash quiet** at the end.

---

