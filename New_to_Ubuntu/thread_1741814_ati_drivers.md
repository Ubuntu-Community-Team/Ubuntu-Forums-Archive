---
title: "ati drivers"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Old-un on 2011-04-28
I have an oldish HP Pavilion Desktop computer which runs Xubuntu 10.10 without any problem. But when the computer boots up the screen remains black? I have been told that it could be a driver problem? Could someone tell me how i can find out the specifications of my computer especially the onboard graphic chip and where i might find a suitable driver + how i might install the driver. Thanks all

---

### Post by Mark Phelps on 2011-04-28
To find out what graphics chipset you have, open a terminal, enter "lspci" and look for the line containing "VGA".  That will tell you the make and model video chipset.

That said, if it is a ATI/AMD chip (Radeon family) and it's NOT one of the newer HD 3x/4x/5x series, there are no new drivers you can install as AMD dropped Linux driver support for the older chips years ago.

Regarding the black screen, I'm running 10.10 and get that every once in a while as well -- and I do have the proper video drivers installed.

Next time that happens, press the SHIFT key to get a GRUB menu, choose the Recovery mode, and when presented with options, choose the one to repair broken packages.  When that finishes, choose the option to boot normally -- and you should then be presented with the standard desktop.

---

### Post by _0R10N on 2011-04-28
> **Old-un said:**
> I have an oldish HP Pavilion Desktop computer which runs Xubuntu 10.10 without any problem. But when the computer boots up the screen remains black? I have been told that it could be a driver problem? Could someone tell me how i can find out the specifications of my computer especially the onboard graphic chip and where i might find a suitable driver + how i might install the driver. Thanks all

I don't understand. If it works without any problem, how can it hangs when booting?. Did you mean that it used to work fine and now it doesn't?? If so, did you update or change something? Are you able to boot with a older kernel?

---

### Post by ndstate on 2011-04-28
If its Ati drivers you may also want to take a look at my bug report, check the 3rd response for a tip on how to get it to still boot.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763909](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763909)

---

### Post by Old-un on 2011-04-28
Have tried pressing the left-hand shift key during boot up but the screen still remains black?

---

