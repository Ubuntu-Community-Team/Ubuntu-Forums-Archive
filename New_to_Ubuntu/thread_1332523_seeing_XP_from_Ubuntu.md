---
title: "seeing XP from Ubuntu"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by beanco on 2009-11-20
So, how can I see the partition which has XP on it while on the one with Ubuntu?

I have files in XP that I need access to.

To make things worse I actually do not know how to check which partition  which OS is on....

Thanks for the help.

Rob

---

### Post by Shazaam on 2009-11-20
If your drive is recognised by fstab/Ubuntu...
On your panel (taskbar) go to Places>your drive. It will be listed by size (one of mine reads 100 GB filesystem); click the icon and after you enter your user password at the prompt the drive/partition will mount and a file browser (nautilus) window will open.
Places>Computer should also list drives/partitions.

---

### Post by Locke_99GS on 2009-11-20
Another method, for the sake of completeness.
Lets assume you want to mount the "C:" drive of windows, usually this is /dev/sda1. 

Go root.
Confirm with *fdisk -l*.
Create mount point.
Mount drive to mount point.
Leave root.
List contents of new mount. Should look like the root of "C:" in Windows.

```

sudo su
fdisk -l
mkdir /mnt/winxp
mount /dev/sda1 /mnt/winxp
exit

ls /mnt/winxp

```

---

### Post by beanco on 2009-11-20
> **Shazaam said:**
> If your drive is recognised by fstab/Ubuntu...
On your panel (taskbar) go to Places>your drive. It will be listed by size (one of mine reads 100 GB filesystem); click the icon and after you enter your user password at the prompt the drive/partition will mount and a file browser (nautilus) window will open.
Places>Computer should also list drives/partitions.

Places>Computer shows only the ubuntu partition i think....

robi

---

### Post by beanco on 2009-11-20
> **Locke_99GS said:**
> Another method, for the sake of completeness.
Lets assume you want to mount the "C:" drive of windows, usually this is /dev/sda1. 

Go root.
Confirm with *fdisk -l*.
Create mount point.
Mount drive to mount point.
Leave root.
List contents of new mount. Should look like the root of "C:" in Windows.

```

sudo su
fdisk -l
mkdir /mnt/winxp
mount /dev/sda1 /mnt/winxp
exit

ls /mnt/winxp

```

this is what i got
```

root@ubuntu:/home/robi# mkdir /mnt/winxp
root@ubuntu:/home/robi# mount /dev/sda1 /mnt/winxp
root@ubuntu:/home/robi# ls /mnt/winxp
AUTOEXEC.BAT            DRIVERS       ntldr                      WINDOWS
Bootfont.bin            initfile.xml  pagefile.sys               wubildr
boot.ini                IO.SYS        Program Files              wubildr.mbr
CONFIG.SYS              MSDOS.SYS     RECYCLER
Documents and Settings  NTDETECT.COM  System Volume Information

```

guess i did sg wrong


robi

---

### Post by chea on 2009-11-20
Seems like you did everything right. That is the root of the "C:" drive.

---

### Post by lisati on 2009-11-20
> **beanco said:**
> Places>Computer shows only the ubuntu partition i think....

robi

I haven't done any tinkering with fstab on my laptop, and Places shows up not only the Vista partition, the recovery partition, and another small partition that seems to have something to do with Vista's setup.

---

### Post by Locke_99GS on 2009-11-20
Yessir, that worked. Now you can navigate to it from Nautilus by doing:
Places -> Computer -> File System -> mnt/ -> winxp/

---

### Post by Locke_99GS on 2009-11-20
```

sudo echo "/dev/sda1 /mnt/winxp ntfs defaults 0 0" >> /etc/fstab

```

To get it to mount automagically at boot.
From within nautilus, you can drag the winxp/ folder to the shortcut pane on the left side of nauilus to make it easy to get to.

---

### Post by nmaster on 2009-11-20
it looks like you're using wubi. if you are, then your XP files will be in "/host".

go to Places->Computer and look for /host

alternatively, open a terminal and type "cd /host"

---

### Post by beanco on 2009-11-20
> **Locke_99GS said:**
> ```

sudo echo "/dev/sda1 /mnt/winxp ntfs defaults 0 0" >> /etc/fstab

```

To get it to mount automagically at boot.
From within nautilus, you can drag the winxp/ folder to the shortcut pane on the left side of nauilus to make it easy to get to.


why would i want it to mount automagically (nice word, BTW)? I am still too n00bish to understand the logic behind such ideas....

```

Yessir, that worked. Now you can navigate to it from Nautilus by doing:
Places -> Computer -> File System -> mnt/ -> winxp/ 
```

actually, I found all that via MC but the documents I need seem to not be there.....

this is fun stuff, btw!

Neal, what's wubi?


thanks

Robi

---

### Post by beanco on 2009-11-20
Neal, you were right.... I guess I am using wubi... I just found /host and the files I could not find when tooling round /winxp were there..

so what exactly have i done with all your help folks?

yeah, that means i do not really know what mount means or wubi, or all this stuff... but I am having having...

robi

---

### Post by Locke_99GS on 2009-11-20
Wubi is the Windows installer for Ubuntu; It's not the proper way of install, and I don't know much about it. Apparently it provides the mountpoint /host to access windows root.

When you mounted the drive in my little example earlier, this is what happened:

sudo su = switch to the root user, since we would be performing multiple commands that require superuser rights.

fdisk -l = list all disks on the system to help determine which disk we actually wanted to mount

mkdir /mnt/winxp = we created a place in the filesystem to mount the new partition to. Everything in linux is a file, even other dirves. We gave it a place to sit.

mount /dev/sda1 /mnt/winxp = we logically attached the device located at sda1 (the first partition of the first physical drive) to the place we made for it.

exit = leave root shell, we don't need it anymore.

ls /mnt/winxp = list the contents of /mnt/winxp, to make sure that it both worked and was the proper drive.


the fstab stuff I mentioned earlier was just to have it mount the drive to that location everytime it booted, toehrwise you'd have to mount it manually every time. Of course, you don't need to do any of this since Wubi provided a mount point already for you (/host)

---

### Post by beanco on 2009-11-20
Locke,

thanks....

so wubi is not what I want actually!

Maybe  I will back up everything, uninstall, reinstall, etc...

or once I have ubuntu running to my liking, can I just get rid of XP and not worry about the whole reinstalling thing?

robi

---

### Post by Locke_99GS on 2009-11-20
Well, you obviously already have it running well enough through the Wubo install, in my opinion, I'd leave it as is until you become more comfortable with Linux and how it functions, the diferences between it and what you're accustomed to. A basic understanding of filesystem hierarchy and mount points is helpful when doing a full install the the proper way.

---

### Post by beanco on 2009-11-20
Locke,

I actually have an ubuntu only pc at home... been MS free for a couple of years and loving!

I did not have any real problems back then installing... however, on this lenovo thinkpad that I just got at work I was having problems with the install... kept getting wubi-bubi stuff adn that would not actually install... a co worker who is a ubuntu freak could not figure it out either... then I created a live CD, at least I thought I did and I thought I managed to install from that somehow.... honestly, this install was far more troublesome than the one I did years ago...

and I also installed ubuntu on pc at my second job!

so i probably know more than I think but not enough,,... actually, just enough to get myself in trouble.

robi

---

