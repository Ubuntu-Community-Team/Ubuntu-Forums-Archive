---
title: "partitioning the easy way"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by paulleth on 2011-07-06
I have been using Ubunt since Dapper and love it{'m using 11.04 now. Whate I would like to do is have sever versions of Ubuntu or Kubuntu to choose fromer when first startin. I have senn a lot of info on using windoz but I don't want to use it. I wou;d like to have  ubuntu and kubunto 10.04 plus 11.04 of each for a totall of 4 OS'sI only can do 2 and they are messed up as the second OS does not have enough room

---

### Post by Rex Bouwense on 2011-07-06
What is your question, how do I put 4 OS on one hard drive or something else?

---

### Post by ajgreeny on 2011-07-06
> **paulleth said:**
> I have been using Ubunt since Dapper and love it{'m using 11.04 now. Whate I would like to do is have sever versions of Ubuntu or Kubuntu to choose fromer when first startin. I have senn a lot of info on using windoz but I don't want to use it. I wou;d like to have  ubuntu and kubunto 10.04 plus 11.04 of each for a totall of 4 OS'sI only can do 2 and they are messed up as the second OS does not have enough room
It is very easy to do what I think you want, that is, have four separate ubuntu-family OSs installed on one machine; I already have mine like this (5 actually).

Tell us in detail what the problem is and I'm sure we'll be able to help you.

---

### Post by Perkins on 2011-07-06
The easiest tool I have found for reorganising your partitions (which seems to be what you're asking how to do) is gparted.  It's on the live CD, just boot one up and you should be able to rearrange things however you need.  (be warned, depending on what you want to do, it can take a *long* time.)

---

### Post by lakosshoots on 2011-07-06
I think that the important issue you must clarify is the number of primary partitions to create. Linux FS allow ony 4 primary. the rest must be logical. So I suggest you do a small preparatory shcme before you start.

This might be helpful for understading File Systems.

[http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-file-systems-56.html]("http://just-more-thoughts.blogspot.com/2011/06/ubuntu-1104-file-systems-56.html")

---

### Post by srs5694 on 2011-07-06
> **lakosshoots said:**
> I think that the important issue you must clarify is the number of primary partitions to create. Linux FS allow ony 4 primary. the rest must be logical.

Actually, that limitation is part of the [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) partitioning scheme, which predates Linux by about a decade. Other partitioning systems have other limits. Most importantly, the GUID Partition Table (GPT) system is limited to 128 partitions by default, although that number can be increased by certain tools.

---

### Post by pdlethbridge on 2011-07-06
both AJ and Rex are right I want to have 4 ubuntu or kubutu os's on my hard drive and be able to up grade them as they get dated

---

### Post by srs5694 on 2011-07-06
pdlethbridge, are you the same user as paulleth? It sounds like you are, but if not, it's best to start your own thread since it can get confusing trying to answer two questions or resolve two problems in one thread. I'll assume you're both the same person....

Your screen shot shows that you've got four primary partitions (counting your extended partition as a primary) crammed together at the very start of your hard disk, with the extended partition sandwiched between primary partitions. This means you've run up against the 4-primary-partition limit of the MBR partitioning scheme. There are three main ways you can overcome this problem:


[list]
[*]You can work within MBR and rearrange your partitions so that the extended partition covers most of the disk. You can create an arbitrary number of logical partitions inside the extended partition, but you can only have one extended partition per disk, so it has to cover most of the disk.
[*]You can move away from MBR by switching to the GPT system. GPT doesn't distinguish between primary, extended, and logical partitions, and its default limit of 128 partitions is plenty to handle most needs. The problem is that Windows can't boot from a GPT disk unless you've got UEFI firmware, so if you want to dual-boot with Windows, GPT isn't a good choice, at least not on a single-disk computer or a new UEFI-based computer.
[*]You can implement a Logical Volume Manager (LVM) configuration atop either MBR or GPT. LVM adds both complexity and flexibility. Personally, I like it for systems with multiple Linux installations because the flexibility comes in very handy when removing old installations and adding new ones; however, the added complexity can be intimidating to new users of LVM, and Ubuntu in particular has poor LVM support in its desktop installer.
[/list]


Any of these options can be applied with varying degrees of disruption to your current configuration. How many of your current partitions can you afford to completely discard? If you've got important data that you'd rather not back up and restore, please tell us where it is and provide the output from the following command:

```

sudo fdisk -lu

```

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags, otherwise it will lose its formatting and become harder to interpret.

If you can ditch everything and start fresh, then IMHO it's best to switch to GPT and start again, optionally with LVM if you're willing to tackle the learning curve. GPT has several advantages over MBR, such as a lack of the primary/extended/logical distinction that's caused you problems, CRCs of important data structures, backups of important data structures, and labels that can be applied to partitions. OTOH, Windows' boot limitations make GPT an impractical choice on a BIOS-based dual-boot computer unless Windows is booting from another physical disk.

---

### Post by beew on 2011-07-06
It is not very difficult but keep in mind that you can only have 4 primary partitions, so instead of making 4, one for each OS, it is better to create only one primary partition plus an extended partition. You can make as many logical partitions in the extended partition as you want so you can have separate / and /home partitions for each OS and can install more than 4 if you want.

You want to have one OS to control grub. So install that first and use the (only) primary partition as its root partition (mount point /) and you can create a /home partition and a swap partition inside the extended partition you have created.  Install the bootloader in the drive (say sda)

You can then install the other OSes (use manual partition) by carving out two pieces in the extended partition to be its / partition and /home partition. Since you only need one swap area for the multiboot system you don't need to create it again.  Important: choose either not to  install the bootloader or, if that option is not available (for Ubuntu based distros), install it in the partition rather than the drive (so say you have Ubuntu in sda1 which controls grub and you have Kubuntu 's / partition in sda5, install the kubuntu bootloader in sda5 instead of sda)

---

### Post by pdlethbridge on 2011-07-07
SRS, yes I'm the same guy. I have been having great problems trying to log in. I wish it was easier to change you use name and password. I just finishand I'm finally here Here is what I have on the hard drive using gpart in the live cd

---

### Post by pdlethbridge on 2011-07-07
here is what the code gave for howit is partitioned nowpaul@paul-desktop:~$ sudo fdisk -lu
[sudo] password for paul: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025697

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   123073964    61536951   83  Linux
/dev/sda2       123073965   244300454    60613245   83  Linux
/dev/sda3       244300455   364418459    60059002+  83  Linux
/dev/sda4       364418521   761524223   198552851+   5  Extended
/dev/sda5       364418523   485661014    60621246   83  Linux
/dev/sda6       485661078   610405739    62372331   83  Linux
/dev/sda7       610405803   732226634    60910416   83  Linux
/dev/sda8       732227584   761524223    14648320   82  Linux swap / Solaris
paul@paul-desktop:~$

---

### Post by pdlethbridge on 2011-07-07
I tried to install 9.04 on the second partition but it screwed up 10.04 on the first partition, But I think I'm heading in the right direction but need to get the grubs togeth

---

### Post by pdlethbridge on 2011-07-07
g parted work great as you can see. I have lots of room at the end of the disk and more than enough at the begining to make an adjustment or 2http://ubuntuforums.org/images/smilies/icon_biggrin.gif

---

### Post by pdlethbridge on 2011-07-09
I'm still running 10.o4 Kubuntu but I would like to add a couple of more flavors to the menu, How do I get to that point from what you see on the hard drive

---

### Post by pdlethbridge on 2011-07-10
This                                                               is current

---

### Post by srs5694 on 2011-07-10
The simplest way is to expand the extended partition to fill the rest of the disk and then add your new Linux installations in logical partitions inside the extended partition. You'll need to disable swap to do this, though, since GParted won't let you modify any in-use partition, and your swap space is currently in use, therefore making the extended partition in use as well. (That's what the key icons in the display mean -- those partitions are "locked" against changes.) You should be able to disable swap space within GParted by right-clicking it and selecting the option to disable it.

Alternatively, you could convert to GPT or LVM, as I outlined in an earlier post; however, at this point these options pose extra hassle and risk, so it's probably best to stick with MBR at the moment. An exception might be if you expect to be making changes every month or two, in which case the short-term pain of converting to LVM might be worthwhile in the long run.

---

### Post by pdlethbridge on 2011-07-11
If I boot up a ubuntu cd and open gpart Would I be able to change, sda2, sda3, sda  5,6+7 to logical and be able to have the 5 OS's I want

---

### Post by srs5694 on 2011-07-11
No, GParted can't do primary/logical conversions. Such things can sometimes be done by using my [FixParts](http://www.rodsbooks.com/fixparts/) program, but not in your case, if the fdisk output from your post #11 is accurate. In any event, there's no need for such conversions; as I said, you just need to expand the extended partition to cover the rest of the disk. This operation is fairly straightforward in GParted, although you do need to ensure that the partitions involved are not *currently* being used (that is, at the moment the operation occurs; this does *not* mean that they must contain no data).

---

### Post by pdlethbridge on 2011-07-13
i tried again last night to get the hard drive the way I want and this is what the drive looks like

---

### Post by pdlethbridge on 2011-07-17
this is what I did last night.10.4 is on the first partition. Are the 2 drives that show up in place sda7 and 8. I have the home folder in same place on the place menu but its properties are not found

---

### Post by pdlethbridge on 2011-07-25
I have change quit a bit with Gpated and found it's much better to use a clean cd to run a live CD I made all partitions smaller as I was not even close to using half of the partitions

---

### Post by pdlethbridge on 2011-07-29
Look at what it is like now

---

