---
title: "i want to install windows 7 in my laptop"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by rjeeva on 2011-01-18
hi
i got a laptop with ''ubuntu 8.10'' os from my college
i want to install Windows 7 on my laptop but problem is windows 7 need ntfs formated hard drive
for that i have to install gparted in ubuntu 8.10. 
 i cant find gparted in synaptic package manager 
when i run this ''sudo aptitude install gparted''
madhuri@dell-desktop:~$ sudo aptitude install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for gparted
No candidate version found for gparted
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
 
so give me some ideas 
finally i am a noob in ubuntu ;).

---

### Post by howefield on 2011-01-18
Download the iso and burn a gparted CD.

That way you'd be using the current version.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by beew on 2011-01-18
> **rjeeva said:**
> hi
i got a laptop with ''ubuntu 8.10'' os from my college
i want to install Windows 7 on my laptop but problem is windows 7 need ntfs formated hard drive
for that i have to install gparted in ubuntu 8.10. 
 i cant find gparted in synaptic package manager 
when i run this ''sudo aptitude install gparted''
madhuri@dell-desktop:~$ sudo aptitude install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for gparted
No candidate version found for gparted
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
 
so give me some ideas 
finally i am a noob in ubuntu ;).

You may as well wipe your hd and install Windows7 and then install Ubuntu 10.04 or 10.10 along side to create a dual boot. Ubuntu 8.10 is dead, it is no longer supported. there is no point keeping it.

---

### Post by cariboo on 2011-01-18
8.10 is no longer supported, that's why you aren't able to download and install gparted. I'd suggest you upgrade to a newer version by pressing Alt-F2 and typing:

```
upgrade-manager -d
```

Once you upgraded, then you can resize your partitions. Keep in mind that Windows 7 needs 100Mb at the very start of the first partition in order to be able to boot.

---

### Post by rjeeva on 2011-01-18
thnk u all
i will try them

---

### Post by wilee-nilee on 2011-01-18
> **cariboo907 said:**
> 8.10 is no longer supported, that's why you aren't able to download and install gparted. I'd suggest you upgrade to a newer version by pressing Alt-F2 and typing:

```
upgrade-manager -d
```

Once you upgraded, then you can resize your partitions. Keep in mind that Windows 7 needs 100Mb at the very start of the first partition in order to be able to boot.

W7 only needs that if you let it install in a unallocated space, which will leave the first partition after the main W7 OS unallocated. You have to either build one NTFS to install the W7 OS into or build the 100Mb NTFS then the main NTFS.

The 100Mb partition is really for the ultimate version as part of the windows encryption.

OP, in the end make a NTFS for the W7 put a boot flag on it and install to it. If you don't pre-format you may loose a adjacent partition.

---

### Post by coffeecat on 2011-01-18
> **wilee-nilee said:**
> The 100Mb partition is really for the ultimate version as part of the windows encryption.

OP, in the end make a NTFS for the W7 put a boot flag on it and install to it. If you don't pre-format you may loose a adjacent partition.

Agreed. I installed Windows 7 Home Premium to my desktop by creating a single NTFS partition with Gparted first. The Windows installer was happy with that, Windows is now running OK from the partition I created with Gparted, and I didn't get the irritating separate 100MB partition. 

I don't believe you need to add the boot flag. I forgot to and the Windows installer must have added it for me automatically.

---

