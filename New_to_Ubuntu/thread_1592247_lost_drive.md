---
title: "lost drive"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by bj218 on 2010-10-10
Please Please help me my 250GB drive is gone. All my linux partitions were on this drive ie
Mint & Ubuntu, plus I have 4 other partitions ie 1 partition with my family & Xmas list,1
partition with all my medical info for the last 10 years,1with the last 10 years of fed/ca
income tax data,1 with Ubuntu/Mint info. that I have downloaded from the internet. I
downloaded this program “Go to sourceforge and download and burn the ISO for System
RescueCD at no more than 8X [http://sourceforge.net/projects/systemr](http://sourceforge.net/projects/systemr) ... o/download “ I then burned a CD & ran it when it
displayed a small terminal screen with gparted in it I knew I had a big problem. Why this
program did not warn me at least several times that it was going destroy my drive I don't
understand. Is there any way I might salvage my data?

---

### Post by Quackers on 2010-10-10
The link you gave returns an error 404, so doesn't work for me. What is the program that you downloaded?
If all else fails there is a program called Testdisk in the repositories with which some people have had very good results.
Hopefully one of the partition gurus will see this and make suggestions for you.
All is not necessarily lost.

---

### Post by sikander3786 on 2010-10-10
The link is not opening up here either.

Can you boot into a live cd and post the output of

```
sudo fdisk -l
```

This page is also worth reading.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bj218 on 2010-10-11
> **Quackers said:**
> The link you gave returns an error 404, so doesn't work for me. What is the program that you downloaded?
If all else fails there is a program called Testdisk in the repositories with which some people have had very good results.
Hopefully one of the partition gurus will see this and make suggestions for you.
All is not necessarily lost.

Go to sourceforge and downloand and burn the ISO for SystemRescueCD at no more than 8X [http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/systemrescuecd-x86-1.3.5.iso/download](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/systemrescuecd-x86-1.3.5.iso/download)
This is where I got the prog. At the moment I have the drive disconnected.

---

### Post by Quackers on 2010-10-11
I can't see why a system rescue cd .iso would cause serious problems.
Can you boot into a Ubuntu Live cd and run the boot_info_script and post the contents of the results.txt in your next post - using the CODE tags (click on # symbol in New Reply window and paste between)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bj218 on 2010-10-11
> **Quackers said:**
> I can't see why a system rescue cd .iso would cause serious problems.
Can you boot into a Ubuntu Live cd and run the boot_info_script and post the contents of the results.txt in your next post - using the CODE tags (click on # symbol in New Reply window and paste between)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This is what I got!!

bill@bill-desktop:~$ boot_info_script
boot_info_script: command not found
bill@bill-desktop:~$ run boot_info_script
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
bill@bill-desktop:~$

---

### Post by sikander3786 on 2010-10-11
> **bj218 said:**
> This is what I got!!

bill@bill-desktop:~$ boot_info_script
boot_info_script: command not found
bill@bill-desktop:~$ run boot_info_script
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
bill@bill-desktop:~$
Instruction to run boot_info_script are present on the home page.

> Open a terminal (Applications>Accessories>Terminal in Gnome) and type

```
sudo bash [path/to/the/download_folder]/boot_info_script*.sh
```

For example if you downloaded the file to the desktop, use

```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by bj218 on 2010-10-13
> **sikander3786 said:**
> The link is not opening up here either.

Can you boot into a live cd and post the output of

```
sudo fdisk -l
```

This page is also worth reading.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 100.0 GB, 100030242816 bytes 
255 heads, 63 sectors/track, 12161 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0d4057a2 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS 
/dev/sda2            6375        8288    15374205    f  W95 Ext'd (LBA) 
/dev/sda5            6375        7012     5124703+   7  HPFS/NTFS 
/dev/sda6            7013        7650     5124703+  83  Linux 
/dev/sda7            7651        7778     1028128+  82  Linux swap / Solaris 
/dev/sda8            7779        8288     4096543+  83  Linux 
omitting empty partition (5) 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x761c12f3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS 
/dev/sdb2            6375       19457   105089197+   f  W95 Ext'd (LBA) 
/dev/sdb5           14024       14661     5124703+   7  HPFS/NTFS 

Disk /dev/sdc: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0002fe5b 

Disk /dev/sdc doesn't contain a valid partition table 
ubuntu@ubuntu:~$ 
I hope the above helps.
I have been having trouble with my modem since last Friday & Verizon said they would have someone come out & ck it I am still waiting!! It seems to
be working this morning ?

---

### Post by sgosnell on 2010-10-13
That says your 250GB drive doesn't have a valid partition table.  I have no idea how it got hosed, but it apparently did.  Google will give you a number of hits on tutorials for restoring the partition table.  After you restore it, use [this tutorial](http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html) for making a backup, and having it available for restoration if it happens again.

If you have data on a drive that you absolutely have to keep, you need to make at least one backup of it.  There are a number of ways to do this, including using another drive, using DVDs, and using an online service.  UbuntuOne lets you store a couple of GB of files, but I prefer Dropbox, because it's available for most OS's, and lets me access my files from almost anywhere.  These allow more storage for a fee, and there are also other fee-based services available.  Never, ever keep essential data in only one place, because Murphy is always lurking nearby.

---

### Post by Quackers on 2010-10-13
Although I have not used it myself, people have had good results with Testdisk (available through Synaptic)

---

### Post by cariboo on 2010-10-13
+1 for testdisk, I had a hard drive with a corrupted partition table and it restored the partitons allowing me to backup the drive before sending it away for warranty replacement.

---

### Post by bj218 on 2010-10-15
> **Quackers said:**
> Although I have not used it myself, people have had good results with Testdisk (available through Synaptic)

I went to synaptic & down loaded Testdisk but I am unable to find it. Do 
you know where I should look for it? I don't know if you can view this screen shot but if you can it might help!! 

it.home/bill/Desktop/Screenshot.png

---

### Post by kroq-gar78 on 2010-10-15
run this from command line (Applications => Accessories => Terminal):
```
sudo apt-get install testdisk
```
input your password when it prompts you to and input "Y" (no quotes) (if it asks). Wait for it to install and its installed

---

### Post by bj218 on 2010-10-15
> **kroq-gar78 said:**
> run this from command line (Applications => Accessories => Terminal):
```
sudo apt-get install testdisk
```
input your password when it prompts you to and input "Y" (no quotes) (if it asks). Wait for it to install and its installed

bill@bill-desktop:~$ sudo apt-get install Testdisk
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Testdisk
bill@bill-desktop:~$ 

bill@bill-desktop:~$ sudo apt-get install testdisk
[sudo] password for bill: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bill@bill-desktop:~$ sudo apt-get install testdisk
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bill@bill-desktop:~$

---

### Post by kroq-gar78 on 2010-10-15
package names (e.g. testdisk) are NEVER uppercase in any way shape or form (took me a while to find that out). on the second command, was there an update manager running or a software center (or synaptic) running? If so, that's why you're getting the error. Otherwise, re-run the command when none of them are running or just reboot/ logout.Report back with the command I had posted earlier:
```
sudo apt-get install testdisk
```

---

### Post by bj218 on 2010-10-16
> **kroq-gar78 said:**
> package names (e.g. testdisk) are NEVER uppercase in any way shape or form (took me a while to find that out). on the second command, was there an update manager running or a software center (or synaptic) running? If so, that's why you're getting the error. Otherwise, re-run the command when none of them are running or just reboot/ logout.Report back with the command I had posted earlier:
```
sudo apt-get install testdisk
```

This is what I got this afternoon. Still can't find testdisk!!

bill@bill-desktop:~$ sudo apt-get install testdisk
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
testdisk is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bill@bill-desktop:~$ sudo apt-get autoremove linux-headers-2.6.31-14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 82.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135905 files and directories currently installed.)
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
bill@bill-desktop:~$

---

### Post by Quackers on 2010-10-16
What happens if in the terminal you type
testdisk
and hit enter?

---

### Post by bj218 on 2010-10-16
> **Quackers said:**
> What happens if in the terminal you type
testdisk
and hit enter?

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Here it is!
TestDisk is a free data recovery software designed to help recover lost
partitions and/or make non-booting disks bootable again when these symptoms
are caused by faulty software, certain types of viruses or human error.
It can also be used to repair some filesystem errors.

Information gathered during TestDisk use can be recorded for later
review. If you choose to create the text file, testdisk.log , it
will contain TestDisk options, technical information and various
outputs; including any folder/file names TestDisk was used to find and
list onscreen.

Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything

---

### Post by Quackers on 2010-10-16
Aha! You found it :-) Here is the Testdisk step by step guide (in case you don't have it). Good luck!
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by bj218 on 2010-10-19
> **Quackers said:**
> Aha! You found it :-) Here is the Testdisk step by step guide (in case you don't have it). Good luck!
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Thank you much it looks like I got everything but ubuntu. Now I need to copy
my other partitions to another (backup) drive. Can you tell me how to do this? Can I go to terminal & do cp ie copy the partitions to another drive!!

---

### Post by Quackers on 2010-10-19
This is my second reply to this tonight. Is it me or is the forum virtually unusable tonight?

So bj218, some success, I'm glad to see :-)

Unfortunately you cannot just cp partitions/drives. I have seen some people using a dd command, which copies partitions/drives on a bit by bit basis, which is what you want, I believe. Sadly I don't know the structure of that command so cannot help any further. Hopefully someone will come along who can give further details. Good luck to you.

---

### Post by sgosnell on 2010-10-19
Are all those partitions on one drive?  Are they primary partitions?  You can only have a total of 4 primary partitions on a drive.  You can get around this limitation by using extended partitions inside a primary partition, but I don't know how you set yours up.

dd is what you want for copying entire partitions.  The man pages for dd will explain how to use it.  The basic syntax is ```
dd if=input_file of=output_file
``` where the input and output files can be a drive, a partition, or a file.  You really want to read the man pages carefully before doing the copy.

---

### Post by bj218 on 2010-10-28
> **sgosnell said:**
> Are all those partitions on one drive?  Are they primary partitions?  You can only have a total of 4 primary partitions on a drive.  You can get around this limitation by using extended partitions inside a primary partition, but I don't know how you set yours up.

dd is what you want for copying entire partitions.  The man pages for dd will explain how to use it.  The basic syntax is ```
dd if=input_file of=output_file
``` where the input and output files can be a drive, a partition, or a file.  You really want to read the man pages carefully before doing the copy.

Re "dd"how do I get the man pages?

---

### Post by CharlesA on 2010-10-28
Doesn't this work:

```
man dd
```

---

### Post by bj218 on 2010-10-29
> **CharlesA said:**
> Doesn't this work:

```
man dd
```

This worked great. THANKS TO ALL for all your help I really needed it!!

---

