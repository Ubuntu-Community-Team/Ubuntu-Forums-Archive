---
title: "iTunes update broke Ubuntu?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by earthpigg on 2011-02-28
Hi,

I installed Ubuntu on a friend's netbook in a true dual boot config (not wubi) that had win7 installed by default.

She's been doing ok with it for the last 5 months or so, but here's what she is telling me now...

-She needed to use iTunes to fix her iPod for some Apply reason, so she started win7 for the first time in months and did the iTunes update thing.
-Phone fixed, yay.

-Restarted to get back into Ubuntu.
-Computer restarts itself over-and-over-and-over-and-over again before grub.
-The bios works. F2 for system setup, F12 for boot menu.
-Holding shift for the grub menu does not work. It still restarts over and over.

Anything jump to anyone's mind?

I have to do this over the phone for now. Ugh. Any suggestions would be helpful. I'm asking if she still has the bootable usb i gave her...

---

### Post by bcbc on 2011-02-28
Reinstall Grub2. I wonder if itunes messes with the boot track for DRM.

---

### Post by Ben Page on 2011-02-28
Reinstall GRUB. It seems that Windows did a disk check before booting to repair the inconsistence that Ubuntu caused on Windows partition, thus it "repaired" the MBR.

---

### Post by Grenage on 2011-02-28
> **earthpigg said:**
> (not wubi)

I'd probably reinstall grub from a livecd.

---

### Post by earthpigg on 2011-02-28
OK, thanks for the advice guys. i went with the consensus solution of reinstalling grub2, and it worked.

documentation of the fix...

gave her directions in a [stinto]("http://www.stinto.net/") temporary chat room... i like stinto because there is no setup, and it works with FF from the livecd without installing anything.

I did indeed have her re-install grub2 from a LiveUSB following this set of directions:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

deviations from those directions:

-i used gparted instead of fdisk -l, as i normally do, to find out what partitions we wanted to work wtih.
-skipped this: sudo cp /etc/resolv.conf /mnt/etc/resolv.conf (saw no point)
-skipped this: nano -w /etc/default/grub (the options were fine, no reason to change them)
-"grub-install /dev/sda" worked fine, so no need for "grub-install --recheck /dev/sda"

marking thread as solved.

---

### Post by Grenage on 2011-03-01
Glad to hear you got it solved; phone support can be a nightmare.

---

### Post by yakinikku on 2011-03-01
even though you have marked this as solved, just thought I would add something I came across

[http://www.linuxbsdos.com/2010/12/08/how-to-dual-boot-linux-mint-10-and-windows-7/2/](http://www.linuxbsdos.com/2010/12/08/how-to-dual-boot-linux-mint-10-and-windows-7/2/)

using easyBCD to force the windows boot manager instead.  it's not as fancy as grub, but it should ensure that same issue won't happen again.  if you already knew about this program, my apologies :{D

---

