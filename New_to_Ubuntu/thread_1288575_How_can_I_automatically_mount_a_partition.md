---
title: "How can I automatically mount a partition?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by SonicMonkey on 2009-10-11
As you gained from the thread's title, I want to know how to automatically mount a hard drive when I boot. I'm using Linux Mint 7 and I have a whole bunch of links/shortcuts set up to get into some of the files I have within the Windows part of my hard drive. As soon as I boot into Gloria, all these links are broken and I have to go into computer and open the drive all my windows stuff is on. How can I get my computer to do this for me every time I go into Gloria?

Thanks in advance,
Dan

---

### Post by N4zgu1 on 2009-10-11
You have to edit fstab and add the partition that  you want to be mounted

first open fstab

```
sudo gedit /etc/fstab
```

then add the partition, first the device name, then the mounting point, then the type, then the mount options and Im not sure what the double zero means but you have to add them.

here is how I added my ntfs partion:

/dev/sda4	/media/windows	ntfs	auto,user,exec,rw,sync	0 0

and here is a tutorial

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by Junkieman on 2009-10-11
What N4zgu1 said :)

The two last options are:

Dump: Dump field sets whether the backup utility dump will backup file system. If set to "0" file system ignored, "1" file system is backed up.

Fsck order: Fsck order is to tell fsck what order to check the file systems, if set to "0" file system is ignored.

These are from the [fstab Howto thread]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by SonicMonkey on 2009-10-11
Thanks a bunch, but I'm still skeptical.

I changed the mount point to '/media/"windows"'. Is this the same as where you have windows in your example?

---

### Post by cariboo on 2009-10-11
IF you want your links to work, mount the ntfs partition the same way you do in Mint 7. I would suggest you mount your Mint 7 partition and compare /etc/fstab on both versions.

---

### Post by SonicMonkey on 2009-10-11
Problem solved, thanks guys!

I'd also like to include that I used the command:
```
sudo fdisk -l
```
To find out the file system to put in the '/dev/sda_' spot. That was the hard part.

---

