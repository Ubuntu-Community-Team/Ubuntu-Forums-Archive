---
title: "vista boot error (vista and ubuntu dual booted)"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Xender1 on 2009-03-22
So here is whats going on.....
When I choose to boot vista it goes to a black screen, stays there for a minute or two, and then throws back a Windows Error Recovery screen the the info: unexpected I/O error.

That sucks...so I popped in my vista recovery cd hoping that a simple repair would work.

When it loads from the recovery disk it loads the windows files, then goes to the vista load screen (just the things going by in the loading bar) and then ends up dumping me off at a black screen with just a cursor.

From here I cannot do anything (ctrl+alt+delete does not bring up anything etc..)

So, yay for having ubuntu on another partition. In ubuntu (after looking up some things to do) here is what I have tried so far, but no success.

Let me preface this with saying that I am an ubuntu nub, but love it, and because of this vista problem all I want (/am hoping to get) is the data from my vista partition (some files that are very important especially on projects that I have been working on for school).

typing fdisk -l in terminal returns:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14253   114487191    7  HPFS/NTFS
/dev/sda2           14254       19457    41801130    f  W95 Ext'd (LBA)
/dev/sda5           14254       19238    40041981   83  Linux
/dev/sda6           19239       19457     1759086   82  Linux swap / Solaris

/dev/sda1 is my vista partition.

Trying to mount this (with ntfs-3g and other programs (Mount Manager/Gparted) returns an error all along the same lines of the error im getting when trying to boot to vista:
(this is the response from  sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force)
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

So next step for me was testdisk. One thing I notice right at the start of testdisk is after i choose to create a new log file on the next screen i notice that my choice for media to mount the size is 160GB/149GB (perhaps another problem in itself). I hit enter for proceed.
Then enter again on the Intel option
Then enter for analyse. this returns:
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1 14252 254 63  228974382 [SW_Preload]
 2 E extended LBA         14253   0  1 19456 254 63   83602260
 5 L Linux                14253   1  1 19237 254 63   80083962
   X extended             19238   0  1 19456 254 63    3518235
 6 L Linux Swap           19238   1  1 19456 254 63    3518172

After this I hit enter on Quick Search and then Y for Vista. returns:
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 14252 254 63  228974382 [SW_Preload]
L Linux                14253   1  1 19237 254 63   80083962
L Linux Swap           19238   1  1 19456 254 63    3518172

after this I dont hit anything because I am not sure what the options will do and they seem to be pretty intense things.

Anyhelp on continue through testdisk after that step to fix the partition or is there a different course to go? Thanks so much for reading sorry if its to much or not.

---

### Post by Melk79 on 2009-03-23
This link seems to be similar and have a solution. 
[http://ubuntuforums.org/showthread.php?t=663452](http://ubuntuforums.org/showthread.php?t=663452)

The other thing I would try for the data part is using just the LiveCD rather than booting into Ubuntu.  I've used those many times to get data off of Windows PC's with serious trouble and it has worked.

---

### Post by Xender1 on 2009-03-23
The only problem is that when using the vista recovery disk, all I get is a black screen with a cursor. No matter what I do thats all there is. Also from looking around I am not sure if this makes a difference but my vista recovery disk is on a cd not a dvd... difference?

---

### Post by gn2 on 2009-03-23
Is it [this Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or a CD that was supplied with a pre-built laptop or PC?

Something to try, get the hard drive out, put it in a USB enclosure and connect it to another booted Windows PC then "Safely Remove" it.

---

### Post by tarps87 on 2009-03-23
It is possible it is a dos prompt. From memory of repairing a mates vista pc this is what the recovery option boots into, try typing help and see if it gives you a list of commands.

---

### Post by Xender1 on 2009-03-23
ok so for some strange reason, I put in the recover disk, went to class, came back, and had the correct screen. i hit next and then click repair, but the repair screen cannot find the vista partition (there are no options to choose from to repair). i can still hit next and have all the options including to repair, should i click repair and see if it works?

---

### Post by Xender1 on 2009-03-23
ok another thing i tried was with the LiveCD attempting to mount it via that, still same problem as in the first post. 
[This is the recovery disk]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") I am using to get vista back.

on repair the system recovery options does not show the vista operating system, but i am able to acces the command prompt off of the vista disk. Any commands i can do from there to try and fix/gain access to my vista partition again?

---

### Post by tarps87 on 2009-03-24
You can try using the dos prompt to navigate to you work, if succeed you will be able to copy the data off.
**cd** is this same a in Ubuntu (change directory)
**dir** lists all the files in the directory

It sounds like your partition is corrupted. This type of thing has happened to a friends pc but he only had vista on it, I tried the Ubuntu live cd and the vista recovery cd and neither could see the document/users directory, unfortunately the solution (according the company that make the pc) was to send it back and have a new hard drive installed. I don't think it was a hard drive issue and also don't think your problem is hard drive related.

Some useful dos commands:
**chkdsk** = check disk
**copy** = copy
**recover** = tries to recover information from a bad or defective disk
**xcopy** = copy (ignores copy rules so is more successful at copying system files)

(I have never used the **recover **option so I can't help with using it, someone else here may be able to help)

---

