---
title: "monitor resolution and mouse problem"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by chrislang on 2009-05-13
I've installed ubuntu 9.04 on my [zonbu mini]("http://www.zonbu.com"). The screen resolution is 800x600 and there is no mouse cursor (the mouse works though, when I click on things).

My graphics device is: "VIA CX700M2 UniChrome PRO II, VGA output, supports up to 2048 x 1536".

I've been running zenwalk 6.0 on the zonbu and had similar problems, which I sorted out by editing xorg.conf. The details [are here]("http://support.zenwalk.org/viewtopic.php?f=10&t=21707").

I've just tried editing xorg.conf in ubuntu 9.04, but now the screen goes black before the log in screen comes up. I took a copy of my edited xorg.conf - but it's hidden somewhere behind the black screen. It was a mixture of what worked in zenwalk and [this]("http://ubuntuforums.org/showthread.php?t=1134552").

Any suggestions for editing xorg.conf would be gratefully received - or any other suggestions, for that matter. Thanks!

---

### Post by Didius Falco on 2009-05-13
Welcome to the Ubuntu Forums!

You said you took a copy - I hope by that you mean that you saved a backup of it. If that is the case, reboot into the Recovery Mode. When the screen with the menu of choices comes up, select the Command Line option.

After it finishes booting, you'll be at a black screen with a command line at the bottom. type ```
cd /etc/X11
``` That will put you in the X11 directory. Then type ```
dir
```, which will list all the files in the directory.

If you want to save a copy of the xorg.conf that you have been working on, type ```
sudo cp xorg.conf xorg.conf.wip
```.

Then you can replace the bad xorg.conf with the backup copy you made earlier with a similar command: ```
sudo cp xorg.conf.nameyouused xorg.conf
```

then type ```
sudo reboot
``` and you should be able to boot normally.

If you have a Live CD handy, you can just boot into  that inthe "make no changes to the PC" mode, navigate to the file and rename it - you'll still need root privileges, though, so open a Terminal and type ```
gksudo nautilus
``` and then navigate to the file.

Regards,

Didius

---

### Post by chrislang on 2009-05-14
Thanks Didius! That got me back to the 800x600 problem - in glorious technicolour though, not just black.

I've now installed xubuntu 8.10, which works a treat - the screen resolution is perfect and the mouse cursor works. 

I'd like to upgrade to 9.04 at some point, so if anyone can suggest any tweaks to xorg.conf that would be cool.

Thanks.

---

### Post by silvertuna on 2009-05-14
FYI, on my Zonbu mini I also had to install Intrepid 8.10 instead of Jaunty 9.04 for the same reasons - wrong screen resolution and invisible mouse pointer.  Intrepid works great but eager for the Jaunty fix.

---

### Post by chrislang on 2009-05-15
Thanks silvertuna - nice to know it's not just me.

Pieter on the [zonbu forum]("http://www.zonbu.com/forums/viewtopic.php?f=9&t=145&sid=6531736434bde0ec59db19c2d79fc789&start=50#p2776") has the same problem. So that's at least three of us.... If anyone has any suggestions, please let us know!

Thanks.

---

### Post by silvertuna on 2009-05-17
I have found a number of posts in Linux forums suggesting the addition of "HWCursor" "off" in the Devices section of Xorg in order to make the cursor reappear. I do not have my Jaunty installed now, but maybe someone out there can try it or confirm that it works.

---

### Post by silvertuna on 2009-06-22
Has anyone found a solution to Zonbu Mini screen reso and cursor problems installing Jaunty?

---

