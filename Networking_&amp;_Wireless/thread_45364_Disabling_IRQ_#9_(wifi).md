---
title: "Disabling IRQ #9 (wifi)"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by StupidHaiku on 2005-06-29
Hey all, I've been trying for over a month to get my wireless working on my laptop under Hoary.  I originally had it working fine under mandrake, but it refused to work anymore after I reinstalled that distro, so I switched to ubuntu and have gone through 3 reinstalls trying to get it to work.  After numerous googles, forum posts, and good old fashioned elbow grease I think I've narrowed down the problem.  Now I should mention that my wireless works maybe 1 out of 10 times that I reboot.  Comparing the output of dmesg when it works and when it doesn't it seems to be an issue of ubuntu 'Disabling IRQ #9' before installing the madwifi modules. (Strange, this is IRQ #11 when using the bottom PCMCIA slot, yet windows device manager reports them both as using #9.  Don't know if that's normal.)  Is there any way to counteract this, or anyone have any ideas at all for me?  It's just my guess that the IRQ is the problem, I'm not positive.  I know this is a little skimpy on details, I've just been through a lot so ask if you need any more info.  All help greatly appreciated.  
Thanks,
Mike

---

