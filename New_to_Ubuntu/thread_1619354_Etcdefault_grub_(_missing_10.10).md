---
title: "Etc/default grub ( missing 10.10)"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Robbyx on 2010-11-11
I am trying to create a new grub file as I do not have one  in the default folder. I want to do it from the live CD. How do I change the user so that I can have write access to the folder (on the HD)?

Could someone post the contents of the grub file that should be in etc/default.

I have a similar problem with backing up the whole of the /etc directory. I tried copying it from within the live CD and I was told I did not have permission to do it.

This is all preparatory to a clean install, although I would like to repair my system with the grub option before I have to do the clean install. I might get the system working without having to do a clean install.

Robin

---

### Post by sandyd on 2010-11-11
> **Robbyx said:**
> I am trying to create a new grub file as I do not have one  in the default folder. I want to do it from the live CD. How do I change the user so that I can have write access to the folder (on the HD)?

Could someone post the contents of the grub file that should be in etc/default.

I have a similar problem with backing up the whole of the /etc directory. I tried copying it from within the live CD and I was told I did not have permission to do it.

This is all preparatory to a clean install, although I would like to repair my system with the grub option before I have to do the clean install. I might get the system working without having to do a clean install.

Robin
```
gksudo nautilus
```

---

### Post by oldfred on 2010-11-11
When in liveCD you may still need to do sudo. Just do not back up /etc as that probably is the liveCd's version. You have to look in media/etc.

You should be able to chroot into your system and run a full set of repairs. 

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc


Any additional updates that may be required.

---

### Post by Robbyx on 2010-11-13
Thank you for your response. I did a clean install but kept /home on a separate partition. 

**Child processes not being found **

I now have a number of applications that  can not be launched because child process can not be accessed.

Example:

> Failed to execute child process "/usr/bin/kdirstat" (No such file or directory)

Before doing the clean install I backed up all of /etc/

What should I bring back into the fresh install's /etc/   ?

[B]Repository recovery
[/B]
I had intended to recover sources.list.d

Is it safe to do it without bringing in other associated files?

[B]Permissions and owners
[/B]
I am in a muddle as to who should own a file in areas such as /etc/ and what permissions they should have attached to them. Have you seen any guidance on this?

Robin

---

### Post by philinux on 2010-11-13
When you did the clean install did you mark / to be formatted?

If not I would reinstall.

---

### Post by Robbyx on 2010-11-13
> **philinux said:**
> When you did the clean install did you mark / to be formatted?

If not I would reinstall.

Yes, I did opt for formatting.

Do you have any comments on my other points?

Robin

---

### Post by oldfred on 2010-11-13
I have had issues with old configuration files not being correct. The only reason I save files from /etc is where I have made custom settings and only sometimes have I still needed those in a new version. I think if you attempt to copy everything back from /etc you will be missing many new maintainer settings and have huge problems.

Also sources list is for my reference where I may have added something non-standard. Most of the listings are by version, so you have to manually edit just about every line. You may just want to review and if you had added something custom add & edit that one or two lines.

Example
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) [COLOR=Red]lucid[/COLOR] main restricted

---

### Post by cantinflas09 on 2011-03-02
ok i have grub file . but there is nothing there . . i think i deleted it on accident or i don't know what happen to it . . .helP? . . first time posting i usually don't need any help cuz yal are doing an excellent job i find everything that i have issues on here but this is kind of weird

---

