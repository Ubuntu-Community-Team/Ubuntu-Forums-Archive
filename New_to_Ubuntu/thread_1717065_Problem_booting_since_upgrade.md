---
title: "Problem booting since upgrade"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by jeannot_unbu on 2011-03-29
I am now getting an error message when I boot my laptop.

A lot of coding, last line is:-

udevd -work [70] '/sbin/blkid -o udev -p /dev/sda1' unexpected exit with status 0 x000b

I then press enter and it goes to a line saying:-

(initramfs)

I then type reboot, it reboots ok and get different options to boot from the selected OS:

Ubuntu, with Linux 2.6.35-28 - generic
Ubuntu, with Linux 2.6.35-28 - recovery mode

Ubuntu, with Linux 2.6.35-27 - generic
Ubuntu, with Linux 2.6.35-27 - recovery mode

etc. I then select the ..27 - generic and its goes in normally.

Anyone know if I could fix that problem, thanks :o

JC

---

### Post by philinux on 2011-03-29
Try the .28 recovery mode.

---

### Post by jeannot_unbu on 2011-03-29
> **philinux said:**
> Try the .28 recovery mode.

Thanks, did that. Starts doing something and then I just get blinking cursor and nothing seems to be happening, how long am I supposed to wait?

JC

---

### Post by irv on 2011-03-29
Have you tried "Ubuntu, with Linux 2.6.35-27 - generic"?
Going back to the kernel before the update.
If it boots that there was a problem with the updated kernel.
If there was then you could try re-installing it. It should be in the package manager.

---

### Post by philinux on 2011-03-29
> **jeannot_unbu said:**
> Thanks, did that. Starts doing something and then I just get blinking cursor and nothing seems to be happening, how long am I supposed to wait?

JC

I was hoping you'd get more info on the error.

[edit]

Post back what these two commands show.

```
sudo blkid

Then

cat /etc/fstab
```

I'm pretty sure all will be ok as the previous kernel boots ok.

---

### Post by jeannot_unbu on 2011-03-29
Have you tried "Ubuntu, with Linux 2.6.35-27 - generic"? Yes this work ok, what annoys me is that boot the pc and then I have to reboot and select this option

sudo blkid returns

/dev/sda1: UUID="170c1f77-d0c1-4bec-a9bb-25ef958654f4" TYPE="ext4" 
/dev/sda5: UUID="dc63bc8a-6eef-4aee-a0b1-ca7628f6e07d" TYPE="swap" 

The other command returns

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=170c1f77-d0c1-4bec-a9bb-25ef958654f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dc63bc8a-6eef-4aee-a0b1-ca7628f6e07d none            swap    sw 

Thanks
JC

---

### Post by philinux on 2011-03-29
> **jeannot_unbu said:**
> Have you tried "Ubuntu, with Linux 2.6.35-27 - generic"? Yes this work ok, what annoys me is that boot the pc and then I have to reboot and select this option

sudo blkid returns

/dev/sda1: UUID="**170c1f77-d0c1-4bec-a9bb-25ef958654f4**" TYPE="ext4" 
/dev/sda5: UUID="**dc63bc8a-6eef-4aee-a0b1-ca7628f6e07d**" TYPE="swap" 

The other command returns

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=**170c1f77-d0c1-4bec-a9bb-25ef958654f4** /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=**dc63bc8a-6eef-4aee-a0b1-ca7628f6e07d** none            swap    sw 

Thanks
JC

As expected the block id's match so no worries there. Stumped to be honest.

I would as a work around for now, select the older kernel to boot from the grub menu at start up.

---

### Post by jeannot_unbu on 2011-03-29
> **philinux said:**
> As expected the block id's match so no worries there. Stumped to be honest.

I would as a work around for now, select the older kernel to boot from the grub menu at start up.

OK thanks, maybe it will fix itself with the next upgrade

JC

---

### Post by irv on 2011-03-29
Go to the startup manager and set it to boot this kernel until the next update.
[ATTACH]187481[/ATTACH]

---

### Post by philinux on 2011-03-29
> **jeannot_unbu said:**
> OK thanks, maybe it will fix itself with the next upgrade

JC

Could fix itself with next kernel.

---

### Post by jeannot_unbu on 2011-03-29
> **irv said:**
> Go to the startup manager and set it to boot this kernel until the next update.
[ATTACH]187481[/ATTACH]

Must be stupid but can't find the startup manager, I have a Startup Applications, is this what you mean?
Thanks
JC

EDIT: OK got it now, i thought it was installed automatically, had to install it and change the kernel, thanks for that
JC

---

### Post by irv on 2011-03-29
> **jeannot_unbu said:**
> Must be stupid but can't find the startup manager, I have a Startup Applications, is this what you mean?
Thanks
JC

EDIT: OK got it now, i thought it was installed automatically, had to install it and change the kernel, thanks for that
JC

Sorry! I take to much for granted, I thought you might have it installed. It is a nice touch to a GUI interface for setting the boot-up. I know you can do it in the terminal but I like GUI apps. Must be a thing from using windows to long. I go back and forth all the time. That's terminal/GUI.

---

