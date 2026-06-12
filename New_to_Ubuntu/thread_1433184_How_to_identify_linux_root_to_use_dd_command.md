---
title: "How to identify linux root to use dd command"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by XeviousR on 2010-03-18
I am one small issue away from joining the Ubuntu community...
[B]
How do I identify the path of my linux root partition?  Do I use the /dev/sd# or mounted name?[/B]

Background: I have installed Ubuntu and installed the Grub boot loader to the same partition.  I did this because I want to use Windows Boot Loader to launch Ubuntu (my preference).  I'm following [instructions found here]("http://forums.techarena.in/operating-systems/1241600.htm") to add a line to my boot.ini file to launch Ubuntu.  My problem is, I am having trouble with the dd command from terminal.  I am using the code as follows...

```
dd if=/dev/sda# of=/media/Data/ubuntu.bin bs=512 count=1
```... where # is the number of my drive.

I know I have the /media/Data path correct because I have been able to write the file to my NTFS drive and recover it in Windows, but the if= path to linux root must not be right because the .bin file I'm writing is no good.  This seems very simple but I'm overlooking something.  Do I need to mount linux root?  I am booting from Live CD, but again, Ubuntu is already installed to a partition.  

I've tried to interpret gparted info on my drives, but I must be interpreting it wrong.  Any ideas?

---

### Post by spiderbatdad on 2010-03-18
i believe you have the if and of backwards?

EDIT: brain cramp you have the order right. What is the exact error?

---

### Post by spiderbatdad on 2010-03-18
```
sudo fdisk -l
``` from the live cd to locate /dev/sdaX of the linux file system.

---

### Post by XeviousR on 2010-03-18
No error.  It makes the ubuntu.bin file as requested, but the file size is only 512 bytes (tiny!).  I tried using it in the Windows Boot Loader anyway and I just get a blinking dash.  Since it is writing the file, I can only presume that my error is in the directory I am pointing to the linux root.

Okay, I'm showing my newb.  BS=512 forces the size to 512 bytes.  Still, it seems that the .bin file generated is not correct.

---

### Post by XeviousR on 2010-03-18
> **spiderbatdad said:**
> ```
sudo fdisk -l
``` from the live cd to locate /dev/sdaX of the linux file system.

Very nice.  Thanks!  I'll try it.

---

### Post by srs5694 on 2010-03-18
A better way is df:

```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             6.0G  635M  5.4G  11% /

```

There will be other entries, but the one you want is probably the one with "/" in the "Mounted on" column. This unambiguously identifies the root filesystem. If you see a separate "/boot" partition, though, you may need that one instead.

The fdisk command that spiderbatdad suggests will unambiguously identify the Linux root filesystem if and only if you used a single partition for OS installation. Although such a configuration seems to be common among new Ubuntu users, it's not the only way to install Ubuntu.

---

### Post by bodhi.zazen on 2010-03-18
Or mount ...

But , FYI, you should run your backup, dd, on an unmounted partition. For your root partition this means booting a live CD (or an alternate OS).

---

### Post by srs5694 on 2010-03-18
> **bodhi.zazen said:**
> But , FYI, you should run your backup, dd, on an unmounted partition. For your root partition this means booting a live CD (or an alternate OS).

All the OP needs is the first sector, which shouldn't be changing unless GRUB is being re-installed at that very moment. Thus, there's no real need to reboot into a recovery disc environment to do this.

---

### Post by bodhi.zazen on 2010-03-18
> **srs5694 said:**
> All the OP needs is the first sector, which shouldn't be changing unless GRUB is being re-installed at that very moment. Thus, there's no real need to reboot into a recovery disc environment to do this.

Ah, I missed that.

---

### Post by spiderbatdad on 2010-03-18
I don't believe running df from a live environment will display the partitions for you...likely something like aufs.
Whereas fdisk will. And yes it assumes the user knows whether he/she has multiple linux / filesystems and on what partitions they might be.

---

### Post by srs5694 on 2010-03-18
> **spiderbatdad said:**
> I don't believe running df from a live environment will display the partitions for you...likely something like aufs.
Whereas fdisk will. And yes it assumes the user knows whether he/she has multiple linux / filesystems and on what partitions they might be.

I missed that the OP was using a live CD. You're correct that df displays only mounted partitions, so it wouldn't work in this case unless the OP mounted the Linux install partition(s) first, but of course that would require knowing which partition(s) they were -- a chicken-and-egg problem. OTOH, if Linux is bootable, the system could be rebooted into Linux and df *would* work for this task.

---

### Post by XeviousR on 2010-03-19
> **spiderbatdad said:**
> ```
sudo fdisk -l
``` from the live cd to locate /dev/sdaX of the linux file system.
[B]
IT WORKED![/B]

Now I could of swore I tried this last night.  The sudo fdisk -l (that is an L by the way) worked great.  Then I just used my dd command.  It performed the same as last night, but I checked the output file and it was definitely different than last time.  Not sure what switch I made.  But I'm in business now.

Thanks, Your newest Ubuntu user!  yay!

---

