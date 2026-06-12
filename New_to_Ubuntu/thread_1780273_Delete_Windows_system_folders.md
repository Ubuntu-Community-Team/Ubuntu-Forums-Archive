---
title: "Delete Windows system folders?"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by fotofill1969 on 2011-06-11
After installing Ubuntu 11.04, I found that I do not have the option of dual booting into windows any more. I do not consider this to be a problem, but I now have a lot of disk space claimed by an os that I do not want to use. Is it wise to just delete the windows system files or is there a better procedure? I have two hard drives installed: one split into equal volumes which hold the operating systems, and another with just one volume.

---

### Post by yetiman64 on 2011-06-11
> **fotofill1969 said:**
> After installing Ubuntu 11.04, I found that I do not have the option of dual booting into windows any more. I do not consider this to be a problem, but I now have a lot of disk space claimed by an os that I do not want to use. Is it wise to just delete the windows system files or is there a better procedure? I have two hard drives installed: one split into equal volumes which hold the operating systems, and another with just one volume.

Before you wipe out Windows, what exactly is the problem in booting Windows? Is it the 
Windows entry is missing from grub ? This may be fixable with a simple command in terminal,
```
sudo update-grub
```If you decide you don't mind losing Windows altogether, you can either use gparted from a live cd or install it into your ubuntu install and reformat the windows partition/s for use as a Linux storage drive. That way nothing from your Windows install will be left on the drive.

You can leave the Windows partition/s as NTFS just in case you decide to reinstall it later on, as Ubuntu can read and write to NTFS partitions. Though ext4 would be better performing under Ubuntu compared to NTFS. Note that Linux file/folder permissions are not supported on NTFS partitons but are set as mount options instead when NTFS is in use.

---

### Post by akand074 on 2011-06-11
You can just wipe and format the Windows partition and use the space for storage or something. It shouldn't be a problem. Only thing is Windows will be gone forever. If you have any intention to dual boot, I'm sure the problem can be troubleshooted, otherwise it shouldn't be a problem to just wipe it.

---

### Post by fabricator4 on 2011-06-11
> **fotofill1969 said:**
> After installing Ubuntu 11.04, I found that I do not have the option of dual booting into windows any more. I do not consider this to be a problem, but I now have a lot of disk space claimed by an os that I do not want to use. Is it wise to just delete the windows system files or is there a better procedure? I have two hard drives installed: one split into equal volumes which hold the operating systems, and another with just one volume.

Seems to be a common problem with the 11.04 installer.  To get Windows to appear in the grub boot menu run

```
sudo update-grub
```

To get rid of Windows altogether reformat the Windows partition.  You could format the partition as ext4 and use it as /home

There are better ways of setting up your system, but since the Ubuntu boot partition is probably on an extended partition I don't know an easy way of doing it.  You might consider starting with a fresh install with Ubuntu on a 15 or 20 GB primary partition, and use the rest for /home.  You'll also need a small swap partition.

Whichever way you go, back up your data first!

Chris

---

### Post by colin.p on 2011-06-11
Yup, open up gparted and nuke that rotten virus off your system.
Just kidding. As the above replies have said, you may be better off getting win to boot, you never know if there is that one win program you just gotta have, and it don't work worth a fiddler's $#@! in wine. If after awhile, and you never boot into win, and you actually really need that space, then remove it. 
I did the same thing a couple months ago, and don't miss win 7 at all, even though the year I have had this laptop, as a dual boot, I only booted into win a dozen times or so.

---

### Post by nosehat on 2011-06-11
You can use gparted to get the windows partition off your drive if that's what you really want to do.

Or you can mount that partition as is, as another drive within Ubuntu, allowing you to use the space as well as allowing you to access your old Windows files.

However, I personally would run update-grub like others are suggesting and try to fix your dual-boot.  If you've already got a Windows license for a machine, I'm a big fan of grub and dual booting.  For me an operating system is like a tool in your tool box, not a religion.  You don't need to throw away your old hammer just because you got a shiny new screwdriver.  ;)

---

### Post by AlphaLexman on 2011-06-11
> **colin.p said:**
> Yup, open up gparted and nuke that rotten virus off your system. Just kidding.
Technically, viruses attach to a host.

---

### Post by fabricator4 on 2011-06-11
> **AlphaLexman said:**
> Technically, viruses attach to a host.

... or can replace part of the code that gets loaded at boot time, making it buggy, unstable, and slow.

Yep, that sounds familiar.  :lolflag:

---

