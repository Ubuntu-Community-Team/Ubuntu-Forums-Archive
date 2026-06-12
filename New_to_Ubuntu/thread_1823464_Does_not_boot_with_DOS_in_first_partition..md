---
title: "Does not boot with DOS in first partition."
date: 2011-08-12
forum: New to Ubuntu
---

### Post by machdohvah on 2011-08-12
OK, so I erased the computer and started over with DOS 6.22 iso on a CD. Installed it correctly except that It already failed to boot on C:. Continued to install Ubuntu 10.10 with a fresh iso for that on a CD. Completing that, I was able to boot on the DOS CD, but not on the first partition that I just created. Is there a way that I can create a boot menu that reads:

1. Boot to DOS 6.22
2. Boot to Unbuntu 10.10

The thing is, though I am able to boot using the CD, this disallows me to ever access any changes that I might want to make to the configuration. I am only able to effect my configuration changes if it would simply boot on the first partition like a good boy. So, I have downloaded dosbox and had to use that to access anything that needed more memory than just the basics. I need to create such a menu that allows me to boot on the first partition.

---

### Post by lkraemer on 2011-08-12
If you boot from the DOS 6.22 CDR, can you then locate sys and do:
```

sys c:

```
That should make c: bootable.  You will also need command.com and
config.sys, autoexec.bat, and other files there, along with the hiden
system files.  I'd expect there would also need to be a C:\DOS subdirectory
with all the files from the CDR copied there.  Also, your frist partition
(C:\) will need to be fat 16 or fat 32.

Once that is booting, if you create the Ubuntu partitions, and install
Ubuntu, you should have the grub menu for selecting DOS or Ubuntu.

lk

---

### Post by jtarin on 2011-08-12
[http://www.computerhope.com/syshlp.htm]("http://www.computerhope.com/syshlp.htm")DOS sys command

---

### Post by haqking on 2011-08-13
Out of interest why do you want to run DOS at all ?

There is no requirement for you to have Dos to run and install Ubuntu ?

Why not install Ubuntu and if you really need Dos for something use a virtual machine ?

See here for how to set it up, it is pretty easy.

[http://ubuntuforums.org/showthread.php?t=1598266](http://ubuntuforums.org/showthread.php?t=1598266)

---

