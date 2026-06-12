---
title: "Which dual-boot setup method would be safer / simpler here?"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by WBojangles on 2010-12-09
Hello,
I am not asking *how* to set up a dual boot, I have done some research on that in a few places. What I am asking is which way I should do it to reduce the difficulties I may have. To be more specific:

I am currently running Ubuntu 10.04, no other OSs.
The installation is new, so I do not have much on the drive.
I want to dual boot this with Windows 7.
I understand that it is possible to setup Windows 7 after Ubuntu 10.04, but from what I have read it is more complicated.

I don't know whether to wipe the drive and start over with Windows 7 then reinstall Ubuntu after it (meaning fixing the problems I had at first all over again), or to try installing Windows 7 on another partition now and having to deal with the MBR and any other problems I might run into. I think I would be OK with either method, but I don't know which is more potentially dangerous or difficult. Any suggestions?

---

### Post by lindsay7 on 2010-12-09
take a look at this site, it should give you some ideas. 

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by WBojangles on 2010-12-09
Thanks for the help! That article is really nice. So it should work just fine with Windows 7 instead of Vista?

---

### Post by wilee-nilee on 2010-12-09
> **WBojangles said:**
> Thanks for the help! That article is really nice. So it should work just fine with Windows 7 instead of Vista?

Although you have researched the topic and want no specific help with dual booting per-sey are you sure you have all the information needed and is what you have accurate.

---

### Post by WBojangles on 2010-12-09
I guess I can't really know for sure. When I do try this, sometime soon most likely, I will use for sure the site linked earlier and some occasional reference from elsewhere, whatever I find with specific issues while installing. The site linked made installing Windows after much more clear than what I had found before, so I feel it will be much simpler to do that than start over.

What I haven't been able to find is if I can do this kind of process with Windows 7 rather than Vista in the same manner. I am assuming so but computers are so fragile, they scare me.

---

### Post by nm_geo on 2010-12-09
> **WBojangles said:**
> I guess I can't really know for sure. When I do try this, sometime soon most likely, I will use for sure the site linked earlier and some occasional reference from elsewhere, whatever I find with specific issues while installing. The site linked made installing Windows after much more clear than what I had found before, so I feel it will be much simpler to do that than start over.

What I haven't been able to find is if I can do this kind of process with Windows 7 rather than Vista in the same manner. I am assuming so but computers are so fragile, they scare me.

The website is pretty old info 2008 and is legacy grub options not Grub2. I just read through it too.

Try this link.. [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by lindsay7 on 2010-12-09
Are we beating a dead horse here?  If ubuntu is installed first and the windows is installed then grub will be wiped out, so what needs to be done is reinstall grub2. Am I off base here.

---

### Post by wilee-nilee on 2010-12-09
> **lindsay7 said:**
> Are we beating a dead horse here?  If ubuntu is installed first and the windows is installed then grub will be wiped out, so what needs to be done is reinstall grub2. Am I off base here.

No, there is missing information.

Thread starter, lots of us I would say probably the majority of the users on this site use more then one OS. Many including myself dual boot W7 and Linux.

Many times when people come to the site for help it is due to misinformation found on the web in regards to there setup. The set up broken and they need help.

So I guess what I'm trying to say here is use the local forum help really if you want straight good answers, but it does help to know who those people are.

This
> **nm_geo said:**
> The website is pretty old info 2008 and is legacy grub options not Grub2. I just read through it too.

**Try this link**.. [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

Is also instructions for grub-legacy as well.

---

### Post by billnyeizzle on 2010-12-09
> **lindsay7 said:**
> Are we beating a dead horse here?  If ubuntu is installed first and the windows is installed then grub will be wiped out, so what needs to be done is reinstall grub2. Am I off base here.

sounds right to me. as long as we are talking about Ubuntu 10.10. BUT the first link that was shared [here ]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=2")   says to back up the grub loader by going into Terminal and actually copying the grub loader so that you don't have to reinstall Ubuntu. BUT, that isn't the only bootloader you can choose to load.. you can load Windows 7 boot loader through their version of MBR which is called (GUID) and then just configure the boot file so that PBS and bootloader run first, instead of dealing with booting through grub first. and that tutorial link says at the end to download  EasyBCD which basically makes you a safe grub loader so even if your vista scorches your grub, you can still dual boot.  ;)

---

### Post by Hans Upp on 2010-12-10
> **billnyeizzle said:**
> sounds right to me. as long as we are talking about Ubuntu 10.10. BUT the first link that was shared [here ]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=2")   says to back up the grub loader by going into Terminal and actually copying the grub loader so that you don't have to reinstall Ubuntu. BUT, that isn't the only bootloader you can choose to load.. you can load Windows 7 boot loader through their version of MBR which is called (GUID) and then just configure the boot file so that PBS and bootloader run first, instead of dealing with booting through grub first. and that tutorial link says at the end to download  EasyBCD which basically makes you a safe grub loader so even if your vista scorches your grub, you can still dual boot.  ;)
I wish I understood a word of what he said. 
Tell me, do I have an inferiority complex or am I really so inferior?

Anyway, I'm a bit in the same boat. I have Meerkat installed, on what I had promised myself would be a MicroSnot free machine, but now I want to install WinXP - so I assume there will be difficulties.

---

### Post by oldfred on 2010-12-10
Not all that difficult, depending on existing partition layout. Know which partition you have Ubuntu installed into.

Make sure you have a good liveCD. Use gparted to resize linux partition(s) and create a primary (must be primary) partition, format as NTFS and set boot flag on(off on any other partitions).

After installing windows it will put its boot loader in the MBR, you just have to reinstall grub2 (usually grub2) using liveCD. 

After booting Ubuntu run this to find the new windows install:
sudo update-grub

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Hans Upp on 2010-12-10
Thanks oldfred, I'm really grateful you took the time, honest.

But I think I'll take this little problem to the Absolute Beginner Talk forum.

Oh . . . wait a sec . . . this IS the Absolute Beginner Talk forum, damn!
.

---

### Post by WBojangles on 2010-12-10
Thank you oldfred, very concise. If I understand correctly, I should partition the drive and install Windows 7 on that new partition, reinstall grub2 with a liveCD, then update grub2 from Ubuntu.

---

### Post by oldfred on 2010-12-10
If you have troubles or need specific instructions just ask. Some are better with details than others.:)

If you need a detailed review of partitions and current booting.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by WBojangles on 2010-12-10
This script gives quite a bit of information. Here is the output:
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   964,702,207   964,700,160  83 Linux
/dev/sda2         964,704,254   976,773,119    12,068,866   5 Extended
/dev/sda5         964,704,256   976,773,119    12,068,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS
/dev/sdb2         976,752,000   976,768,001        16,002  17 Hidden HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7ec256df-c845-4ac0-a1f7-aa8c7d9f6b0a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b236ca6f-36c9-41eb-b96f-0ff3d4bc1ec5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        749802C7980287B6                       ntfs       Second                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
```

Ignore the second drive, I use it to back up files, I don't want to use it for Windows 7.

The only other partitions it looks like I have are a small one for "extended," I don't really know what that does, and one reserved for the Swap. So I could easily partition sda1?

---

### Post by oldfred on 2010-12-10
Under MBR (msdos) you are only allowed 4 primary partitions. But you can convert one primary to an extended that can hold many logical partitions. Windows has to be in a primary which is sda1 thru sda4. logicals start at sda5 whether you have used sda3 or 4 or not.

Your Ubuntu install is in sda1, sda2 is the extended and sda5 is swap which is used if RAM runs out of space and for hibernating.

Partitions do not have to be in order, so you can shrink  your Ubuntu partition and make a new windows NTFS partition as sda3 which is a primary. Move the boot flag from sda1 to sda3 or else windows will not see it to install. Windows does not see Linux partitions at all.

If you want you can also create a shared NTFS partition which can be logical or not and a /home partition. If you do both you will have to slide the start of the extended partition left to make room for more logical partitions. If you have data separate from system, system partitions do not have to be as large.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
Separate data partitions are a little more advanced but system is faster  & more reliable if data is separate(both windows & Ubuntu. 

More links on partitioning:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by WBojangles on 2010-12-10
Wow, that cleared up a lot. And I thought I had enough of an understanding to begin with.

I can't tell you how worried I was just thinking about trying to set something like this up earlier, though I am sure you have helped many through that. I am very confident now.

Unfortunately, I probably can't get around to doing this until after Christmas sometime, so I won't be posting back on how it went anytime soon. Anyway, thank you very much for the help. I have honestly never seen such a helpful and nice community elsewhere.

---

