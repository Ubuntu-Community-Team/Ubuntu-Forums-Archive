---
title: "Existing install of 9.04, switch to ext4? And how, foolproof?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Dvdre on 2009-11-16
I have a 9.04 install, it is set up JUST RIGHT, and I love it, but no personal data I need to worry about, not a single file. But I worked hard to get it set up JUST RIGHT.

Then I read about the ext4 file system, faster boot times, etc., my ext3 boots up in 50 seconds now with the boot list (Windows 7) and login in and even the wireless connection. So it can't be much faster.

Should I bother trying to switch to ext4, given I have no data to be worried about today?

Should I do a fresh install, and if so, how? How, for example, do I move my home directory to a different partition during the install? That would be worth doing if I do this again. Step by step, if possible.

Or, try to switch to ext4 on the the existing install? Nothing much to lose, again. What is the foolproof way, step by step?

Or just forget the whole thing?

Don't bother suggesting 9.10. I tried. Didn't like.

---

### Post by Ji Ruo on 2009-11-16
I have experienced an improvement with speed using ext4, but this was on old hardware (think: celeron). 50 seconds seems like a reasonable boot time - my desktop is a 3.06GHz Prescott with a SATA drive, and with an ext4 boot of Jaunty (from pressing the button to login screen) it takes just over 50 seconds. So I don't think you will see any significant improvement in boot times with your hardware.

If you should bother - I think it's up to you. I enjoy trying out new technology and experimenting with it, maybe you do too.

I did a quick search for 'transfer ext3 ext4' on [www.google.com/linux](www.google.com/linux), here are a couple of sites from the first page -

[http://www.ibm.com/developerworks/linux/library/l-ext4/](http://www.ibm.com/developerworks/linux/library/l-ext4/)
(Of course you won't have to recompile the kernel, as Jaunty already supports it).

[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)
(Regarding GRUB, the configuration file in Ubuntu Jaunty is the one that's listed in brackets, /boot/grub/menu.lst - to edit you would press <ALT>+<F2> to get a launch bar and type: gksudo gedit /boot/grub/menu.lst )

You will probably want to research it a bit more, but hopefully this will get you started if you're interested. HTH

---

