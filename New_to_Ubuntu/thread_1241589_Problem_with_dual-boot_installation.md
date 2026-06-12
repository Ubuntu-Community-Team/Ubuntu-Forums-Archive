---
title: "Problem with dual-boot installation"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Ian Ferguson on 2009-08-16
I'm trying to install Ubuntu 9.04 in dual-boot mode on a Toshba Equium P200D runnng Windows Vista Home Premium, using a disc purchased from The Linux Store (so it should be a good disc).

After booting from the disc, I get the startup page, followed by the page where I choose the language, but then it stops and shows a screen with the following

> [      0.368001]  ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[      2.440037]  ata1: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory

Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _(Actually, the first two lines of this appeared right at the start, but then it carried on)

Any suggestions as to how to fix this? Do I perhaps need to do something in my BIOS first?

---

### Post by vedek on 2009-08-16
looks like a problem with either the HD or the live cd that you are using.

so u might want to check that out.

If you are sure that the HD works then try getting a new live cd

---

### Post by Ian Ferguson on 2009-08-16
The HD works fine in Windows.

I first encoutered this problem a while ago when I tried to install from a live CD which I had burned from a downloaded .iso. That's why I decided to buy a live CD, thinking that the one I burned may have been corrupted.

After searching some forums, I've found a fix for the first problem (MP-BIOS bug: 8254 timer not connected to IO-APIC). During the boot, I hit F6, selected "noapic" form the pop-up menu, hit ESC to close the menu, then Return to continue the installation.

This time the first line didn't appear, but I still got the rest.

I suspect that the "ata1: softreset failed (device not ready)" error could be to do with the fact that I'm using an external USB DVD drive, because the built-in drive on my laptop is broken. Anyone know of a fix?

As for the third error (modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory), it looks as if this is a file it's trying to load from the disc, but I've searced the disc and there's no such file on it. In fact there isn't a "lib" directory. Should there be? If so, then it looks like I've got another dud disc!

---

### Post by presence1960 on 2009-08-16
boot options scroll down to the section dealing with F6. you want to try those options when booting the live CD such as noapic. if that doesn't work try the other options under F6.

If all else fails download the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by presence1960 on 2009-08-16
> **Ian Ferguson said:**
> The HD works fine in Windows.

I first encoutered this problem a while ago when I tried to install from a live CD which I had burned from a downloaded .iso. That's why I decided to buy a live CD, thinking that the one I burned may have been corrupted.

After searching some forums, I've found a fix for the first problem (MP-BIOS bug: 8254 timer not connected to IO-APIC). During the boot, I hit F6, selected "noapic" form the pop-up menu, hit ESC to close the menu, then Return to continue the installation.

This time the first line didn't appear, but I still got the rest.

I suspect that the "ata1: softreset failed (device not ready)" error could be to do with the fact that I'm using an external USB DVD drive, because the built-in drive on my laptop is broken. Anyone know of a fix?

As for the third error (modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: no such file or directory), it looks as if this is a file it's trying to load from the disc, but I've searced the disc and there's no such file on it. In fact there isn't a "lib" directory. Should there be? If so, then it looks like I've got another dud disc!

if the optical drive is a problem try using a bootable USB version of the Live CD if your machine can boot from USB that is. Download [unetbootin]("http://unetbootin.sourceforge.net/") to create it.

---

### Post by Ian Ferguson on 2009-08-22
I'm afraid none of these solutions has worked for me, but I've succeeded in installing Ubuntu 8.04 from a disc burned from a downloaded .iso image. The message about "timer not connected to IO-APIC" still pops up briefly at the start, but it carries on and boots up anyway. The only trouble is, my wireless adaptor doesn't work. (It's an Atheros AR5007EG, driver is athr.sys, inf file is netathr.inf). I've tried ndiswrapper, but it just says my driver is invalid. I've yet to try linux-backports-modules-hardy. I can connect to the Internet by cable, but it's an inconvenience having to do so, and if I'm going to go over to using Ubuntu as my everyday OS, as I want to, then I really need to have wireless.

So it seems I have two courses of action open:

1. Stick with 8.04 and try to get the wireless working.

2. Try to upgrade to 8.10 or 9.04. I understand that they have better support for wireless adaptors than 8.04 and earlier, but will the same boot problems come back? Watch this space!

---

### Post by Ian Ferguson on 2009-08-22
Success!

Connected via cable to internet.

Upgraded to 8.10. Upgrade went fine, no boot problems, but wireless adaptor still not working.

Upgraded to 9.04. Everything works straight off, including the wireless adaptor! I still get the same error messages at the start (timer not connected and softreset failed), but it boots up anyway.

So now I have a fully functioning, up-to-date Ubuntu system, but with Windows still there for a couple of applications that I still need it for.:lolflag:

---

### Post by LewRockwell on 2009-08-22
thank you for posting details regarding your accomplishments!

.

---

