---
title: "Is there a way to permanently enable WOL via GUI?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2007-12-03
WOL works great if I shutdown my machine from Windows 2000 or Windowx XP (multi-boot with Ubuntu 6.06 LTS).

But if I shutdown the machine from Ubuntu, it does not wake on LAN.

In my search for a solution I found that, like in Windows, Ubuntu needs to "help" the hardware a little bit so that WOL would work:
```
sudo ethtool -s eth0 wol g
```
But one needs to remember to do it before *every *shutdown of the machine (which is foregetfullness prone , of course).

Knowing Ubuntu, there must be a smart automated solution somewhere which would enable this ability once and for all.

If indeed this is the case, where do I find it?

If this is not the case, then I would like to program this command into a shutdown script in Ubuntu. Is there such a thing, "shutdown script"? If so, where do I find it? 

Thanks,
Alex

---

### Post by Big_Croc7 on 2007-12-19
In case you haven't found it already:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
Towards the end it tells you how to put it into a script that runs every time.

---

