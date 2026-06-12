---
title: "External USB Hard Drive - Help Needed"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by kapilapshankar on 2009-02-07
[FONT="Georgia"]
I am in my first week of Ubuntu 8.10 and pretty much a newbie.

Here's the problem: I had an external USB hard drive connected to my Ubuntu laptop. It must have been NTFS - since  I had  transferred data on it using my other WinXP laptop.

It was auto-recognized, and mounted in Ubuntu. I moved data to it after enabling the NTFS option enabled. 

I then shut down my Ubuntu machine, unplugged the external HD - and now it is not recognized on either WinXP or Ubuntu.

Here's what I get:
ubuntu@ubuntu:~$ sudo lsusb
Bus 004 Device 005: ID 059b:0370 Iomega Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and then:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        6834    54837877+   7  HPFS/NTFS
/dev/sda3            6835        7295     3702982+  db  CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88af9a0d

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 

I don't see the partition table for my external HD.

But looks like Ubuntu is recognizing some sort of HD connected to it:
ubuntu@ubuntu:~$ sudo lshw -businfo -C disk
Bus info          Device      Class          Description
========================================================
scsi@0:0.0.0      /dev/sda    disk           60GB FUJITSU MHV2060A
scsi@1:0.0.0      /dev/cdrom  disk           DVD+-RW ND-6650A
                  /dev/cdrom  disk           
scsi@4:0.0.0      /dev/sdb    disk           500GB SCSI Disk
ubuntu@ubuntu:~$ 

Consequently, I cannot mount this HD:
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb /media/external
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
ubuntu@ubuntu:~$ 

What's happening here? What do I need to do? 

I have close to 50GB data on this HD that I need to get back - either in Ubuntu or WinXP.

Please help. 

[/FONT]

---

### Post by blueridgedog on 2009-02-07
I recommend you examine the disk using testdisk.

```
sudo apt-get install testdisk
```

I am not an expert with testdisk, but it will either recover your partition table or allow you to copy files from the disk to a recovery folder on another drive.  There are many threads that talk about using testdisk, for example:

[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

When you run it, (sudo testdisk) you will need to select create a log file, then select /dev/sdb1, then INTEL/PC Partition.

Choose 'Analyze' then 'Proceed', after that it depends on the results you get. TestDisk should now scan your device for partitions (If it hasn't already discovered them). The process could take a while.

---

### Post by caljohnsmith on 2009-02-07
Since you are trying to recover an NTFS partition, I would recommend using the latest stable version of testdisk which is 6.10. How about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sdb USB HDD and "Proceed", "Intel", "Analyze", "Quick search", "N" to search for Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and which partition seems to be your lost data partition. We can work from there if you want.

---

### Post by blueridgedog on 2009-02-07
I was hoping you would jump in...I have seen you work with others using teskdisk (in fact I learned about it from another post where you gave an overview of it).

---

### Post by caljohnsmith on 2009-02-07
> **blueridgedog said:**
> I was hoping you would jump in...I have seen you work with others using teskdisk (in fact I learned about it from another post where you gave an overview of it).
Well I'm no expert with testdisk, but fortunately it isn't complicated to use once you have a little experience with it. It sure is a powerful program, and I'm amazed sometimes at the things it can do. Hopefully it will be able to find kapilapshankar's lost partition, although I'm wondering what happened in the first place how kapilapshankar's partition would have gotten deleted somehow. Thanks much for the positive feedback, I'm glad at least a few of my posts are useful to someone. :)

---

### Post by kapilapshankar on 2009-02-07
I'd already started with 6.9 - so couldn't go ahead with 6.10.

Here's what I got:

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 60800 254 63  976768002 [Iomega_HDD]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 500 GB / 465 GiB

And listing the files gives me this:
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

   * HPFS - NTFS              0   1  1 60800 254 63  976768002 [Iomega_HDD]
Use Right arrow to change directory, c to copy, q to quit
Directory /

dr-xr-xr-x     0     0         0  9-Sep-2008 02:24 .
dr-xr-xr-x     0     0         0  9-Sep-2008 02:24 ..
dr-xr-xr-x     0     0         0 16-Jan-2009 17:23 Jingle Toons
dr-xr-xr-x     0     0         0  5-Feb-2009 20:56 Kapil Laptop Data
dr-xr-xr-x     0     0         0 25-Jan-2009 21:53 Laptop Backups
dr-xr-xr-x     0     0         0  5-Jan-2009 04:14 Movies
dr-xr-xr-x     0     0         0 10-Jan-2009 15:13 Music
dr-xr-xr-x     0     0         0 19-Jan-2009 17:44 Photos
dr-xr-xr-x     0     0         0 16-Jan-2009 19:14 RECYCLER
dr-xr-xr-x     0     0         0  9-Sep-2008 02:24 System Volume Information
dr-xr-xr-x     0     0         0 16-Jan-2009 18:59 Videos

Wow! I see my data here.

Now what? I don't want to mess things up from here.

It's about 50GB of data and not sufficient space on my local HD to copy it over there.

Won't do anything till I hear back from you. Thanks a bunch!

---

### Post by caljohnsmith on 2009-02-07
Great, glad to see that testdisk found your lost partition. The partition is shown marked with a "*" in front of it right now which is fine, so if you just press "enter" to get to the next screen, you can then choose "Write" so that testdisk will write the new partition table with that partition. Then reboot, and if all goes well you should be all set. Let me know if you run into problems though.

---

### Post by kvk on 2009-02-07
What happens if Testdisk cannot identify any partitions on the USB drive?

---

### Post by kapilapshankar on 2009-02-07
[FONT="Georgia"]
Hooray! I got all my data back.

TestDisk saved my day. 

Thanks a tonne, caljohnsmith and blueridgedog for putting the smile back on my lips tonite :D
[/FONT]

---

### Post by caljohnsmith on 2009-02-08
Glad to hear that worked OK, kapilapshankar. Hopefully whatever happened that the partition was accidentally deleted won't happen again. Cheers and hope your Ubuntu experience goes smoother from now on. :)



> **kvk said:**
> What happens if Testdisk cannot identify any partitions on the USB drive?
If that's the case, then at least in my experience, you usually have to resort to something like "photorec" to just try and recover whatever individual files can be found on the drive. Thankfully that was not the case for kapilapshankar.

---

### Post by egalvan on 2009-02-08
> **kapilapshankar said:**
> [FONT="Georgia"]
Hooray! I got all my data back.

TestDisk saved my day. 

Thanks a tonne, caljohnsmith and blueridgedog for putting the smile back on my lips tonite :D
[/FONT]

Echoing caljohnsmith, I'm glad that testdisk worked so well for you.

But may I add one more thought?

I know many (in the "free-as-in-beer" community) don't agree with me on this, 
but you may want to consider a small donation to the authors of this program.

I used it, it worked well for me, so I donated $10 (I am still using it).

Even a $5 donation would be helpful to the authors.
(and I bet even $1 is good)

CAUTION!!
MY PERSONAL OPINION on this:
We need to get past the "it-doesn't-cost-a-dime" attitude and start sending some financial support to the authors of well-written software.
Yes, being cost-free is a tremendous advantage, but once we find that the software works well, let's help out.
(if the software doesn't work for you, then remove it. It didn't cost you anything. The advantage is still there).

I think the Linux community, and the Ubuntu folks, should look at this.

and one last though-provoker to the OP:
this software saved you 50GB of precious data...
what would Bill Gates *et al* have charged you for the privilege?

Donate or not.
You do have a choice.
It's what makes Linux so strong.

ErnestG

**[COLOR="Red"]I HAVE NO CONNECTION WITH ANY AUTHORS OF FOSS/OSS SOFTWARE[/COLOR]**

---

### Post by mkvnmtr on 2009-02-08
Since the thank you button is disabled for a while I would like to say thanks for the information in this thread. Also Ernest has a good point about helping out the authors of software that helps us.

---

### Post by blueridgedog on 2009-02-08
> **egalvan said:**
> 
I know many (in the "free-as-in-beer" community) don't agree with me on this, 
but you may want to consider a small donation to the authors of this program.



I don't know many in the FOSS community that object to buying software that you appreciate or donating to software projects that you want to support.  I generally donate as well to projects that I use.

> **kapilapshankar said:**
> [FONT="Georgia"]
Hooray! I got all my data back.

TestDisk saved my day. 

Thanks a tonne, caljohnsmith and blueridgedog for putting the smile back on my lips tonite :D
[/FONT]

Bravo!  I hope you don't have this issue again.

---

