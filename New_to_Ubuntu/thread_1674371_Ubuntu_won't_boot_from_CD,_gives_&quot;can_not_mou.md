---
title: "Ubuntu won't boot from CD, gives &quot;can not mount&quot; error"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by windsorwindsor1 on 2011-01-23
I tried to boot up Ubuntu 10.10 from the CD, the Ubuntu logo screen comes up, then it stops and gives me this error message:

(initramfs) mount: mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on filesystem.squash.fs

Then I get a Busybox command shell with the prompt

(initramfs)

I tried it again with Ubuntu 10.4 and had the same problem. I can't figure out what's causing this or how to get it to resume booting. My computer is an Acer laptop with a Pentium T4500 processor, and I'm trying to Dual boot with Windows 7. I've used Xubuntu 7.04 on my older computer for a few years, this is the first problem I've had installing Ubuntu.

---

### Post by bioterror on 2011-01-24
Did you check MD5sum of the .iso -image file?
I would also suggest to try this "Check disc for defects" from the boot menu.

One possible thing is that your cd/dvd drive's optical lens is dirty or something.

---

### Post by windsorwindsor1 on 2011-01-24
Oh no... Now I'm having a major problem.

I tried to install Ubuntu with Wubi instead, then I tried to migrate it to a an ext4 partition (which Fedora was installed on) using a script I found on the forums [here]("http://ubuntuforums.org/showthread.php?t=1519354")

The script said the partition I wanted to move Ubuntu to was not empty, so I opened the DISK partition editor in Wubi and deleted the Fedora partition. When I tried to reformat it, it gave me an error, and appeared as if nothing had happened.

I then shutdown and rebooted into a CD that had Gnome partition editor on it, and it said my whole disk was unallocated.

I rebooted to the hard disk and got a basic Grub command prompt. I can't get to Windows, or even the Windows system restore partition to get it back to factory settings and start over.  This is a brand new laptop, what happened? Why did the DISK partition editor delete my whole partitioning table, when I told it to only delete the one partition? Is there a way to get it back?

---

### Post by windsorwindsor1 on 2011-01-25
Well after a late night and early morning, I got my system back to normal. I used the live CD Gparted, and used *testdisk*  to get the partitions back, which took a few tries and a few hours. Then Gparted could see the partitions but it still wouldn't boot.

This morning I installed Cruchbang linux where Fedora was, and it saw my Windows partitions and put them on the GRUB menu. Problem solved.

Now that my computer will actually boot, I'm not gonna mess with it for now. I'll probably try Ubuntu again when 11.04 comes out.

---

