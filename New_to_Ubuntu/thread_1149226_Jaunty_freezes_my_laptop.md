---
title: "Jaunty freezes my laptop"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by AncientPC on 2009-05-05
I'm running 9.04 x86 on my Thinkpad X61s and occasionally (once a few days) it will lock up.  My mouse can move but that's about it.  I can't use ctrl+alt+backspace or ctrl+alt+f1 either to reset X.org.

---

### Post by Peter09 on 2009-05-05
Look in the log files to see if there are any messages there and keep htop running to see if you can get an idea of what is locking the system up.

---

### Post by zimmerj on 2009-05-06
Do you have an intel graphics card?  If so your problem may be a driver issue.  I think people are currently working on a fix.  I'm also having the same problem and looking for a workaround.  Check out these sites:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)
[https://wiki.ubuntu.com/X/Bugs/IntelDriver](https://wiki.ubuntu.com/X/Bugs/IntelDriver)

This apparently is a big problem for people with intel graphics cards, and not necessarily limited to people with one specific chipset.

---

### Post by Happibun on 2009-05-14
This is happening to me too. I upgraded to 9.04 from 8.10 about 2 weeks after it came out.

Yes, I have an Intel graphics chip - Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)     

I followed the fix outlined here in [this forum]("http://ubuntuforums.org/showthread.php?t=1136738"), and my video works a lot better, but I still get Ubuntu crashes where the only thing I can do is move my cursor. I can not click on anything, no key or key combination produces any result, leaving the lappy on overnight does nothing, and all I can do is hit the power switch.

This is getting more than irksome, especially since the laptop was operating so well under 8.10. I'm being philosophical and looking at this whole thing as an exercise in learning more about the OS, but my patience is getting tried. I am not used to Ubuntu being so unstable. It is starting to look like going back to 8.10 will be the better option.

In the meantime, I use my net-book running Mint if I need a stable session. :(

---

### Post by kennethmsmith on 2009-05-14
don't forget to test your RAM (memory) also.  I recently had problems and found out through a memory test that I had bad RAM.

---

### Post by AncientPC on 2009-05-18
Yes, I have an Intel GMA X3100 GM965 integrated graphics card.  I've since then disabled Compiz since there are known issues with Jaunty and Intel graphics (a pity since I buy Intel graphic cards for their open source drivers) and haven't had a crash since.

---

### Post by Cabo_Nobby on 2009-05-22
I have exactly the same problem as happibun. How can i disable compiz?
Because when i set the Aparence, my screen efeccts are set to none. and it still crashes.

Is someone trying to fix this, or i will have this issue until i change my laptop?

thx

---

### Post by roger64 on 2009-05-25
Hi

I have an Intel 915 which randomly freezed during these last four weeks (since I updated to jaunty). About once or twice a day. Truly enjoyable experience...

It seems (well three days now...) I finally solved this by downgrading to the Intrepid Intel driver.

I followed this merciful advice

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Hope this helps.

---

