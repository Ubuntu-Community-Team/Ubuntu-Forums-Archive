---
title: "Help adding windows 7"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-05-03
Hi everyone, I'm pretty new to linux and 10.04 is my first attempt. I made the switch because my xp went to hell again and decided to dual boot with ubuntu and am loving it, 
I haven't even used the xp partition since setting it all up.

Now I have encountered an unexpected problem, when my xp decided that speed was of no importance to anyone, my girlfriend thought it'd be nice to order me a copy of windows 7. This has now arrived I have installed ubuntu and got it all going how i like it. My problem is that my limited knowledge  only includes how to install windows 7, then install ubuntu to get the dual boot working. I would really rather not do this again!

I was just wondering how I install windows 7, then install the GRUB loader without having to reinstall ubuntu?

Thanks in advance - this would be a huge help!

---

### Post by blazemore on 2010-05-03
It's really easy,

Write this down.

Install Windows 7
Boot from the Ubuntu LiveCD
Run the commands:
```
sudo grub-install /dev/sda
sudo update-grub

```

Then reboot!

---

### Post by head2head on 2010-05-03
I did this recently and the key is restoring Grub (the ubuntu bootloader) after the windows installation.

Try here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Note that you will be using Grub 2 with 10.04.


Hope that helps!

---

### Post by sylvainrb on 2010-05-03
I think you might have to create a ntfs partition using gparted before you install Windows 7 so it doesn't overwrite your Ubuntu install... Others correct me if I'm wrong!

---

### Post by blazemore on 2010-05-03
> **sylvainrb said:**
> I think you might have to create a ntfs partition using gparted before you install Windows 7 so it doesn't overwrite your Ubuntu install... Others correct me if I'm wrong!
There needs to be enough space.
Windows can only install on a primary partition.

I assumed OP was going to overwrite his existing XP partition, so didn't mention it.
But yes, you need a partition (doesn't need to be formatted, win7 installer will do that, and you should let Windows format ntfs always)

---

