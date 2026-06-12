---
title: "Put Ubuntu 10.10's boot loader to drive"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by apollothethird on 2010-11-17
I just used clonezilla to bring an Ubuntu installation to a larger hard drive that had been used with windows.  When I try to boot to the drive I get “Invalid or damaged Bootable partition”.

If I put the drive into a different computer I can mount it, chroot to it, and perform everything with it except boot to it.

I guess the simple question is how to install the Ubunto 10.10 boot loader to this drive.

Thanks in advance.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by sikander3786 on 2010-11-17
Please boot from a Live CD and post the output of bootinfoscript as per instruction here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It will give us a better idea of the situation and thus help you accordingly.

Wrap the output with proper code tags # from post menu.

---

### Post by LowSky on 2010-11-17
boot from a Live CD

Mount your Ubuntu partition from Places menu. 


open a temrinal

type (or paste):
```
mount | tail -1 
```

You should see output similar to this:

```
/dev/sda2 on /media/0d104aff-ec8c-44c8-b811-92b993823444 type ext4 (rw,nosuid,nodev,uhelper=devkit)
```

Note the designation for the disk /dev/sda which you will be using later, and the directory in /media. 

Use Tab Completion in Terminal to complete the path. Hitting the <TAB> key will automatically finish file names, directory locations, and other long or hard to type file names.

To make sure this is indeed the Ubuntu boot partition, run```
 ls /media/0d104aff-ec8c-44c8-b811-92b993823444/boot
```, substituting 0d104aff-ec8c-44c8-b811-92b993823444 with your volume's UUID from before, which should output something like this:

```
config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686
grub                     lost+found                   vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin
```

If what you have is not similar, unmount it and try another partition.

Now that everything is mounted, we just need to reinstall GRUB by specifying the correct directory and the correct drive name:

```
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
```


I copied this straight form here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by apollothethird on 2010-11-17
> **LowSky said:**
> boot from a Live CD

Mount your Ubuntu partition from Places menu. 


open a temrinal

type (or paste):
```
mount | tail -1 
```

You should see output similar to this:

```
/dev/sda2 on /media/0d104aff-ec8c-44c8-b811-92b993823444 type ext4 (rw,nosuid,nodev,uhelper=devkit)
```

Note the designation for the disk /dev/sda which you will be using later, and the directory in /media. 

Use Tab Completion in Terminal to complete the path. Hitting the <TAB> key will automatically finish file names, directory locations, and other long or hard to type file names.

To make sure this is indeed the Ubuntu boot partition, run```
 ls /media/0d104aff-ec8c-44c8-b811-92b993823444/boot
```, substituting 0d104aff-ec8c-44c8-b811-92b993823444 with your volume's UUID from before, which should output something like this:

```
config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686
grub                     lost+found                   vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin
```

If what you have is not similar, unmount it and try another partition.

Now that everything is mounted, we just need to reinstall GRUB by specifying the correct directory and the correct drive name:

```
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
```


I copied this straight form here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks, Guys.  It worked like a charm!  Grub is great... Linux is great!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

