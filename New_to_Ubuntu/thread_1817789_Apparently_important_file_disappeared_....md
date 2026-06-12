---
title: "Apparently important file disappeared ..."
date: 2011-08-03
forum: New to Ubuntu
---

### Post by mooboontu on 2011-08-03
I was changing some background and color settings the other day and when I rebooted my PC today my Ubuntu basically said this:

```
Error: cannot find /etc/apparmor/initramfs
```

:(

I use a couple different operating systems, and I mount a few hard drives here and there in different ways, but I don't get too crazy.

I hope I didn't like, "mis-mount" anything or whatever.

Is there some way to like, update ... or, recreate this file?

---

### Post by haqking on 2011-08-03
> **mooboontu said:**
> I was changing some background and color settings the other day and when I rebooted my PC today my Ubuntu basically said this:

```
Error: cannot find /etc/apparmor/initramfs
```:(

I use a couple different operating systems, and I mount a few hard drives here and there in different ways, but I don't get too crazy.

I hope I didn't like, "mis-mount" anything or whatever.

Is there some way to like, update ... or, recreate this file?

do you have other kernels ?
do you have a grub menu where you can choose ? if so choose the latest....and does the error message say find or execute ?

sounds like a possible kernel update or grub issue ? im not an expert on apparmor though

---

### Post by mooboontu on 2011-08-03
well sir, uh...

I've got 4 hard drives.

One is random crap, and 3 have operating systems.

I use the whole " F8 " to get a boot menu and select which OS I want.

But ... yes ... I have a GRUB with multiple kernels.

My GRUB lists my current and several other older kernels of Ubuntu.  It only shows a buncha that and a " memtest " at the bottom.

So, yeah, I did boot the most recent version or update of what I have.

And above, there, is the exact error I got with my most recent kernel of Ubuntu 10.04

---

### Post by haqking on 2011-08-03
> **mooboontu said:**
> well sir, uh...

I've got 4 hard drives.

One is random crap, and 3 have operating systems.

I use the whole " F8 " to get a boot menu and select which OS I want.

But ... yes ... I have a GRUB with multiple kernels.

My GRUB lists my current and several other older kernels of Ubuntu.  It only shows a buncha that and a " memtest " at the bottom.

So, yeah, I did boot the most recent version or update of what I have.

And above, there, is the exact error I got with my most recent kernel of Ubuntu 10.04

ok well it appears as  known bug back in 9.10 [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/439726](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/439726) you might wan log in to check it more to see if fix applies to you

---

### Post by mooboontu on 2011-08-03
```
Error: command /usr/sbin/apparmor_status failed with exit code 4: You do not have enough privilege to read the profile set.
```


I read that ^^ on the bug page but I've never seen that error before :(

---

### Post by haqking on 2011-08-03
> **mooboontu said:**
> ```
Error: command /usr/sbin/apparmor_status failed with exit code 4: You do not have enough privilege to read the profile set.
```I read that ^^ on the bug page but I've never seen that error before :(


if you read the top of the bug page it says:

At boot time, /etc/apparmor/initramfs throws errors about not  finding 'find' and 'xargs' commands.  It appears this script is being  run too early, before /usr is mounted?

which is related to your error

however like i say im not an apparmor expert, i am just throwing in my 2 cents as im bored ;-)

---

### Post by jtarin on 2011-08-03
Try to update Grub in the related OS.

---

### Post by mooboontu on 2011-08-03
... do I just do that when GRUB comes up or do I have to do some single user stuff or ... what?

---

### Post by mooboontu on 2011-08-03
Cuz I have no access to my Ubuntu Distro main interface at all

---

### Post by jtarin on 2011-08-03
Do you have your Ubuntu Live CD? Use the [CHROOT]("https://help.ubuntu.com/community/Grub2#ChRoot") method to update Grub.You can skip steps 9/10.

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> Do you have your Ubuntu Live CD? Use the [CHROOT]("https://help.ubuntu.com/community/Grub2#ChRoot") method to update Grub.You can skip steps 9/10.


Suhweet !! ... thanks for the tip.  Now, lol, I have to close everything and reboot and go do that, heh.


I'll reply when I can with the results, hopefully I actually get this right.

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> Do you have your Ubuntu Live CD? Use the [CHROOT]("https://help.ubuntu.com/community/Grub2#ChRoot") method to update Grub.You can skip steps 9/10.

I tried that, exactly, and successfully.

Then I rebooted, and got these:

```
init: hwclock main process (337) terminated with status *[...my drive ID]*
```

In the "main process"

I got 337 when I first rebooted.
Then 328.
Then 332.
Then 312.

I'm kind of at a loss with this craziness.

---

### Post by jtarin on 2011-08-03
So you able to get to the desktop OK?

---

### Post by jtarin on 2011-08-03
Typically that erorr msg will accompany the actual error msg. 
For example:
```
init: hwclock main process (nnn) terminated with status 2
.: can't open /etc/default/rcS
init: mountall main process (nnn) terminated with status 2
filesystem check failed
```
That guy's problem was /etc/default/rcS.

Post the entire output of the message, or take a photo of the screen & post somewhere. Also, boot to a liveCD and take a look at your /var/log files to see if you can spot any obvious error messages.

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> So you able to get to the desktop OK?

Unfortunately no.  I read some stuff about people suggesting some forced checkup:

```
sudo fsck -f /dev/sda1
```

Did that just fine from the LiveCD.

Then somebody mentioned:

```
mountall start
```

If I go do that, is there anything else you think I should try additionally?

---

### Post by jtarin on 2011-08-03
mountall start
...this should get you up to the login page, you may encounter further errors there..
Then you might be able to login but the desktop might not load,  you can then proceed with the normal troubleshooting..or if you get errors, try logging in with a different environment, maybe xbuntu or any other, not gnome..depending on which flavor you are using..atleast if you have 2 or more environments, I think you be able to login to the desktop..
My understanding says that this problem happens when you are dual booting with windows, or unknowingly you remove a mount point which was there during last boot..

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> mountall start
...this should get you up to the login page, you may encounter further errors there..
Then you might be able to login but the desktop might not load,  you can then proceed with the normal troubleshooting..or if you get errors, try logging in with a different environment, maybe xbuntu or any other, not gnome..depending on which flavor you are using..atleast if you have 2 or more environments, I think you be able to login to the desktop..
My understanding says that this problem happens when you are dual booting with windows, or unknowingly you remove a mount point which was there during last boot..

K ... I'm gonna go do that now.  Don't know about all these "other environments" though.  I'll have to see.

---

### Post by jtarin on 2011-08-03
In your error:init: hwclock main process (337) terminated with status [...my drive ID].....does your drive id match the one your trying to mount?

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> In your error:init: hwclock main process (337) terminated with status [...my drive ID].....does your drive id match the one your trying to mount?

Sure does ...

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> mountall start
...this should get you up to the login page, you may encounter further errors there..
Then you might be able to login but the desktop might not load,  you can then proceed with the normal troubleshooting..or if you get errors, try logging in with a different environment, maybe xbuntu or any other, not gnome..depending on which flavor you are using..atleast if you have 2 or more environments, I think you be able to login to the desktop..
My understanding says that this problem happens when you are dual booting with windows, or unknowingly you remove a mount point which was there during last boot..

Got this ... 

```
Mountall: mount /sys/fs/fuse/connections [368]: Permission Denied
```

---

### Post by mooboontu on 2011-08-03
> **jtarin said:**
> mountall start
...this should get you up to the login page, you may encounter further errors there..
Then you might be able to login but the desktop might not load,  you can then proceed with the normal troubleshooting..or if you get errors, try logging in with a different environment, maybe xbuntu or any other, not gnome..depending on which flavor you are using..atleast if you have 2 or more environments, I think you be able to login to the desktop..
***My understanding says that this problem happens when you are dual booting with windows, or unknowingly you remove a mount point which was there during last boot..***

I'm not doing any sort of dual-booting at all btw, traditionally.

This Ubuntu install has a completely unique hard drive.

---

### Post by jtarin on 2011-08-03
To boot, try this from the prompt you were given

```
mount / -o remount,rw
nano /etc/init/hwclock.conf
# comment out the 'start on' line to have a # at the beginning of the line
mount / -o remount,ro
```
That should let you reboot properly. However, if you ever want to dual boot w/ windows you may want to re-enable this .conf file, so try this in a terminal:

sudo apt-get install util-linux --reinstall

Which should fix the 'hwclock' program so it won't exit improperly. Then edit /etc/init/hwclock.conf again and uncomment the 'start on' line, you should be able to reboot.

---

### Post by mooboontu on 2011-08-03
K ... trying that now ...

---

### Post by mooboontu on 2011-08-04
> **jtarin said:**
> To boot, try this from the prompt you were given
 
```
mount / -o remount,rw
nano /etc/init/hwclock.conf
# comment out the 'start on' line to have a # at the beginning of the line
mount / -o remount,ro
```
That should let you reboot properly. However, if you ever want to dual boot w/ windows you may want to re-enable this .conf file, so try this in a terminal:
 
sudo apt-get install util-linux --reinstall
 
Which should fix the 'hwclock' program so it won't exit improperly. Then edit /etc/init/hwclock.conf again and uncomment the 'start on' line, you should be able to reboot.
 
I then get denied from the first instruction with this:
 
```
mount: Permission Denied
```
 
I literally ran that straight from:
 
[EMAIL="root@mypc:~$"]root@*mypc*:~$[/EMAIL]
 
after the error pushed me into single user admin mode

---

### Post by mooboontu on 2011-08-04
> **jtarin said:**
> To boot, try this from the prompt you were given

```
mount / -o remount,rw
nano /etc/init/hwclock.conf
# comment out the 'start on' line to have a # at the beginning of the line
mount / -o remount,ro
```
That should let you reboot properly. However, if you ever want to dual boot w/ windows you may want to re-enable this .conf file, so try this in a terminal:

sudo apt-get install util-linux --reinstall

Which should fix the 'hwclock' program so it won't exit improperly. Then edit /etc/init/hwclock.conf again and uncomment the 'start on' line, you should be able to reboot.

Did that maybe change my filesystem or something weird?  Cuz now it's like, denying everything o_0

---

### Post by jtarin on 2011-08-04
> **mooboontu said:**
> Did that maybe change my filesystem or something weird?  Cuz now it's like, denying everything o_0
No...does not change filesystem. Undo the edit if it's not working.

---

### Post by jtarin on 2011-08-04
> **mooboontu said:**
> Did that maybe change my filesystem or something weird?  Cuz now it's like, denying everything o_0

When you say denying everything......what exactly do you mean? You need to post error messages.
If you can get to the desktop with the Live CD I recommend you run the BootInfo Script. There is a link in my signature. We maybe can tell more of what is going on if we can look at you setup. Post it here.

---

### Post by mooboontu on 2011-08-06
> **jtarin said:**
> When you say denying everything......what exactly do you mean? You need to post error messages.
If you can get to the desktop with the Live CD I recommend you run the BootInfo Script. There is a link in my signature. We maybe can tell more of what is going on if we can look at you setup. Post it here.


Thanks very much for the advice btw.  I had to take this advice, AND your previous CHROOT advice, but that script eventually worked out nicely ... it's pretty b.a. :)


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Testdisk is installed in the MBR of /dev/sdd.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sde and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sdd2: __________________________________________________________________________

    File system:       ufs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sdd3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sdd4: __________________________________________________________________________

    File system:       ufs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sdd5: __________________________________________________________________________

    File system:       ufs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sde5 starts 
                       at sector 63.
    Mounting failed:   boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
boot_info_script.sh: line 2298: /bin/mount: Permission denied
fuse: failed to execute /bin/mount: Permission denied

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,244,330,639 1,244,330,577  83 Linux
/dev/sda2       1,244,330,640 1,250,258,624     5,927,985  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   629,153,594   629,153,532   7 NTFS / exFAT / HPFS
/dev/sdb2    *    629,153,792 1,250,260,991   621,107,200   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   488,392,064   488,392,002  83 Linux


Drive: sdd _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *              1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34           161           128 Boot partition (FreeBSD)
/dev/sdd2             162     4,194,465     4,194,304 Unix File System (UFS) partition (FreeBSD)
/dev/sdd3       4,194,466    25,165,985    20,971,520 Swap partition (FreeBSD)
/dev/sdd4      25,165,986    27,263,137     2,097,152 Unix File System (UFS) partition (FreeBSD)
/dev/sdd5      27,263,138   976,763,041   949,499,904 Unix File System (UFS) partition (FreeBSD)

Drive: sde _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde2    *         16,065   488,392,064   488,376,000   5 Extended
/dev/sde5              16,128   488,392,064   488,375,937   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2fecbbf2-2d92-4f3a-99d0-ae24fd8e95c4   ext3       
/dev/sda2        1846e2da-9a9d-4af2-a4ac-461cd09105da   swap       
/dev/sdb1        1CBEC6DDBEC6AF18                       ntfs       ASSORTED
/dev/sdb2        26B8198DB8195C9D                       ntfs       
/dev/sdc1        8182c6fd-821a-46aa-8bf5-768a987a3716   ext3       BACKUP
/dev/sdd2                                               ufs        
/dev/sdd4                                               ufs        
/dev/sdd5                                               ufs        
/dev/sde5        C92325EF6959CD15                       ntfs       BACKUP_2

================================ Mount points: =================================

Device           Mount_Point              Type       Options



======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdd1

00000000  31 c9 8e c1 8e d9 8e d1  bc 00 7c bb 63 7c 8b 77  |1.........|.c|.w|
00000010  0a 01 de 89 f0 c1 e8 04  83 e6 0f 8e d8 83 c6 f0  |................|
00000020  b8 00 0a bf f0 ff 8e c0  fd 89 f9 41 f3 a4 8e d9  |...........A....|
00000030  8e c1 8b 4f 0a 89 de bf  00 90 01 ce 01 cf 4e 4f  |...O..........NO|
00000040  f3 a4 fc fa 49 74 14 e4  64 a8 02 75 f7 b0 d1 e6  |....It..d..u....|
00000050  64 e4 64 a8 02 75 fa b0  df e6 60 fb 88 16 00 09  |d.d..u....`.....|
00000060  e9 ad 13 eb 0e 42 54 58  01 02 00 f7 0f 90 06 00  |.....BTX........|
00000070  00 00 00 fa 31 c0 8e d0  bc 00 18 8e c0 8e d8 66  |....1..........f|
00000080  6a 02 66 9d bf 00 5e b9  00 19 f3 ab bb 29 95 b9  |j.f...^......)..|
00000090  10 00 bf 80 00 89 1d 47  47 ab 83 c3 04 e2 f6 bf  |.......GG.......|
000000a0  00 5e be e2 95 ac 98 91  e3 1d ac 92 ad 93 ad b6  |.^..............|
000000b0  08 d1 eb 73 0b 89 05 88  75 02 88 55 05 83 c0 04  |...s....u..U....|
000000c0  8d 7d 08 e2 ec eb de c6  45 05 18 c6 45 08 10 c6  |.}......E...E...|
000000d0  45 66 68 bb 20 28 e8 b8  00 0f 01 1e d6 95 0f 01  |Efh. (..........|
000000e0  16 d0 95 0f 20 c0 40 0f  22 c0 ea 8c 90 08 00 31  |.... .@."......1|
000000f0  c9 b1 10 8e d1 b1 38 0f  00 d9 ba 00 a0 00 00 36  |......8........6|
00000100  0f b7 05 13 04 00 00 c1  e0 0a 2d 00 10 00 00 29  |..........-....)|
00000110  d0 b1 33 51 50 68 02 02  00 00 6a 2b ff 35 0c 90  |..3QPh....j+.5..|
00000120  00 00 51 51 51 51 52 b1  07 6a 00 e2 fc 61 07 1f  |..QQQQR..j...a..|
00000130  0f a1 0f a9 cf fa bc 00  18 00 00 0f 20 c0 25 ff  |............ .%.|
00000140  ff ff 7f 0f 22 c0 31 c9  0f 22 d9 0f 01 15 d0 95  |....".1.."......|
00000150  00 00 66 ea f5 90 18 00  b1 20 8e d1 8e d9 8e c1  |..f...... ......|
00000160  8e e1 8e e9 48 0f 22 c0  ea 0a 91 00 00 31 c0 8e  |....H."......1..|
00000170  d0 8e d8 bb 08 70 e8 18  00 0f 01 1e dc 95 fb f6  |.....p..........|
00000180  06 07 90 01 74 fe c7 06  72 04 34 12 ea f0 ff 00  |....t...r.4.....|
00000190  f0 e4 21 50 e4 a1 50 b0  11 e6 20 e6 a0 88 d8 e6  |..!P..P... .....|
000001a0  21 88 f8 e6 a1 b0 04 e6  21 b0 02 e6 a1 b0 01 e6  |!.......!.......|
000001b0  21 e6 a1 58 e6 a1 58 e6  21 c3 6a 00 eb 34 6a 01  |!..X..X.!.j..4j.|
000001c0  eb 30 6a 03 eb 2c 6a 04  eb 28 6a 05 eb 24 6a 06  |.0j..,j..(j..$j.|
000001d0  eb 20 6a 07 eb 1c 6a 08  eb 20 6a 0a eb 1c 6a 0b  |. j...j.. j...j.|
000001e0  eb 18 6a 0c eb 14 6a 0d  eb 10 6a 0e eb 0c 6a 10  |..j...j...j...j.|
000001f0  eb 00 ff 34 24 c6 44 24  04 00 fc 1e 06 60 0f a8  |...4$.D$.....`..|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 689: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 2285: /bin/mount: Permission denied
boot_info_script.sh: line 3036: /bin/mount: Permission denied

```

Five HDD's ... 3 Operating Systems --> 2 HDD's full of random, non-boot flagged, crap.

Every single OS has a private HDD ... Except MS Windows -- BUT, it is partitioned on an even split of a 640 GB drive, paired with only random backup stuff.

-- Ubuntu 10.04 32bit
-- PC BSD Unix 8.2 64bit ... (and its quadzillion partitions)
-- MS Windows 7 Ultimate 32 Bit

---

### Post by jtarin on 2011-08-07
I'm going to make a recommendation and you can follow or not. I would make Windows /dev/sda (first drive/first partition) I would upgrade all Grub installs to Grub 2 and install them to the "/" (root) of each drive of their respective OS. Then I would install EasyBCD (in my signature)in your windows install to boot all. You need to get everything in order. Why are you still using Grub Legacy (1.97)?

---

### Post by mooboontu on 2011-08-08
> **jtarin said:**
> I'm going to make a recommendation and you can follow or not. I would make Windows /dev/sda (first drive/first partition) I would upgrade all Grub installs to Grub 2 and install them to the "/" (root) of each drive of their respective OS. Then I would install EasyBCD (in my signature)in your windows install to boot all. You need to get everything in order. Why are you still using Grub Legacy (1.97)?


I understand what you said, I do appreciate that.  The only part I'm a big fan of is the idea for the GRUB 2 update.  Other than that I set my boot prefs. really weird like on purpose.

I did exactly what I was supposed to do with your advice, and link, from the CHROOT and the GRUB 2 update as per the official Ubuntu tutorial page itself.

However, I am denied because the Ubuntu unit I have, when I CHROOT into it, it is set to update from 

```
'ftp.ussg.iu.edu'
```... that repository no longer even exists.

I just need to know how to change a repository from which to update, and I would like to know more about the abovementioned issue with constant "Permission Denied."

Those two would be great if I could get help, the repository and denial issues :) ... once I can update GRUB after correcting the repository source, hopefully some of the other issues can be resolved.

---

### Post by jtarin on 2011-08-09
> **mooboontu said:**
> 
However, I am denied because the Ubuntu unit I have, when I CHROOT into it, it is set to update from 

```
'ftp.ussg.iu.edu'
```... that repository no longer even exists.

I just need to know how to change a repository from which to update, and I would like to know more about the abovementioned issue with constant "Permission Denied."

.
[This]("https://help.ubuntu.com/community/Repositories/Ubuntu") will show you how to enable an alternate Main repository.

---

### Post by mooboontu on 2011-08-12
Sorry to seem like I ditched btw.  I'm runnin' into lotsa snags with the modding of "***sources.list***".  

I'm totally still workin' on it though, and I appreciate the help.  Once I get some more "***GRUB***" stuff figured out.  Hopefully then we can resolve all of the "***Permission Denied***" errors and "***corrupt filesystem***" errors :(

---

### Post by jtarin on 2011-08-13
> I'm runnin' into lotsa snags with the modding of "sources.list". Post what your haveing a problem with. You might also post your sources.list (between code tags) so I can take a look.

---

### Post by mooboontu on 2011-08-17
So laugh all you want at my moronic efforts, lol ... but I tried the following in desperate failing attempts to see if I could simply let my old Ubuntu install get itself to update, so that I could even have GRUB update in the first place ... since updating of any sort doesn't work.


this is my original ***sources.list*** from the very beginning:

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid main restricted
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates main restricted
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid universe
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid universe
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates universe
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid multiverse
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid multiverse
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates multiverse
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security main restricted
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security main restricted
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security universe
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security universe
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security multiverse
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security multiverse
# deb http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/ # disabled on upgrade to lucid
# deb http://ftp2.de.debian.org/debian-volatile sarge/volatile main # disabled on upgrade to lucid
```
^^ I have no idea why that says ***Jaunty***...


This is when I decided to change my repository by adjusting my very original to something diff. I thought would work better:

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ lucid main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security main restricted
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security main restricted
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security universe
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security universe
deb http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security multiverse
deb-src http://ftp.ussg.iu.edu/linux/ubuntu/ lucid-security multiverse
# deb http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/rvm/mplayer/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/ # disabled on upgrade to lucid
# deb http://ftp2.de.debian.org/debian-volatile sarge/volatile main # disabled on upgrade to lucid
```
^^ That flopped as well for some reason.

This one is what I did when I tried to just overhaul everything:
```

deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

This is the variety of error message that I get every. single. time. ...  but the following display is most recent...

```
Err http://ppa.launchpad.net lucid Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid Release.gpg
Err http://archive.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid Release
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/main Packages
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/restricted Packages
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign http://security.ubuntu.com lucid-security Release
Ign http://archive.ubuntu.com lucid Release
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://ppa.launchpad.net lucid Release
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://archive.ubuntu.com lucid-updates Release
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://archive.ubuntu.com lucid/main Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Err http://ppa.launchpad.net lucid/main Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid/restricted Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://archive.ubuntu.com lucid/universe Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://archive.ubuntu.com lucid/multiverse Packages
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://archive.ubuntu.com lucid/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://archive.ubuntu.com lucid/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://archive.ubuntu.com lucid/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://archive.ubuntu.com lucid/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://archive.ubuntu.com lucid-updates/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://archive.ubuntu.com lucid-updates/restricted Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://archive.ubuntu.com lucid-updates/universe Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://archive.ubuntu.com lucid-updates/multiverse Packages
Err http://security.ubuntu.com lucid-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/restricted Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid-updates/main Sources
Err http://security.ubuntu.com lucid-security/universe Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid-updates/restricted Sources
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid-updates/universe Sources
Err http://security.ubuntu.com lucid-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid-updates/multiverse Sources
Err http://security.ubuntu.com lucid-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid/main Packages
Err http://security.ubuntu.com lucid-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid/restricted Packages
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid/universe Packages
Ign http://archive.ubuntu.com lucid/multiverse Packages
Ign http://archive.ubuntu.com lucid/main Sources
Ign http://archive.ubuntu.com lucid/restricted Sources
Ign http://archive.ubuntu.com lucid/universe Sources
Ign http://archive.ubuntu.com lucid/multiverse Sources
Ign http://archive.ubuntu.com lucid-updates/main Packages
Ign http://archive.ubuntu.com lucid-updates/restricted Packages
Ign http://archive.ubuntu.com lucid-updates/universe Packages
Ign http://archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://archive.ubuntu.com lucid-updates/main Sources
Ign http://archive.ubuntu.com lucid-updates/restricted Sources
Ign http://archive.ubuntu.com lucid-updates/universe Sources
Ign http://archive.ubuntu.com lucid-updates/multiverse Sources
Err http://archive.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/main Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/restricted Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/universe Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-updates/multiverse Sources
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

---

### Post by jtarin on 2011-08-17
You need to verify your sources.list addresses....this why you keep getting ```
"(-5 - No address associated with hostname)"
```

---

### Post by mooboontu on 2011-08-25
> **jtarin said:**
> You need to verify your sources.list addresses....this why you keep getting ```
"(-5 - No address associated with hostname)"
```

Is there a mirror that you prefer?  

I like reliable ones, but those are usually popular enough to be slow.  And the fast ones are not well taken care of 

:(

---

### Post by jtarin on 2011-08-26
Here's an example:

**You have:**
```
http://archive.ubuntu.com/ubuntu/ lucid/main
```

**It should be:**
```
http://archive.ubuntu.com/ubuntu/dists/lucid/main/
```

If you enter each problematic "http" address in your browser you will see that it is unreachable. If you will instead enter "http://archive.ubuntu.com" then look for the next link, the next link and so on you will eventually see the correct address in your browser url bar. Follow the crumbs.

---

### Post by mooboontu on 2011-09-05
I'm not having much luck with that idea.

Has the " sources.list " file architecture, in general, been significantly overhauled since 10.04 LTS up till now?  I have no idea what the "average"  ... sources.list ... file is supposed to look like on a standard 10.04 LTS install.

I just don't know because I have like 3 or 4 of these source files laying different places and some of the originals on my previously functional pc were for "jaunty jackalope" even, lol.


So ... I don't know the correct layout of this document, I've tried your idea and am still having trouble, and I also don't know what to do with these suffixes:

-- Universe
-- Multiverse
-- Restricted 

.... etc.

How are those above incorporated?

I am having some issues and I am willing to push through this gibberish to meet your advice of updating to GRUB 2, I am just a very substantially stupid user when it comes to this, so bear with me.

---

### Post by jtarin on 2011-09-05
rename you old sources.list and make a new one.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by mooboontu on 2011-09-06
> **jtarin said:**
> rename you old sources.list and make a new one.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


So I did the chroot you told me to get into the Ubuntu Install ... and I used the link you gave me to generate this:
```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 
```I had that " sources.list " set to be used when I did the generic update command from a CHROOT from a standard LiveCD


After doing exactly that .... I got this:


```
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Err http://us.archive.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US     
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ lucid/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net lucid Release
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid/main Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com lucid Release
Ign http://us.archive.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com lucid-updates Release
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com lucid-security/restricted Packages
Ign http://us.archive.ubuntu.com lucid-security/universe Packages
Ign http://us.archive.ubuntu.com lucid-security/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-security/main Sources
Ign http://us.archive.ubuntu.com lucid-security/restricted Sources
Ign http://us.archive.ubuntu.com lucid-security/universe Sources
Ign http://us.archive.ubuntu.com lucid-security/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com lucid-security/restricted Packages
Ign http://us.archive.ubuntu.com lucid-security/universe Packages
Ign http://us.archive.ubuntu.com lucid-security/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-security/main Sources
Ign http://us.archive.ubuntu.com lucid-security/restricted Sources
Ign http://us.archive.ubuntu.com lucid-security/universe Sources
Ign http://us.archive.ubuntu.com lucid-security/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://us.archive.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-security/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```I apparently suck at managing my own distros ... FAIL ... :(

---

### Post by jtarin on 2011-09-06
Are you using a router to connect to the internet? Are you using Network Manager? Post the contents of /etc/resolv.conf .

---

### Post by mooboontu on 2011-09-07
> **jtarin said:**
> Are you using a router to connect to the internet? Are you suing Network Manager? Post the contents of /etc/resolv.conf .



You're right ... I use a router.  I think it's pretty decent though ... I hope, lol.

Here's the contents of that file:

```
# Generated by NetworkManager
```Yes, I promise, that's exactly what I saw, and ***only*** what I saw, when I used " gedit " to look at this.

Dunno if that's good or bad, but to me, it doesn't seem like much.

---

### Post by jtarin on 2011-09-07
I think your having DNS problems. Is your router setup to resolve DNS for you?

---

### Post by jtarin on 2011-09-07
[Try this fix for DNS]("http://ubuntuforums.org/archive/index.php/t-1475399.html").....should do ya!

---

### Post by mooboontu on 2011-09-07
> **jtarin said:**
> [Try this fix for DNS]("http://ubuntuforums.org/archive/index.php/t-1475399.html").....should do ya!


I honestly have no idea what is going on in that thread.  It is a complete garbled mess and I have no desire to sign up for some weird 3rd-party service.  I just want this system to work like it worked 9 months ago.  10.04 was working fine for me and none of those random comments seem familiar nor do they make any sense.  I am consistently leaning more towards FreeBSD every day now.  This really is kind of ridiculous.  " sudo apt-get update " should not be this hard.

Is there no other idea other than some random "OpenDNS" third party stuff where I sign up for some weird service and am forced to screw with my Comcast?  ELEVEN other devices work PERFECTLY in my house, today, literally.

---

### Post by jtarin on 2011-09-08
Your missing the point....there is nothing to sign up for.
I asked you if your using Network Manager.....you never answered.
If you are using Network Manager under "Edit Connections..." select the network where the issue is occurring (selecting the proper tab at the top, if necessary), and click Edit. Under the "IPv4 Settings" tab, set the Method to "Automatic (DHCP) addresses only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

---

### Post by jtarin on 2011-09-08
If your not using Network Manager open your etc/resolv.conf file, **_as root_** and add these lines at the top and save.

```
search google.com
nameserver 8.8.8.8
nameserver 8.8.4.4
```

These settings may or may not survive a reboot, if they don't there is one more file we need to edit if this works.

---

### Post by mooboontu on 2011-09-27
> **jtarin said:**
> If your not using Network Manager open your etc/resolv.conf file, **_as root_** and add these lines at the top and save.

```
search google.com
nameserver 8.8.8.8
nameserver 8.8.4.4
```These settings may or may not survive a reboot, if they don't there is one more file we need to edit if this works.



Sooo ....

I think the update worked ok, because I have a bunch of things that showed up.  I just had no idea that it would be so quick.  when I last got on that install, partially, there were like 300 things to update.  The update below took like 30 sec o_0

Also, I did all of this and got the exact same ."General error mounting filesystems ". error.

And I am really shaky about installing the grub with the ." grub-install ". business to update GRUB 2 etc.  I am more than willing to update the GRUB, but I'm unaware of a way to detect which partition the GRUB " 1 " is already on.  If I screw it up, then I'll botch my Win7 partition or botch my Ubuntu 10.04 that this is about.

Anyway, this is what I ran with your idea, and btw, the abovementioned quote of yours was good, it worked ... clearly, lol ;)   ...   I just need to boot it now that we got it to update.
```

ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:1 http://us.archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Get:3 http://us.archive.ubuntu.com lucid-security Release [44.7kB]
Hit http://ppa.launchpad.net lucid/main Packages                           
Get:4 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]
Hit http://us.archive.ubuntu.com lucid/main Packages    
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:5 http://us.archive.ubuntu.com lucid-security/main Packages [206kB]
Get:6 http://us.archive.ubuntu.com lucid-security/restricted Packages [14B]
Get:7 http://us.archive.ubuntu.com lucid-security/universe Packages [83.2kB]
Get:8 http://us.archive.ubuntu.com lucid-security/multiverse Packages [4,559B]
Get:9 http://us.archive.ubuntu.com lucid-security/main Sources [63.2kB]
Get:10 http://us.archive.ubuntu.com lucid-security/restricted Sources [14B]
Get:11 http://us.archive.ubuntu.com lucid-security/universe Sources [25.8kB]
Get:12 http://us.archive.ubuntu.com lucid-security/multiverse Sources [1,751B]
Get:13 http://us.archive.ubuntu.com lucid-updates/main Packages [514kB]
Get:14 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:15 http://us.archive.ubuntu.com lucid-updates/universe Packages [225kB]
Get:16 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]
Get:17 http://us.archive.ubuntu.com lucid-updates/main Sources [201kB]
Get:18 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get:19 http://us.archive.ubuntu.com lucid-updates/universe Sources [80.4kB]
Get:20 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,070B]
Fetched 1,515kB in 2s (676kB/s)                             
Reading package lists... Done
```

---

### Post by jtarin on 2011-09-28
As to Grub2.......[upgrading.]("https://help.ubuntu.com/community/Grub2#Upgrading_to_GRUB_2_From_GRUB")

---

### Post by mooboontu on 2011-09-29
> **jtarin said:**
> As to Grub2.......[upgrading.]("https://help.ubuntu.com/community/Grub2#Upgrading_to_GRUB_2_From_GRUB")


Thanks for the tip ;) ... just did the following and I'm now rebooting to test it:

```
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo apt-get install grub-pc
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following packages will be REMOVED:
  grub
The following NEW packages will be installed:
  grub-pc
The following packages will be upgraded:
  grub-common
1 upgraded, 1 newly installed, 1 to remove and 379 not upgraded.
Need to get 2,193kB of archives.
After this operation, 1,503kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-common 1.98-1ubuntu12 [1,584kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-pc 1.98-1ubuntu12 [609kB]
Fetched 2,193kB in 1s (1,118kB/s)
Preconfiguring packages ...
(Reading database ... 480492 files and directories currently installed.)
Removing grub ...
Processing triggers for man-db ...
(Reading database ... 480455 files and directories currently installed.)
Preparing to replace grub-common 1.98-1ubuntu9 (using .../grub-common_1.98-1ubuntu12_i386.deb) ...
/usr/sbin/invoke-rc.d: 274: /sbin/runlevel: Permission denied
Unpacking replacement grub-common ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu12_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98-1ubuntu12) ...
/usr/sbin/invoke-rc.d: 274: /sbin/runlevel: Permission denied

Setting up grub-pc (1.98-1ubuntu12) ...

Creating config file /etc/default/grub with new version
Generating core.img
Saving menu.lst backup in /boot/grub/menu.lst_backup_by_grub2_postinst
Running update-grub Legacy to hook our core.img in it
    Searching for GRUB installation directory ... found: /boot/grub
    Searching for default file ... found: /boot/grub/default
    Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
    Searching for splash image ... none found, skipping ...
    Found GRUB 2: /boot/grub/core.img
    Found kernel: /boot/vmlinuz-2.6.32-27-generic
    Found kernel: /boot/vmlinuz-2.6.32-26-generic
    Found kernel: /boot/vmlinuz-2.6.32-25-generic
    Found kernel: /boot/vmlinuz-2.6.32-24-generic
    Found kernel: /boot/vmlinuz-2.6.31-22-generic
    Found kernel: /boot/vmlinuz-2.6.31-20-generic
    Found kernel: /boot/vmlinuz-2.6.31-19-generic
    Found kernel: /boot/vmlinuz-2.6.31-17-generic
    Found kernel: /boot/vmlinuz-2.6.31-16-generic
    Found kernel: /boot/vmlinuz-2.6.31-15-generic
    Found kernel: /boot/vmlinuz-2.6.31-14-generic
    Found kernel: /boot/vmlinuz-2.6.28-16-generic
    Found kernel: /boot/memtest86+.bin
    Updating /boot/grub/menu.lst ... done
    
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
done

root@ubuntu:/# 
```

---

### Post by mooboontu on 2011-09-29
I ran your boot info script again, and got this right after I did the " GRUB 2 " update.  It looks, eh, kinda bad ... I think.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options



=============================== StdErr Messages: ===============================

boot_info_script.sh: line 689: /bin/mount: Permission denied
boot_info_script.sh: line 3036: /bin/mount: Permission denied

```

---

### Post by jtarin on 2011-09-29
Can you boot normally into any OS?

---

### Post by mooboontu on 2011-09-29
> **jtarin said:**
> Can you boot normally into any OS?

Well, I've found out that I think the boot HDD with GRUB is the Ubuntu HDD ... my " SATA 1 ".

I have 4 hard drives in the pc & 1 on the outside.

2 internals are random crap

1 internal is Win7

1 internal is the Ubuntu 10.04 


The only way that the " GRUB " auto randomly comes up is when the Ubuntu HDD is set to be the auto-default boot option of the system.

I hate boot manager confusion at times, so I never mess around with it that much, I just push " F8 " during boot and pick which ever OS I choose.

I am, right now, booted thru eSATA to an external HDD that has PCBSD sitting on it.

So this that I'm using works perfectly, so does the Win7.

The isolated Ubuntu 10.04 issue is on its own, separate (currently messed up, lol) drive.

---

### Post by mooboontu on 2011-09-29
> **jtarin said:**
> Can you boot normally into any OS?

Also ... I've had problems like what we've got here before.


I have tried some boot disc jazz with PCBSD as well that had dependencies like what we're dealing with.


Almost nothing like this, the bootscript, or grub, or what have you, ever recognizes my Ubuntu HDD.

People say I have too many hard drives, or the boot order is wrong, or something.

I have actually tried to Upgrade GRUB and other things in many different ways, even by partially decompiling the whole damn computer.  It's always difficult for me to get certain updates and discs to work when they can never see the damn drive.

I just feel at a loss for words tho, when I take everything down to only 1 drive, the Ubuntu one, and things are still not recognized.

---

### Post by jtarin on 2011-09-29
There's a link in my signature for EasyBCD it will allow you to edit your WIN7 bootmanager so that you can boot all OS's. Win7 should be the first disk to boot.Grub should be installed in the boot sector of each Linux partition.

---

### Post by mooboontu on 2011-09-30
> **jtarin said:**
> There's a link in my signature for EasyBCD it will allow you to edit your WIN7 bootmanager so that you can boot all OS's. Win7 should be the first disk to boot.Grub should be installed in the boot sector of each Linux partition.


I appreciate the advice but we already discussed that I do not want this "EasyBCD" ordeal.  I've never had to do that before in my life and I don't need to and I don't want to right now.

Boot managers are completely irrelevant for my computer.  Every single OS has it's own hard drive.  I don't use boot manager crap, I hate that.  I manually boot each OS from its own personalized hard drive each time.  I actually prefer to choose the boot device upon startup, from the BIOS.  It's better for me that way.


Is there anything we can do without this convoluted "EasyBCD" stuff?

---

### Post by jtarin on 2011-09-30
EasyBCD is "NOT" a boot manager. EasyBCD is an editor with a GUI that edits a file called "bcd" , which is located in Windows 7's hidden partition under \boot\bcd. It will add the entries for your other operating systems. Your WIN7 uses it now.....it's just transparent to you as it is booting nothing but windows now. EasyBCD helps you edit this file to be able to boot your other OS's. After editing it will appear at boot giving you the advantage of making a choice. It's either use the WIN7 boot manager or GRUB installed to the MBR to boot all,or you can continue to select your drive to boot at boot time. Windows likes to be on the first disk and first partition. I have dual/tripled booted for years,literally, and first started editing manually in notepad my windows boot.ini file. With Win7 it is not so easy to do by hand. If you don't want to use this method your free to do it as you prefer. Maybe a new post with your present problem someone can offer something more to you preference.[ Here's a link to do it MS's way without the GUI.]("http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html")

---

### Post by mooboontu on 2011-10-01
wow ...

---

