---
title: "Newbie question about duel boot"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Norie on 2009-05-30
I am new to ubuntu and I just downloaded Kubuntu 9.04.  After reading a little bit more, I see that I can duel boot. So my question is, do I have uninstall kubuntu and then try to set up the duel boot, or do I have the option to still be able to duel boot somehow.
I am not very savvy on all the technical computer talk so, if I sound ignorant or naive, please be patient with me.
Thanks in advance!

Norie

---

### Post by lisati on 2009-05-30
You can learn about dual-booting with Windows here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Norie on 2009-05-30
Yeah, I read those instructions _after_ I downloaded kubuntu 9.04. So now  I needed to know, can I set up a duel boot AFTER I've already installed kubuntu, or must I start from scratch.
thanks lisati for the response though:p

---

### Post by Jimmynemo2 on 2009-05-30
the original replier's link did give step by step for if you already have either one installed. Read the whole article, it helps. It's now here for your convenience.


Otherwise, you can use WUBI to install ubuntu with no computer knowledge needed at all, and it makes it literally as easy as it gets.



Installing Windows After Ubuntu

Normally when Windows is installed after Ubuntu the master boot record will be overwritten. This means that you would have to boot off a LiveCD and re-install grub. However, here is an alternative method:

   1. Create an NTFS partition for windows (using fdisk or whatever tool you are familiar with)
   2.

      Backup the boot sector e.g. dd if=/dev/hda of=/mbr.bin bs=512 count=1
   3. Install windows
   4. Boot into a LiveCD
   5. Mount your root partition in the LiveCD
   6.

      Restore the boot sector e.g. dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1
   7. Restart and Ubuntu will boot
   8. Setup grub to boot windows

---

### Post by Norie on 2009-05-30
ok thanks guys, I will do that. I guess I must have misread the part to duel boot after installation.  Wish me luck!!  Sorry for being such a noob:p

---

