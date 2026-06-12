---
title: "Grub error 17"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by CarlCromer on 2009-10-05
I originally have Ubuntu in stalled on my machine but wanted to run windows XP with a Ubuntu VM. After I ran the system recovery disks I get the error "GRUB loading, please wait ...
Error 17" 
 
and it just hangs there. My machine is now a paper weight. I need help.

---

### Post by mikeyphi on 2009-10-05
Sounds as though windows has ****** grub!
You can use an Ubuntu live CD or a supergrub CD to reinstall grub.

Lots of good info here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by LewRockwell on 2009-10-05
[http://ubuntuforums.org/search.php?searchid=64997414](http://ubuntuforums.org/search.php?searchid=64997414)

one or more of these previous trouble-calls should give you some insight on your specific difficulties

.

---

### Post by LewRockwell on 2009-10-05
```
sudo fdisk -l
```

---

### Post by trikster_x on 2009-10-05
Try this:

> Restoring GRUB

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar. Ideally use Ubuntu 8.04 or higher as this has NTFS write support and makes life a bit easier; this isn't necessary, just handy.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)" note the space between root and (hd0,3).

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. At this stage you can either restart the system and install your own bootloader, or you can continue and tell the Windows bootloader where to find GRUB which will handle booting Linux. 

The rest of the instructions for recovering from grub errors can be found here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

