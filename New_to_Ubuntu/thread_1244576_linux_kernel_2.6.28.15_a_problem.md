---
title: "linux kernel 2.6.28.15 a problem"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by DarinB on 2009-08-19
I got linux headers for kernel  2.6.28.15 now things like firefox shut down constantly and screenlets won't come up i am using kernel 2.6.28.14 what should i do?
there was a problem getting it from the columbia server so i switched and it did download, but i don't know what to do or if the problem is .15 linux kernel or not didn't have too many issues before this????

---

### Post by DarinB on 2009-08-19
what is 10 acpi can not mount fs kernel panic??????

---

### Post by tgalati4 on 2009-08-19
Your message could be interpretted as:

At 10 seconds past boot, the acpi module is experiencing problems.  ACPI controls the power management of the hardware, sleep, hibernation, shutdown.

Can't mount the filesystem (fs) means that it either can't find it or there is a problem with the disk.

The kernel panic is when the kernel is left in a non-recoverable state.  A crash.  In this case, it can't find the file system (because it is not mounted).  A kernel without a file system is short-lived.

What version of Ubuntu are you running?  If it's Jaunty, then you should be running:

uname -a

2.6.28-11

Was there an update to 28-15 that you tried to install?

To recover, boot the live CD and post the contents (on the harddrive, probably /mnt/sda1/boot) of the boot directory:

tgalati4@tpad-Gloria7 /boot $ ls -la
total 12996
drwxr-xr-x  4 root root    4096 2009-07-25 23:29 .
drwxr-xr-x 21 root root    4096 2009-07-25 15:51 ..
-rw-r--r--  1 root root  529118 2009-04-16 20:41 abi-2.6.28-11-generic
lrwxrwxrwx  1 root root       1 2009-07-25 15:45 boot -> .
-rw-r--r--  1 root root   96795 2009-04-16 20:41 config-2.6.28-11-generic
drwxr-xr-x  2 root root    4096 2009-05-20 01:08 gfxmenu
drwxr-xr-x  2 root root    4096 2009-07-27 16:20 grub
-rw-r--r--  1 root root 7562212 2009-07-25 23:29 initrd.img-2.6.28-11-generic
-rw-r--r--  1 root root  128796 2009-03-27 10:15 memtest86+.bin
-rw-r--r--  1 root root 1456232 2009-04-16 20:41 System.map-2.6.28-11-generic
-rw-r--r--  1 root root    1074 2009-04-16 20:43 vmcoreinfo-2.6.28-11-generic
-rw-r--r--  1 root root 3501776 2009-04-16 20:41 vmlinuz-2.6.28-11-generic

Overwrite any mismatched files with ones from the live CD.  If your initrd.img is mismatched, then you will have to recreate it.

sudo dpkg-reconfigure linux-generic

should recreate it.

You can expect breakage when updating kernels or the graphics server (xorg).  I try to postpone those until I have time to fix the expected breakage.

---

### Post by LewRockwell on 2009-08-19
you describe having a problem with the updating process

this is most likely the problem

you may have received some error logs that might give an indication of how to proceed

.

---

### Post by DarinB on 2009-08-19
I am running 14 now i deleted 15 since it came today as a update. How can i go back to 11 I don't have it in my boot menu. and avoid kernel upgrades in the future

---

### Post by LewRockwell on 2009-08-19
> **tgalati4 said:**
> Your message could be interpretted as:

At 10 seconds past boot, the acpi module is experiencing problems.  ACPI controls the power management of the hardware, sleep, hibernation, shutdown.

Can't mount the filesystem (fs) means that it either can't find it or there is a problem with the disk.

The kernel panic is when the kernel is left in a non-recoverable state.  A crash.  In this case, it can't find the file system (because it is not mounted).  A kernel without a file system is short-lived.

What version of Ubuntu are you running?  If it's Jaunty, then you should be running:

uname -a

2.6.28-11

Was there an update to 28-15 that you tried to install?

automatic updates have proceeded through 13, 14, and most recently 15

.

---

### Post by LewRockwell on 2009-08-19
> **DarinB said:**
> I am running 14 now i deleted 15 since it came today as a update. How can i go back to 11 I don't have it in my boot menu. and avoid kernel upgrades in the future

if 14 runs ok(you state you're on it right now)...

why would you want to go all the way back to 11?

there are updates to the packages for a reason...

.

---

### Post by DarinB on 2009-08-19
OK so how do i go back to 11 add it in synaptic????

---

### Post by LewRockwell on 2009-08-19
> **DarinB said:**
> OK so how do i go back to 11 add it in synaptic????

again, if you are successfully running fourteen, why would you want to go all the way back to eleven?

.

---

### Post by DarinB on 2009-08-19
tgelati4 above said i should be running 11
and i do have crashes all the time firefox closes my panel crashes i never had that before jaunty???? I do remember that jaunty ran great for a while though maybe that was 11 when is rean good, pain in the ***, maybe i should go back to 11
or even hardy heron but that would be way too much work.
so what about 11

---

### Post by LewRockwell on 2009-08-19
> **DarinB said:**
> tgelati4 above said i should be running 11
and i do have crashes all the time firefox closes my panel crashes i never had that before jaunty???? I do remember that jaunty ran great for a while though maybe that was 11 when is rean good, pain in the ***, maybe i should go back to 11
or even hardy heron but that would be way too much work.
so what about 11

well...now you're referencing past problems and not what we were led to believe was your present trouble-call

if you've had problems with Jaunty and/or kernels and/or packages previously, could you please link to those previous trouble-calls that you placed on the ubuntuforum regarding those specifically

as far as eleven goes...you should be able to get any packages you want via Synaptic

.

---

### Post by tgalati4 on 2009-08-19
Here's the problem I have with minor kernel updates.  They don't always trigger a new grub entry.  So if there is a problem, you don't have a grub entry where you can select the previous kernel to reboot into.

I'm running 2.6.28-11-generic, and yes there are 13,14, and 15 updates (not sure where 12 went).  

If you can't boot and you have a Live CD of Jaunty, then chances are it will have 2.6.28-11 kernel that you can copy over to /boot on the hard disk and boot then upgrade back to 14.  If the older kernels already exist in /boot, then either modify your grub to point to those older kernels and reboot.

I'm not advocating staying at an older version of the kernel, but only if you have no other choice to get a working system.  I assume that Jaunty was working OK after first install--that would be the 2.6.28.11 kernel.

Not sure what was updated, but regressions do happen.

Edit:  I just checked synaptic.  I'm running 2.6.28.11.15 on a thinkpad t43p without issue.  Synaptic shows 2.6.28.15.20 is available to upgrade.  I think I'll sit tight until this is sorted out.



Linux Mint 7 (based on Jaunty) hides updates to the kernel and xorg for a reason.  It gives them a Level 5--meaning breakage likely.  Unless you know how to fix that breakage--drag your feet on installing them.  You have to weigh uptime vs some possible unknown gain by upgrading.

---

