---
title: "loading kernal"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by shadowlands on 2010-02-14
XP Starting a new threat because the other one was way to long with out a solution

the kernel did not load and I am using wubi.
What I know:
sh: grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disks ro

error: file not found

sh: grub> sudo update-grub 

error unknown command 'sudo'

sh: grub>ls
(hd0) (hd0,5) (hd0,1)

sh: grub> set
color_highlight=
color_normal=
pager=
perfix=(hd0,1)/boot/grub
root=(d0,1
show_panic_message=true

the file wubi file that you can down load and copy to the c drive to replace the messed up file did not work.

---

### Post by Temposs on 2010-02-14
I recommend that you should reinstall without Wubi. Wubi has issues...

You should either dual-boot or install Ubuntu with Virtualbox. Both methods are recommended over Wubi. Wubi is for those who cannot take any messing around with booting or other complications(assuming Wubi works). They just want to install Ubuntu like a Windows program and be done with it... Given that you're talking about the kernel and running terminal commands, I think that you should not use Wubi, unless your intent is to use it for testing to give feedback to the developers.

---

### Post by shadowlands on 2010-02-14
ok > **Temposs said:**
> I recommend that you should reinstall without Wubi. Wubi has issues...

You should either dual-boot or install Ubuntu with Virtualbox. Both methods are recommended over Wubi. Wubi is for those who cannot take any messing around with booting or other complications(assuming Wubi works). They just want to install Ubuntu like a Windows program and be done with it... Given that you're talking about the kernel and running terminal commands, I think that you should not use Wubi, unless your intent is to use it for testing to give feedback to the developers.

---

