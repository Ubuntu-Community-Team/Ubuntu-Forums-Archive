---
title: "Won't boot any more...I am at a loss"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by gqqser on 2010-02-16
I did a clean install of ubuntu 9.10 Remix on a Acer Aspire One with an 8 GHz SSD. The install went fine and everything was working for about a week and a half. Then one night I turned on the netbook and it went directly to the grub...it hadn't done that before, I had several choices;

Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Memory tests seem to indicate that every thing is fine.

If I select the "Ubuntu, Linux 2.6.31-17-generic" option, the logo flashes for a second then i get the following;

[COLOR=RoyalBlue]*mount: mounting /dev/disk/by-uuid/3a61e7a7-9404-4892-a04f-5646af940c83 on /root failed: Invalid argument*

mount: mounting /sys on /root/sys failed: no such file or directory

mount: mounting /dev on /root/dev failed: no such file or directory

mount: mounting /sys on /root/sys failed: no such file or directory

mount: mounting /proc on /root/proc failed: no such file or directory
Target file system doesn't have /sbin/init
No init found. Try passinginit= bootarg

BusyBox v1.13.3.(Ubuntu 1:1.13.3-ubuntu?) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_[/COLOR]

If I try the "recovery" mode, I get a long list of items really fast but I end up in the same place.

If I try the third option the logo (which looks like the wheel) flashes and fades and the screen goes blank and there it sits, nothing on the screen.

If I choose the (recovery) mode of this option, I get the same results as when i try to boot from the recovery mode up above.

I was told to try and reinstall but use 9.04 (jaunty jackalope) Remix. I really didn't have anything on it so I figured I would give that a try...I got a different menu and I selected install but it wouldn't install or format the drive.

I really do not know what to do..it won't even let me install windows xp on it...could someone please help a newbie out here

Thanks

---

### Post by bodhi.zazen on 2010-02-16
Sounds as if it may be a hard drive failure.

Boot a live CD (use unetbootin) and take a look at the hard drive.

---

### Post by gqqser on 2010-02-16
Man I was hoping that wasn't brought up...I was thinking it myself...but i don't know how to check this in linux. I know in windows it a chkdsk but I do not know how to do this in linux.

---

### Post by undecim on 2010-02-16
@bodhi.zazen: If it were a complete drive failure, you wouldn't be getting GRUB at all. Though this is a solid state drive, so some traditional HDD wisdom won't apply here. Maybe it's just a bad sector or two? 

Someone correct me if I'm wrong, but shouldn't the root FS be mounting to / rather than /root? Or is this some trick that initramfs uses early in the boot sequence?

@gqqser: You should try looking at your /etc/fstab file from a live CD. (post the contents of that file here)

I also have two questions: 

1: What message did you get when you tried to format the drive?

2: Since the AA1 doesn't have a CD drive, I assume you are installing from a thumb drive, USB hard drive, or USB CD drive. All of those may be treated as a hard drive. Are you sure that you are trying to install to your internal SSD and not your USB drive?

---

### Post by bodhi.zazen on 2010-02-16
> **gqqser said:**
> Man I was hoping that wasn't brought up...I was thinking it myself...but i don't know how to check this in linux. I know in windows it a chkdsk but I do not know how to do this in linux.

Linux uses fsck

```
fsck -y /dev/sdxy
```

where /dev/sdxy is the partition to check (/dev/sda1).

---

### Post by gqqser on 2010-02-16
> **undecim said:**
> @gqqser: You should try looking at your /etc/fstab file from a live CD. (post the contents of that file here)

I also have two questions: 

1: What message did you get when you tried to format the drive?

2: Since the AA1 doesn't have a CD drive, I assume you are installing from a thumb drive, USB hard drive, or USB CD drive. All of those may be treated as a hard drive. Are you sure that you are trying to install to your internal SSD and not your USB drive?

I have not been sucessful using a Live CD. I have been using unetbootin and i tried both 910 and 9.04 Remix but I keep getting the images in Picture for starters and then when i select OEM installation like in picture1 I get a lot of information scrolling very fast and picture2 is where it leaves me.

---

### Post by bodhi.zazen on 2010-02-16
Which CD (iso) are you using to make a bootable USB with ? The alternate CD ? That will not work, you need the Desktop CD.

If you are using the Desktop CD, something went wrong with unetbootin. Wipe / reformat the USB and run unetbootin again.

If you are still having problems, check the md5sum of the iso.

---

### Post by Silver40mm on 2010-02-16
If you have a copy of 9.10, boot it.

Once it's booted, go to System > Administration > Disk Utility. You can perform a health check of your hard drive. It should tell you if it's failed or not. :D

---

