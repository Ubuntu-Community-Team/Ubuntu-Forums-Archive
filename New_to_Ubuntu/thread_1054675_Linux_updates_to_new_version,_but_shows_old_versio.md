---
title: "Linux updates to new version, but shows old version number"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-29
I did an update recently, and I got 2.6.27-11, but at grub it still shows 2.6.27-9.

I looked up "linux headers" in synaptic, and it shows *-9 uninstalled and only *-11 installed, so I'm assuming everything's fine, only it's named wrong.

Can anyone confirm this, or did my update mess up?

---

### Post by ibutho on 2009-01-29
If you are sure you have a new kernel installed, try running "sudo update-grub" and see if that corrects your boot entries.

---

### Post by jpkotta on 2009-01-30
linux-headers has nothing to do with what shows up in grub.  You can always find out exactly what kernel is running with
```
uname -a
```

Have a look at the output of
```
dpkg -l "linux-image*" | grep ^i
```
(or the equivalent search in Synaptic).  It will show you exactly which kernels are installed.

---

### Post by adobrakic on 2009-01-30
> 
If you are sure you have a new kernel installed, try running "sudo update-grub" and see if that corrects your boot entries.


sudo update-grub gives me:

```

ado@ado-desktop:~$ sudo update-grub
[sudo] password for ado: 
Your /usr is broken, please fix it before call this wrapper!
ado@ado-desktop:~$

```

It seems that I have 2.6.27-11 installed, but it is still using 2.6.27-9. Is there a way to fix this? only -9 shows up in grub.

```

ado@ado-desktop:~$ uname -a
Linux ado-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
ado@ado-desktop:~$ dpkg -l "linux-image*" | grep ^i
ii  linux-image-2.6.27-11-generic              2.6.27-11.27                            Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.27-7-generic               2.6.27-7.16                             Linux kernel image for version 2.6.27 on x86
ii  linux-image-2.6.27-9-generic               2.6.27-9.19                             Linux kernel image for version 2.6.27 on x86
ii  linux-image-generic                        2.6.27.11.14                            Generic Linux kernel image
ado@ado-desktop:~$ 

```

---

### Post by ibutho on 2009-01-30
Post number two in this [thread]("http://ubuntuforums.org/showthread.php?p=6638380") will help resolve the update-grub problem.

---

### Post by Boomhauer on 2009-01-30
if update-grub doesnt add the kernel once you have followed ibutho's advice you can try this ugly fix

press alt+f2 and enter in ```
gksudo gedit /boot/grub/menu.lst
```

now go down to where your kernel entries are.  youll see something like (yours will be similar but different, that is ok)
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/memtest86+.bin
quiet
```

now copy the first two blocks of kernel entries and paste them right below where it says ## ## End Default Options ##.  now everywhere it says 2.6.27-9, change that 9 to an 11.  when you have done this, your list will look similar to this ```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		e68b2bb7-17f9-445b-b1b7-10d07ed8099a
kernel		/boot/memtest86+.bin
quiet
``` save the file and close it then reboot.  you should now be able to select and boot the new kernel.

---

### Post by adobrakic on 2009-01-30
worked perfectly, thanks

---

### Post by Tony Flury on 2009-01-30
The root cause of this problem maybe that when you installed the new kernel - it would prompt you to change the boot loader menu (i.e. GRUB). The default for that prompt seems to be leave the menu alone, so it would not have added 11 automatically - if you just clicked OK at that prompt.

At that prompt tere is an option (use maintainers version) which adds in the new kerel to grub, but as you have found out it is easy to manually add kernels at a later point after they are insalled.

---

