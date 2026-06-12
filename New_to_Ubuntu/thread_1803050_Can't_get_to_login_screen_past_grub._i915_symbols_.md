---
title: "Can't get to login screen past grub. i915 symbols error"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by Jun392 on 2011-07-12
Hi I'm pretty new at this stuff and I pretty much wanted to switch because windows botched. So my problems is that after installing ubuntu 11.04 from a livecd or alternate live cd, I can't seem to get to the login screen. Booting from grub, Ubunti, with Linux 2.6.38-8-generic, with quiet splash taken out of the linux line,I get to

Begin: Running /scripts/init-bottom // done.

And then it just kinda hangs with the blinking cursor at loading.

Booting from recovery mode, I get a bit further and I end up with the "failed to get i915 symbols, graphics turbo disabled."

Now I know there are a few threads already online and that it tells you to run 
sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf
but how do I even get to a terminal from grub or anything. Btw I'm a complete nub and I've literally spent hours trying to fix this. If anyone can just point me in the right direction that would be great thanks.

---

### Post by wildmanne39 on 2011-07-12
> **Jun392 said:**
> Hi I'm pretty new at this stuff and I pretty much wanted to switch because windows botched. So my problems is that after installing ubuntu 11.04 from a livecd or alternate live cd, I can't seem to get to the login screen. Booting from grub, Ubunti, with Linux 2.6.38-8-generic, with quiet splash taken out of the linux line,I get to

Begin: Running /scripts/init-bottom // done.

And then it just kinda hangs with the blinking cursor at loading.

Booting from recovery mode, I get a bit further and I end up with the "failed to get i915 symbols, graphics turbo disabled."

Now I know there are a few threads already online and that it tells you to run 
sudo echo "softdep intel_ips pre: i915" > /etc/modprobe.d/intel-ips-dep-i915.conf
but how do I even get to a terminal from grub or anything. Btw I'm a complete nub and I've literally spent hours trying to fix this. If anyone can just point me in the right direction that would be great thanks.Hi, have a look at this link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
it should allow you to boot into ubuntu so you can fix your problem. Also this is how to boot into recovery.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Jun392 on 2011-07-12
So I tried nomodeset, and acpi_osi= and I get a blinking cursor. When I tried taking off nomodeset and leaving just quiet splash, I still get the 

"failed to get i915 symbols, graphics turbo disabled" error. 

I can get to recovery mode, but I end up at the same line. 

Forgive me, I forgot mention that I have already installed ubuntu 11.04 on this computer and upon the restart after the installation these problems occurred.

---

### Post by wildmanne39 on 2011-07-12
Hi, there are things we can try but you have to be able to get into recovery mode. When you see the screen with the kernels is there not a line there that says recovery mode? If so click it then choose recovery with root and networking.

---

### Post by Jun392 on 2011-07-12
Hm, thanks for being so patient with me. Uh, well when I turn the laptop on I get to the grub menu, I guess it would be called. Then there's the option of recovery mode under Ubuntu, with Linux 2.6.38-8 generic (recovery mode). And That's all I really see. When I hit enter with the recovery mode selected, it loads for a bit with the black screen and white letters and stop at the

"failed to get i915 symbols, graphics turbo disabled" and refuses to go any further. It just hangs there. 

When I hit e with the recovery mode selected, it says

 linux /boot/vmlinuz-2.6.38-8generic root=UUID=76de32c6-c4df-4d47-a658-966367143aeaa ro single nomodeset echo 'Loading initial ramdisk ... "
initrd /bot/initrd.img-2.6.38-8-generic

Idk if that'll help but I'm trying to give you as much as information as possible if it makes things easier.

---

### Post by wildmanne39 on 2011-07-12
Hi, ok if you can not get into recovery mode I am out of ideas, I hope someone else will pop in here with an idea, but as far as I know you will need to do a fresh reinstall. 

There are some boot disk programs but I have not used them and I do not know if they have good instructions for them on there download site,because they are all command line programs.

---

### Post by Jun392 on 2011-07-12
So i reinstalled and now it won't even load to grub. It just sits at the black screen with blinking cursor :/ Thanks for trying tho, I appreciate it. Hopefully someone will kno how to fix this

---

### Post by wep940 on 2011-07-12
First, try editing the boot line in the grub menu at boot by adding vga=772 then see if you get least to the recovery console.  If so, try again with a normal remembering to edit the boot line to include vga=772.  There also at least used to be a nomodeset for the i915 - something like i915-modeset=no or some such thing.  I'll go looking for that to see if it's still valid.
 
Post back what happens with  the vga=772 attempts.

---

### Post by wep940 on 2011-07-12
OK, just nomodeset used to be for nvidia cards.  For the 915, you should try this on the editing of the boot line:
 
add i915.modeset=1 and try booting.
 
if that doesn't work, try i915.modeset=0 instead.
 
Post back with what happens.

---

### Post by rushikesh988 on 2011-07-12
Reinstall os ....

---

### Post by wep940 on 2011-07-13
> **rushikesh988 said:**
> Reinstall os ....
 
Did you read the OP's last post before you posted this??

---

### Post by Jun392 on 2011-07-13
Okay I did a clean reinstall and from grub did the vga=772 but not the i915 thing. And now it just skips the grub menu and straight into ubuntu. So now I can log in which is very good news! BUT for some reason it won't pick up wireless Internet .

---

### Post by wildmanne39 on 2011-07-13
> **Jun392 said:**
> Okay I did a clean reinstall and from grub did the vga=772 but not the i915 thing. And now it just skips the grub menu and straight into ubuntu. So now I can log in which is very good news! BUT for some reason it won't pick up wireless Internet .Hi, start a new thread for that issue and when you are satisfied that you booting issue is fixed would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Jun392 on 2011-07-14
Okay no problem, I'll get on that asap.

---

### Post by wep940 on 2011-07-14
Do you know how to update the config files for grub and run update-grub so that the change is permanent instead of editing the boot line each time you boot?

---

