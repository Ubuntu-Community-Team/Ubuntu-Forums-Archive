---
title: "Problem with ubuntu 10.04 install"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Nielander on 2010-09-11
Ok...
I have kind a wierd installing problem..I think

I seem to be unable to install Ubuntu or Kubuntu(there seems to be no differnce on install) either from USB or live CD...

Once I boot from a USB stick or a CD I get the default menu with Try (K)Ubuntu; Intall ubuntu to a hard disk; esc...but when I hit either of those selections I get loads of log lines and it all ends up with text message WELCOME TO UBUNTU 10.04 and so on...and theres only command line with blinking cursor...

I've tried typing startx and hitting alt+F7 but then screen just goes blank and freezes...

Same problem happens with Ubuntu 9.04 original Live CD...but I am able to install or run a live sesson with Ubuntu 8.04...

I don't know what to do?
I would like to install Kubuntu 10.04, but it's always the same problem...

I'm not that great with Linux commands and terms...so I would be thankful if possible help is as easy to understand as possible...

Computer specs:
AMD Sempron 1.8 Ghz
1,5 Gb of RAM
SAPPHIRE RADEON&#8482; 9550

---

### Post by corrytonapple on 2010-09-11
Sounds like you downloaded the alternate install CD. You should try the full install version. You have plenty of RAM to do so.

---

### Post by Nielander on 2010-09-11
I'm sure I downloaded full install image - kubuntu-10.04.1-desktop-i386.iso
I downloaded one manually...same problem...then I used Unetbootin to download it automaticly...again, same problem...

Plus I have Ubuntu 9.04 original(requested CD)live CD that is doing the same thing...
It seems that I can't go above 8.04...although I haven't tried 8.10...

---

### Post by corrytonapple on 2010-09-11
Try the 64-Bit version of Ubuntu. It should not give you any problems. I know that is what I have.

---

### Post by coffeecat on 2010-09-11
Being dumped into a command line interface when trying to use the live desktop CD is often caused by graphics hardware/driver problems. A quick search of the community documentation shows that your Radeon 9550 *should* be supported, but the fact that 8.04 worked and later versions don't does suggest a driver problem.

There is one way that might get you into the desktop, but it's not elegant and involves using the old vesa driver. Monitor resolution will be limited and you won't get widescreen but at least it might be one step in the right direction. I'll flag this link...

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

... but also explain what I think needs to be done.

Boot up with the 10.04 CD and as soon as you see two small icons at the bottom of your screen, tap the space bar to get the main menu. (This bit isn't explained in that link so I think the link is not up-to-date.) Select your language and then press F6. When the little menu pops up, press ESC and you *should* then see the boot options ready for editing. Simply add the word "xforcevesa" to the end. Don't include quotes and make sure there is a space between the original end of the line and the word xforcevesa. Now press enter and the system should boot up using the vesa driver, hopefully into the desktop.

I don't think this is a good solution because if you were to install to the HD now you'd probably encounter the same problem with the HD install. But at least if you can get into a desktop this way, it excludes certain BIOS issues that sometimes cause this problem.

If you still don't get into the desktop, feel free to try some of the other boot options listed in that link.

Do post back with whatever happens.

---

