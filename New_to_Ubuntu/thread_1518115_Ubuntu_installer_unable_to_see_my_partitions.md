---
title: "Ubuntu installer unable to see my partitions"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by Drawdecirle on 2010-06-26
Brand new (hopeful) Linux user here.  I recently got a new computer (with Windows 7 preinstalled), but I wanted to go ahead and put Ubuntu on here so I wasn't tied down to Microsoft.  Anyway, I've been working on this problem for a little while but to no avail.  I was actually recommended to come here from another forum, so here I am.  Here's a basic rundown of my problem:

To start things off, I've got a 600GB hard drive, which consisted mostly of one large Windows 7 partition.  I shrunk this down to roughly 300GB with the intention of using the other half for Ubuntu.  After doing this, I burned the .iso image (both regular and alternative) but had some other problems with those.  I've been able to get the furthest with a USB boot, so that's what the following steps will describe.

After getting into Ubuntu (this is 10.04 by the way), I've tried a number of things from other forums and through searching, but essentially when I reach step 4 of the installer (Prepare Partitions) it only shows /dev/sdb (which is the device for my USB).  It can't seem to pick up the hard drive.  I've got some pictures below to demonstrate my situation.

GParted (sda is my hard drive, sdb is my USB drive):
[http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot--dev-sda-GParted.png&newest=1](http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot--dev-sda-GParted.png&newest=1)
[http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot--dev-sdb-GParted.png&newest=1](http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot--dev-sdb-GParted.png&newest=1)

Here's what the 4th step in my installer looks like (you can't see it here, but the only option in the dropdown is sdb)
[http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot-Install.png&newest=1](http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot-Install.png&newest=1)

I'm fairly new to this, so if there's any information you need or advice you'd like to offer, I'd be glad to give/take it.  Thank you very much.

---

### Post by sikander3786 on 2010-06-26
Hi.

Very strange problem at least for me. Is your system an OEM? Can you please list your model and manufacturer?

Check this link for any useful references.

[http://ubuntuforums.org/showthread.php?t=581574](http://ubuntuforums.org/showthread.php?t=581574)

Regards.

---

### Post by wilee-nilee on 2010-06-26
You need to hit the custom install to see the preformatted ext3. Lucid runs with a ext4, If it was me I would remove the ext3 with gparted and just let the installer go to the largest free space. It will build a extended partition with Lucid in a primary and a swap. If you have the extended you cam shrink the Lucid and put a bunch of other OS in that extended if you wanted more then a dual boot possibilities.

---

### Post by sikander3786 on 2010-06-26
I am so lazy to welcome you to the forums.

WELCOME:popcorn:

---

### Post by Elfy on 2010-06-26
If when you get to the partitioning stage - try choosing manual - does it see the sda3 partition then? If it does I would be inclined to going back to gparted and making the partitions before installing and then using the manual method.

Edit - also did you check that the download and burn were good?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by wilee-nilee on 2010-06-26
> **forestpiskie said:**
> If when you get to the partitioning stage - try choosing manual - does it see the sda3 partition then? If it does I would be inclined to going back to gparted and making the partitions before installing and then using the manual method.

Yah I would to, some don't know about the extended and primaries inside and being able to have multiple OS inside the extended.

---

### Post by Drawdecirle on 2010-06-26
>  Is your system an OEM? Can you please list your model and manufacturer?Sure thing.  It's an HP Pavilion Elite e9300z.  I customized it a bit from the standard though.  I have an AMD Phenom II X4 955, 6 gigs of RAM, and the SATA 600 GB hard drive that I mentioned before.  If there's anything else you'd like to know or want me to take a snapshot of, just point it out.

---

### Post by wilee-nilee on 2010-06-26
> **Drawdecirle said:**
> Sure thing.  It's an HP Pavilion Elite e9300z.  I customized it a bit from the standard though.  I have an AMD Phenom II X4 955, 6 gigs of RAM, and the SATA 600 GB hard drive that I mentioned before.  If there's anything else you'd like to know or want me to take a snapshot of, just point it out.

That doesn't matter look at my posts and forestpiskie's.

---

### Post by Drawdecirle on 2010-06-26
Here is what I get when I try to move forward on /dev/sdb (the USB drive):

[http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot-Install-1.png](http://s931.photobucket.com/albums/ad153/Drawdecirle/?action=view&current=Screenshot-Install-1.png)

It's a 1 GB flash drive, hence the size.  I did have it unallocated when I first tried but was getting the same results as currently, which is why I formatted as such figuring that I could "help" it along.  The download is good as well.

---

### Post by Drawdecirle on 2010-06-26
> That doesn't matter look at my posts and forestpiskie's.

Yeah, sorry about that.  I'm a couple minutes behind on my responses.  That was answering the very first question that sikander asked.

---

### Post by wilee-nilee on 2010-06-26
**Stop your not understanding** You show no partition in the main install window because you have no free space.
I will help you with this as will forestpikie but you have to stop now and answer a post by them or me so we can get you set up correctly.

Okay just ignore that sikander post the person has good intentions but doesn't understand, we all have been there it's no big deal.;)

---

### Post by Drawdecirle on 2010-06-26
> **Stop your not understanding** You show no partition in the main  install window because you have no free space.
I will help you with this as will forestpikie but you have to stop now  and answer a post by them or me so we can get you set up correctly.

What am I not understanding?  I answered your question two posts ago.  There's no free space on /dev/sdb because that's my USB drive.  I want to install it on my main hard drive (/dev/sda).  Whether I have the partition (/dev/sda3) formatted or not, it still does not show up.

---

### Post by wilee-nilee on 2010-06-26
> **Drawdecirle said:**
> What am I not understanding?  I answered your question two posts ago.  There's no free space on /dev/sdb because that's my USB drive.  I want to install it on my main hard drive (/dev/sda).  Whether I have the partition (/dev/sda3) formatted or not, it still does not show up. 

We were both posting at the same time so all I saw were answers to the moot post.

---

### Post by Drawdecirle on 2010-06-26
> We were both posting at the same time so all I saw were answers to the  moot post.

Ah, sorry about that.  I'm glad to see that even this late (for my time zone anyway), it's still pretty active here.  Hopefully that bodes well for solving this problem.

---

### Post by Elfy on 2010-06-26
Please answer whether the manual partitioner allows you to see the sda partitions.

Please answer whether the download iso was checked and is known to be good.

Please answer whether the burn was verified at boot.

I would also  suggest that we slow down and allow the OP time to read and respond to posts.

---

### Post by Elfy on 2010-06-26
@OP - also if you want to talk to someone in real time - try the #ubuntu-beginners link in my sig - I am there at the moment for a while - you can do so from the livecd in firefox.

---

### Post by Drawdecirle on 2010-06-26
> Please answer whether the manual partitioner allows you to see the sda  partitions.

Please answer whether the download iso was checked and is known to be  good.

Please answer whether the burn was verified at boot.

Yes for the last two.  For "manual partitioner", are you referencing GParted?  If so, yes I can see them.  My first post shows the screenshots I took of it.

---

### Post by Stigmata13 on 2010-06-26
> **Drawdecirle said:**
> Yes for the last two.  For "manual partitioner", are you referencing GParted?  If so, yes I can see them.  My first post shows the screenshots I took of it.
I'm pretty sure what he means is checking the box "Specify Partitions Manually (Advanced) right below the Erase and Use Entire Disc, the second radio box.
Check that and hit Next and tell us if you can see your hard drive from there.

---

### Post by Drawdecirle on 2010-06-26
> I'm pretty sure what he means is checking the box "Specify Partitions  Manually (Advanced) right below the Erase and Use Entire Disc, the  second radio box.
Check that and hit Next and tell us if you can see your hard drive from  there.

Nope, not there either.  By the way, I'm talking with him in the ubuntu-beginners chat in his sig.

---

### Post by Drawdecirle on 2010-06-26
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   619,446,271   619,239,424   7 HPFS/NTFS
/dev/sda3         619,450,335 1,226,273,579   606,823,245   5 Extended
/dev/sda5         619,450,398   646,712,639    27,262,242  82 Linux swap / Solaris
/dev/sda6         646,712,703   678,167,909    31,455,207  83 Linux
/dev/sda7         678,167,973 1,226,273,579   548,105,607  83 Linux
/dev/sda4       1,226,287,104 1,249,996,799    23,709,696   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3404EC0C04EBCEC4                       ntfs       SYSTEM                        
/dev/sda2        78F65C35F65BF23C                       ntfs       HP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        DEC4B5E9C4B5C3D5                       ntfs       FACTORY_IMAGE                 
/dev/sda5        7182141c-36e6-4fca-83be-b37ac0d5c1da   swap       swap                          
/dev/sda6        666f0de5-3483-422a-a745-a81831c38c84   ext4       home                          
/dev/sda7        c0ba009e-be09-4105-be92-16f0abf873b5   ext4       Ubuntu                        
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        3B69-1AFD                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/HP                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Drawdecirle on 2010-06-26
Was talking with forestpiskie in irc.  He thinks it may have something to do with there being a raid set up on my machine.  My guess is that it was there when I first got it as I have not actively set up any raids.

---

### Post by Drawdecirle on 2010-06-26
With the new information provided for forestpiskie about the RAID, I continued doing more searching and came across this:

[http://ubuntuforums.org/showthread.php?t=1380077](http://ubuntuforums.org/showthread.php?t=1380077)

This sounds very similar to my problem (the user was probably using a CD, which is why he didn't have anything showing up compared to me seeing my flash drive).

I went to run the first command and got this message:

Do you really want to erase "pdc" ondisk metadata on /dev/sda ? [y/n] :

I'd hate to jack my system up if this was something HP put on there.  Any clues?

---

### Post by Drawdecirle on 2010-06-26
Well, after reading about it a bit more, I went ahead and did it and it worked!  Amazing.

So, now I can select the /dev/sda7 to place Ubuntu, but I'm getting a "No root file system is defined" error.  Does anyone want to help me pick up from here and finish off this bad boy?

---

### Post by Elfy on 2010-06-27
> No root file system is definedIf you are using manual partitioning you need to select sda7, then edit (close to the bottom) in the new window - pick a mount point of /

---

