---
title: "Can't see my hard drives"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by technmom on 2010-05-31
Hello,
I'm brand new to ubuntu. When I clicked on Computer I was able to see my hard drives and mount them. Now I cannot. I have my system set up as a dual book with Window XP. 
I was showing my husband and children how to get to their files and could not. I rebooted to show them how to get onto windows or ubuntu and how to use it. Of course, whenever you try to demonstrate something thats when it doesn't work.
I did install c++ using the instructions from the forum 
I just tried to cut and paste them here but that doesn't seem to work either. I don't see how making that install would change things.
I'm frustrated obviously :(

---

### Post by saakeman on 2010-05-31
> **technmom said:**
> Hello,
I'm brand new to ubuntu. When I clicked on Computer I was able to see my hard drives and mount them. Now I cannot. I have my system set up as a dual book with Window XP. 
I was showing my husband and children how to get to their files and could not. I rebooted to show them how to get onto windows or ubuntu and how to use it. Of course, whenever you try to demonstrate something thats when it doesn't work.
I did install c++ using the instructions from the forum 
I just tried to cut and paste them here but that doesn't seem to work either. I don't see how making that install would change things.
I'm frustrated obviously :(

I have the same problemo ! 

-----------------------------------------***
**join facebook's dustbin of history**
it is 
**dustbin of history**

---

### Post by Matt__ on 2010-05-31
try ```
sudo apt-get install ntfs-config
```

allow write support when prompted and the drives should automount on boot

---

### Post by technmom on 2010-05-31
> **Matt__ said:**
> try ```
sudo apt-get install ntfs-config
```allow write support when prompted and the drives should automount on boot


I tried it. I did not get an option to allow write support. nothing happened. I am going to try rebooting.....be back

---

### Post by technmom on 2010-05-31
nothing worked. Please help

---

### Post by halitech on 2010-05-31
what is the output of
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by technmom on 2010-05-31
sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track


and

grubel@grubel-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/grubel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=grubel)

---

### Post by halitech on 2010-05-31
I'm thinking you put in sudo fdisk -1 instead of sudo fdisk -l (lowercase L)

---

### Post by yetiman64 on 2010-05-31
>      Quote:
                                                                      Originally Posted by **Matt__**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9389435#post9389435")                 
                 [I]try      Code:
     sudo apt-get install ntfs-config 
allow write support when prompted and the drives should automount on boot[/I]
                                 

I tried it. I did not get an option to allow write support. nothing happened. I am going to try rebooting.....be backAfter installing ntfs-config did you launch it from System>Administration>NTFS Configuration Tool, then input your password ? 

If so it should have given a dialog box where ntfs partitions can be selected by ticking their box, then when applied, another dialog is shown where write support for internal or external devices can be set up. 

This tool will automatically mount the partitions and put an entry into fstab for mounting on subsequent boots. The process isn't automatic on install and won't do its job until launched manually. Hope this helps.

---

### Post by technmom on 2010-05-31
THank you thank you:)

Now if i can figure out how to mark this sovlved

---

### Post by yetiman64 on 2010-05-31
At the top of your browser window is the thread tools drop down menu. Select solved. Cheers.

Edit: you will be redirected and will need to click on confirmation etc.

---

