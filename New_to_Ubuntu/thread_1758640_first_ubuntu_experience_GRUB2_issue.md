---
title: "first ubuntu experience: GRUB2 issue"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by readmylips on 2011-05-14
Hello y'all,

I have just installed ubuntu 11.04, i also plyed with centos a bit a while back, i`m not a pro linux user, but i can usually google my way around a problem. Thing about this particular problem is that i couldn`t really find something for this specific error i`m getting.

So let`s get into it.

I installed ubuntu after windows (as in windows is installed for a few weeks now).
I have 3 Hdd's, the first one is partitioned in 2, the second one is partitioned in 2 and the 3rd one is partitioned in 2. Windows is installed on the 1st hdd and ubuntu is installed on the 3rd one.

After a clean install remove the CD (as instructed) and reboot the system. But no loader, it went directly to windows XP. Once in windows I run partion magic to check it out, but it gives me 2 errors and that it will fix them. My windows partitions look intact, so i decide to run the live cd and see how to fix the grub2.

This is what i get:

```
root@ubuntu:/boot/grub# mount |tail -l
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc6 on /media/8acd2dc4-91c0-4379-ae65-c38859c0c3ea type ext4 (rw,nosuid,nodev,uhelper=udisks)
root@ubuntu:/boot/grub# sudo grub-install --root-directory=/media//8acd2dc4-91c0-4379-ae65-c38859c0c3ea/ /dev/sd
sda   sda1  sdb   sdb1  sdb5  sdc   sdc1  sdc2  sdc5  sdc6  sdc7  
root@ubuntu:/boot/grub# sudo grub-install --root-directory=/media//8acd2dc4-91c0-4379-ae65-c38859c0c3ea/ /dev/sdc6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```Similar to my errors is only [http://ubuntuforums.org/showthread.php?p=10748199](http://ubuntuforums.org/showthread.php?p=10748199) , I also get the ```
grub-probe: error: cannot stat `aufs'.
``` error on further trials.

Centos was really easy to find fixes for every issue (didn`t have to post 1 question), the official forum would usually help you out really fast but X in ubuntu is something else and i would like to give it a try

So, anyone could push me in the wright direction?

---

### Post by drs305 on 2011-05-14
readmylips,

Hi, and welcome to the Ubuntu forums.

From the LiveCD, the only place you really want to install Grub is to sdc: In the first command, sdc6 if that is your Ubuntu partition. Do NOT use the partition number in the second command.
```
sudo mount /dev/sdc**6** /mnt
sudo grub-install /dev/sdc
```

If you haven't done so, you may just have to change your BIOS boot order to sdc (check BIOS and change it to the Ubuntu drive). That should allow Grub to control the boot.

If you do that and it boots directly to Ubuntu, open a terminal and run "sudo update-grub". That should detect Windows and the next boot the menu will display.

If you are still having problems, download and run the boot info script from the "BIS" script in my signature line. If you are using Natty, click on the "BIS-2" link and it will download it directly. The "BIS" link also contains instructions and links for how to run it if you have any questions.

---

### Post by readmylips on 2011-05-15
your post sounds helpful, problem now is that i boot the liveCD, i wait for ages to get to the Try Ubuntu button and when i press it nothing happens. Left it in that state for a few hours while i was out and when i came back, no movement. Gave it a few tries again and still no movement.

Was gonna try and boot it to find out what the primary partition is and install the GRUB on it since my bios is old and i doubt it can set partitions boot order. So i`m thinking of formatting the ubuntu partition and reinstalling it. The problem with this is that i open my partition magic and it`s a mess over there, can`t see the ext partitions and can`t really manage my ntfs partitions. Tell me if you understand what is what from the attached print screen.

LATER EDIT: since the partitions are still there and working, i checked the winxp disk management tool (pic attached), and as expected, everything is as should. don`t understand why partition magic looks like that tho..
Anyway, my next move is one of two:
1. format the ext partitions to clean ubuntu from the hdd, reinstall it and configure the grub correctly.
2. backup about 100GB, format everything and put win&ubuntu on disk0 (100gb each) to have them both on the primary disk, clean fresh install.

Think i`ll go for #2.

For those who look for answers to this problem and find this thread, the solution should be to install the boot loader on the primary partition or to set the partition that has grub on it as primary boot from bios.  Just hope the planets won`t align for you as they did in my first ubuntu experience.

---

### Post by drs305 on 2011-05-15
It sounds like the Cd is bad. It usually takes just a minute or three for me to get to the Desktop with the LiveCD. I'd make sure the download went ok by checking the MD5SUM (if you've never used the CD before) and burning a new one.

I'd like to help interpreting Partition Magic but I haven't used Windows apps in years and don't know how it interprets linux partitions. Hopefully someone with PM knowledge will pop in and tell us.

---

### Post by readmylips on 2011-05-15
sorry, i edited my post because i hate double posting.

I will download it again and burn it on another cd to be sure. 
Will update you after my full reinstall procedure with the result.

---

