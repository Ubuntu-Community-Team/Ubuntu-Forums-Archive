---
title: "Apt-get Dist-upgrade Error"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-05-25
Can somebody please help me with this?

Using this command > sudo apt-get dist-upgrade everything went fine until it reached to unpack the linux-image then an error goes off.

> Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 102770 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
** dpkg: error processing** /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 **failed in buffer_write(fd) (10, ret=-1)**: backend dpkg-deb during `./lib/modules/2.6.27-7-generic/kernel/net/decnet/decnet.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
...
...
...
Updating /boot/grub/menu.lst ... done

Preparing to replace tzdata 2008h-2ubuntu1 (using .../tzdata_2009f-0ubuntu0.8.10_all.deb) ...
Unpacking replacement tzdata ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
mount: /usr is busy
E: Sub-process /usr/bin/dpkg returned an error code (1)What seems to be the problem? I'd appreciate it if anyone could help me out on this one. Thanks.

---

### Post by Gazneth on 2009-05-25
Is it possible that you are out of hard drive space this line seems to say that.

> dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.27-7-generic/kernel/net/decnet/decnet.ko': No space left on device

---

### Post by drs305 on 2009-05-25
You can run the following command to check your disk space:
```

df -Th 

```

Here is a link to a pretty comprehensive ubuntu wiki page on finding why your disk/partition is full if that is the problem.  Users with a small, separate /boot partition experience this problem, but if your system partition is full it can also happen:
[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by r3cht3r on 2009-05-26
> **drs305 said:**
> You can run the following command to check your disk space:
```

df -Th 

```Here is a link to a pretty comprehensive ubuntu wiki page on finding why your disk/partition is full if that is the problem.  Users with a small, separate /boot partition experience this problem, but if your system partition is full it can also happen:
[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Thanks for the link you gave.  I am now trying to figure out other ways to solve this problem although I have gotten rid of the problematic linux-image once I have upgraded but still whenever I do an update using the Update Manager still there shows 1 needed update to be installed.  And when I tried installing it it has the same problem, so now I just ignore it but I don't know if that is wise but I have already upgraded it so I guess it would be fine right?

@Gazneth  I don't think I am already out of HD space coz there's a lot more room in it but anyhow thanks.

---

### Post by r3cht3r on 2009-05-29
I tried to upgrade to Jaunty but still the problem persists but later on somehow when I was installing another application together with its dependencies of that application I was about to install, came a phrase "TO BE REMOVED" and it was the current linux-image that Jaunty came with.  Then, I tried the janitor to look for the unneeded files, then deleted those that are marked as no longer required together with linux-image-2.6.27-7-generic, then installed again  the current linux-image, and restarted. Up until now so far so good.

Thank you all.:)

---

