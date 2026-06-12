---
title: "Attempting to Dual boot win 7 and ubuntu"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by raw157 on 2010-10-03
Alright, first off, I'm rather new to linux as an OS always been a Windows guy, but was looking to try and learn something new. I have Ubuntu as my OS on my netbook and i really like the way the pictures and stuff are sorted, so I wanted to dual boot it on my desktop with Windows 7. 

I've read all the stickies and stuff and googled around but I can't find anything that solves my problem. When I boot into the CD I go to install, select the partition i made for it in Windows7 and it installs fine. However, as soon as I update it and restart and try to get back into it, it just freezes at the purple ubuntu screen. 

My windows7 is a x64, so I tried x64 ubuntu, I also tried 32bit just to see what happened. Neither worked as far as getting past the first reboot after updates.

Edit: Ubuntu 10.04

Ideas?

Thanks,
RAw

---

### Post by oldfred on 2010-10-03
Probably a video issue. What video card? Try changing the quiet splash to nomodeset or other (below) to see if it works.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

### Post by raw157 on 2010-10-03
GTX 465 is the card
But i tried it also with my old 9800 GT. 

I'll give that a shot. Thanks

---

### Post by raw157 on 2010-10-03
After trying that, before I even install, it freeze at the ubuntu screen

---

