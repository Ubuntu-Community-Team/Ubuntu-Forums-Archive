---
title: "help backing up a Hard drive"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by tsalib on 2010-02-18
I have a pc that I turned in to my server using ubuntu server 9.10 I have placed 2 hard drives in this unit I need to know an easy way to copy all info from my main to my back up HDD can someone please help me I know I can find this or raid these to I am just bound by finacial restrictions (a girl friend that will not alow me any money for my computer habit)

---

### Post by 2hot6ft2 on 2010-02-18
Are you wanting to clone the drive? Or do you have something else in mind?

---

### Post by 2hot6ft2 on 2010-02-19
I'm going to bed so here it is if you want it.

**Cloning a drive with dd**

The iformation given here is a collaberation from these sources that I saved for my own future reference and use:
[http://www.justlinux.com/forum/showthread.php?threadid=134457](http://www.justlinux.com/forum/showthread.php?threadid=134457)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/archive/index.php/t-1080626.html](http://ubuntuforums.org/archive/index.php/t-1080626.html)

Boot from livecd/dvd
Applications > Accessories > Terminal

To get the needed info
```
sudo fdisk -l
```
Turn off the swap so it's not trying to use it and copy it at the same time
```
sudo swapoff
```
Type in the following command, replacing SOURCE with the name of the source drive and DESTINATION with the name of your destination drive:
```
dd if=/dev/SOURCE of=/dev/DESTINATION bs=32256 conv=notrunc,noerror,sync
```
it will look similar to 
```
dd if=/dev/sda of=/dev/sdh bs=32256 conv=notrunc,noerror,sync
```
In the above "if" is the input device and "of" stands for the output device. The Block size parameter bs has been chosen to be one complete track of 64 sectors each 512 bytes. Omitting the bs parameter will cause dd to default to 512 bytes in each transfer and this slows down the cloning. The 32256 is about the optimum.

notrunc tells dd not to abbreviate blocks of all zero value, or multiple adjacent blocks of zeroes, with five asterisks (when you want to maintain size) Do not use notrunc for copying a larger volume to a smaller volume. noerror and sync are pretty self explanitory.

Make absolutely sure you have them right before hitting Enter or you might wipeout your source drive.

To clone only one partition from the source drive, specify the partition (e.g., /dev/sda1 or /dev/sda2). To clone the entire drive, specify only the drive name, with no partition number (e.g., /dev/sda).

Wait. Cloning a large drive using dd can take hours, and according to some accounts, even more than a day depending on your system the size of the drives and how much data is on them.

Learn more about using the dd command here:
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Other options like using GParted and ddrescue can be found here:
[http://ubuntuforums.org/archive/index.php/t-1080626.html](http://ubuntuforums.org/archive/index.php/t-1080626.html)
GParted can clone a HDD itself? Simply copy/paste? Right from Ubuntu Live CD?

dd does not output any information until the process is completed. The flickering LED of the hard disk tells us dd is busy. On completion dd will always report the number of records, each equal to the the specified block size, transferred. Multiplying the record number with the block size should correspond to the capacity of the source hard disk.

I recommend removing the source disk, put it away for safe keeping as the backup, install the cloned disk in its place and start using the new disk right away.

For those who is not already aware dd stands for "data dump" meaning the binary pattern from a source disk is read and then written on the target disk. Technically it is impossible to clone a disk that is not a 100% carbon copy of the original.

The newly cloned disk's extra capacity over and above the original disk simply become the unallocated hard disk space which can be absorbed into the existing partitions by gparted or Parted Magic. It is recommended the current versions of these software to be downloaded and run as Live CD.

It has been my experience the whole hard disk cloning will always work on XP and Vista. 

The current Live CD versions of gparted and Parted Magic are good for resizing XP. To resize Vista I recommend using its own internal resizer program which is faster and the success is guaranteed by M$.

It is recommended Vista to be cloned as the whole hard disk. This is because the current Vista has a new MBR and will conduct a check on the partition table. It can use a change to the partition table, between a reboot, as an excuse for the security risk to refuse to boot. Cloning the whole disk gives Vista no such excuse because the partition table isn't changed. Vista will still be able to detect the hard disk has been altered and demands an immediate reboot, same as XP. After a reboot Vista will work normally after the hard disk serial number has been updated.

I had no problem booting right up to the new drive. Grub2 worked fine so I booted into windows to let it do it's check.
Then reboot to the livecd/dvd and resized my partitions.

If you have grub2 problems just reinstall grub2 like this:
Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda7,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:

To get the info needed use:
```
sudo fdisk -l
```
Then to actually do it use:
```
sudo -i
```
```
mount /dev/sda7 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda

```
Replace sda7 and sda6 with those for your setup.

From here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by tsalib on 2010-03-27
Cloning is fine I just want to be able to pull my back up drive out and replace the primary if my primary goes bad with minamal loss of data I mainly use this for a file server and nothing more

---

### Post by bumanie on 2010-03-27
Firstly, I would consider getting a new girlfriend, alternatively, follow above and use dd commands. I usually shrink the partition to a bit above the amount of data it has on it and then do dd and then resize back to the original. A bit of mucking around, but if one does a few 'full images', storage space gets used up very quickly.

---

### Post by NickJones on 2010-03-27
Ghost for Linux is your friend.
[http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)

---

### Post by NickJones on 2010-03-27
> **NickJones said:**
> Ghost for Linux is your friend.
[http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)
"G4L is a hard disk and partition imaging and cloning tool. The created images are optionally compressed and transferred to an FTP server or cloned locally. Version 0.30 adds cifs (Windows) on local menu, and mbr and ebr backup."
In short, it creates an *identical* copy of your current HDD.

---

### Post by BogdanMare on 2010-09-27
Hi people,

As I am new to this forum and also to the "linux world" (I have about 2 months of succesfull, "study-hard", pleasureful linux experience - Ubuntu 10.04 distro).
I just finished installing a mail and web server and after almost 2 weeks spent on configuring it to work right I want to make sure I wont have to do it again :)).

I heard a couple of things about this "dd" command and I what to be sure I got it right. 
First of all, let me explain what I have and what I want to do with what I have ;)
- I have one 320 GB HDD which containes the linux OS + email&web servers
- I have another 80GB HDD which containes some data (dont know what exactly)
- I want to copy the contents of the 320 GB HDD (out of which maybe 30-40 GB is being used) to the 80 GB HDD. This means an EXACT replica of the OS with the settings for the servers, etc.
- I will connect the two HDD on SATA and boot-up ubuntu from a live CD and from there run "dd", right?!

Now for the questions :D
- Can the 80GB HDD be used in this case or do I need at least a 320 GB HDD (same as the original HDD containing the OS)?
- Does the 80GB HDD have to "clean" (Unllocated space), or will "dd" erase all data from the 80GB HDD and replace it with the contents of the 320 GB HDD?

If you have any other sugestions please tell me :)

Thanks in advanced! ;)

---

