---
title: "dual boot and file systems"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by beew on 2010-10-10
Hi,

I am thinking of setting up a dual boot between Ubuntu and another Linux distro, most likely Fedora 13. I am wondering if I will encounter a problem if I format the Ubuntu partition in Ext4 since apparently Fedora (for example) is still using Ext3? Should I format the Ubuntu partition in Ext3 to make sure that it is compatible with any Linux distro that I may install in the second partition or it doesn't matter?

Thanks.

---

### Post by amjjawad on 2010-10-10
> **beew said:**
> Hi,

I am thinking of setting up a dual boot between Ubuntu and another Linux distro, most likely Fedora 13. I am wondering if I will encounter a problem if I format the Ubuntu partition in Ext4 since apparently Fedora (for example) is still using Ext3? Should I format the Ubuntu partition in Ext3 to make sure that it is compatible with any Linux distro that I may install in the second partition or it doesn't matter?

Thanks.

Hi my friend,

Allow me to answer this because I have a good experience in both installation of Ubuntu and Fedora 13.

First thing first, Fedora and Ubuntu both are using ext4 so don't worry about that. I have two Fedora's Distros as you can see in my signature and all the partitions are ext4. I even share the SWAP partition among all the other OS's.

Fedora needs (as per their installation guide)
1- /boot
2- /root
3- /home
4- swap

That's the recommended scheme.

Check this: [http://www.facebook.com/album.php?aid=37804&id=154937727857763](http://www.facebook.com/album.php?aid=37804&id=154937727857763)

---

### Post by beew on 2010-10-10
Thanks my friend. That answers my question. :)

---

### Post by amjjawad on 2010-10-10
Very important note:
If Ubuntu is installed first and it's your main OS and it's boot loader (GRUB2) is installed in the MBR, then you need to do this:

Install Fedora's boot loader in **the first sector of your boot partition** where Fedora will be installed.
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-x86-bootloader.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s1-x86-bootloader.html)


I suggest to check this before anything: 
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/index.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/index.html)

---

### Post by amjjawad on 2010-10-10
> **beew said:**
> Thanks my friend. That answers my question. :)

If you need anything about Fedora, just let me know ;)
I installed Fedora more than I installed Ubuntu and had a major issue with it so I learned a lot indeed. Beside, Fedora's forum is very nice and helpful but it's a bit slower than this forum.

[http://forums.fedoraforum.org/](http://forums.fedoraforum.org/)

---

### Post by beew on 2010-10-10
Thanks again, the information about grub and grub2 is helpful.

---

### Post by coffeecat on 2010-10-10
One thing you may need to know if you are dual-booting Ubuntu and Fedora is that Ubuntu sets the UID of the first created account as 1000, whereas with Fedora it's 500. That's only a (minor) problem if you try to access your home folder from the "other" distro or if you set up a shared data partition with a Linux filesystem. In which case you will have to deal with ownership/permissions issues.

By the way, I recently had Fedora 13 running happily on an ext4 partition with Fedora's grub booting Fedora, Ubuntu and Windows.

---

### Post by Quackers on 2010-10-10
coffeecat, any chance of some cheap car insurance?  :-)

---

### Post by amjjawad on 2010-10-10
> **beew said:**
> Thanks again, the information about grub and grub2 is helpful.

You welcome :)

---

### Post by coffeecat on 2010-10-10
> **Quackers said:**
> coffeecat, any chance of some cheap car insurance?  :-)

:lol:

What I didn't make clear is that the reason I said that I *had" Fedora running happily rather than *have* is that I broke it. :oops: You remember that thread about using the restore partition on a Sony Vaio? Well - I tried a complete system restore (just for the heck of it) and Fedora didn't take kindly to my method of cloning partitions with tar.

:sigh:

---

