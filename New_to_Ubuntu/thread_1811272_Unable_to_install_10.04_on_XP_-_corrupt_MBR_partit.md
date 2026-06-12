---
title: "Unable to install 10.04 on XP - corrupt MBR partition table"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by user_linux on 2011-07-24
During ubiquity installer I get no root  filesystem defined. This is a wubi install so the filesystem is  automatically specified... the bootinfoscript shows some MBR partition  table corruption:
 ============================ Drive/Partition Info: =============================
 Drive: sda _____________________________________________________________________
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 /dev/sda1    *             63    95,561,994    95,561,932   7 NTFS / exFAT / HPFS
/dev/sda2          95,563,774   147,814,064    52,250,291   5 Extended
Extended partition linking to another extended partition.
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.
/dev/sda3         147,828,240   156,295,439     8,467,200  12 Compaq diagnostics
 "blkid" output: ________________________________________________________________
 Device           UUID                                   TYPE       LABEL
 /dev/loop0                                              squashfs
/dev/sda1        BEE00CEDE00CADA9                       ntfs       IBM_PRELOAD
/dev/sda3        1B33-0A00                              vfat       IBM_SERVICE


For detailed info please see:[http://pastebin.ubuntu.com/651258/](http://pastebin.ubuntu.com/651258/). Please include detailed steps as to how to solve this issue.
Thank you very much!

---

### Post by oldfred on 2011-07-24
I do not know how to do this from windows. These are Linux commands but I do not think they work from wubi.

But I believe there is a windows version of this:
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You should back up partition table first just in case. Again not sure if it works from wubi.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Linux quick way but I would not run from wubi:
Extended partition linking to another extended partition
Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect.

---

### Post by user_linux on 2011-07-24
Ok, thats encouraging to hear its easy to fix. But I will tell you my current situation. I don't have wubi running yet. I have only installed it, but when I was about to boot it for the first time, I received the message "No root file system is defined." message. Right now I only have ubuntu 10.04 live cd and your steps in linux didn't work. I don't know what Supergrub is. Also, I downloaded fixparts but everytime I give a command and press enter it closes. So, I'm in a very messy situation.
Thanks.

---

### Post by oldfred on 2011-07-24
from the liveCD you should be able to run the fdisk command. Supergrub is just another way to get a broken system to boot including most systems using windows or grub.

Post PT.txt

Are you getting any error messages from fixparts?

---

### Post by user_linux on 2011-07-24
> **oldfred said:**
> from the liveCD you should be able to run the fdisk command. Supergrub is just another way to get a broken system to boot including most systems using windows or grub.

Post PT.txt

Are you getting any error messages from fixparts?
I am not getting any error messages from fixparts. It just closes when I press enter in windows xp. In live cd ubuntu, when I extract fixparts, there are so many files, I just don't know which one to choose.  When I type"sudo sfdisk -d /dev/sda > PT.txt", the result I'm getting:
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
When I type sudo fdisk /dev/sda, the result I'm getting:
"Unable to seek on /dev/sda"
So, i have no idea what to do?

---

### Post by oldfred on 2011-07-24
The sfdisk error is expected, but is it writing PT.txt to your home.

Did you download the windows version of fixparts. He has several versions.

Fixparts should be just the program. What else are you getting?

---

### Post by user_linux on 2011-07-24
> **oldfred said:**
> The sfdisk error is expected, but is it writing PT.txt to your home.

Did you download the windows version of fixparts. He has several versions.

Fixparts should be just the program. What else are you getting?
When I downloaded the windows version of fixparts, I extracted the folder on my desktop, and then I ran gdisk.exe and a command prompt window appeared. Then, I typed in \\.\physicaldrive*# *but as soon as i pressed enter to execute the command, the window closed automatically. I'm not sure what would be another way to run the command prompt.

---

### Post by oldfred on 2011-07-24
You should not need gdisk but just the program fixparts. Gdisk is primarily for creating and editing gpt partitioned drives which is the future. But you have MBR(mdos) partitioning and should just need fixparts.

---

### Post by bcbc on 2011-07-24
To run a command line program in XP, click START, Run, and enter "CMD" to get to a command prompt. If you run command line programs from Windows Explorer, the command window will close before you can see any output so you have no idea if there were errors or not.

Also don't run things if you aren't sure what you are doing. As *oldfred* said, you should only need fixparts, but you are running gdisk. 

Also, when you mess with anything to do with the partition tables you need to back up everything before hand - if you have personal data you don't want to lose then it's important to stop and back it up. If you need to restore the partition table, it's important to understand how to do this - and have the rescue disks you require, before you make changes.

PS *oldfred*, I suggested the OP post here (after [this]("https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/165054") original post). So I apologise if it seems I am jumping in. I'll back away slowly now ;)

---

### Post by user_linux on 2011-07-24
Hmm, ok, I went to [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/) and downloaded [[COLOR=#006699]fixparts-0.7.1-windows.zip[/COLOR]]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/fixparts-0.7.1-windows.zip/download") on my desktop. Now, like you say about running this file, when I open fixparts, no matter what I type I still close the window. Even when I type [[FONT=Courier New]\\.\physicaldrive[/FONT]]("file://\\.\physicaldrive")*[FONT=Courier New]# [/FONT]*in cmd, I receive "The filename, directory name, or volume label syntax is incorrect". I think I'm doing something wrong. so guys please explain me in detailed steps as to how should I run this fixparts.[FONT=Courier New][/FONT]

---

### Post by srs5694 on 2011-07-24
To run FixParts in Windows XP, you should:


[list=1]
[*]Open a Command Prompt window.
[*]Type "fixparts 0:" in the Command Prompt window, changing "fixparts" to include its complete path if necessary and changing "0:" to the drive number (probably 0 if it's /dev/sda in Linux, but that's not guaranteed).
[/list]


The Command Prompt window should not close when you do this. If FixParts is crashing, please post any text that it does display.

All that said, I'm uncertain that FixParts will be able to help. The error you reported from fdisk suggests that your partition table is corrupted in a way that FixParts might not be able to repair. It could be you'll need to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover your logical partitions.

One more tip: When posting program output, it's helpful to enclose it in [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This preserves the original formatting and keeps it legible.

---

### Post by user_linux on 2011-07-25
Ok, so now I went to command prompt, ran as an admin, typed "fixparts 0:" and received message: 'fixparts' is not recognized as an internal or external command, operable program or batch file. Then I typed in the complete file path where I have extracted the fixparts.exe file alongwith 0: in the end, but still the same message I wrote earlier. As usual if I run fixparts.exe file, the window still closes upon pressing enter without posting any text. So, am I doing something wrong again?

---

### Post by srs5694 on 2011-07-25
The "is not recognized" message means that the program isn't on your path and you have not specified the correct path. Try using "cd" in the Command Prompt window to change to the directory where the .exe file exists and then typing ".\fixparts 0:".

---

### Post by user_linux on 2011-07-25
OK, so I ran fixparts and typed in p to print MBR partition table. I have also attached a screen shot in under [http://imagebin.org/164877](http://imagebin.org/164877) heading Output. Please explain me slowly and in detailed steps what to do next to rectify the whole issue so that I can start running ubuntu again from wubi.
Thanks.

---

### Post by srs5694 on 2011-07-25
The good news is that FixParts seems to have read more of your partitions than fdisk or Boot Info Script did, judging from your first post. The bad news is that there may still be a missing partition, since there's a gap between sectors 133160959 and 147091203 -- about 6.6 GiB.

My inclination would be to take what you can get from FixParts and type "w" at its "MBR command (? for help):" prompt to save its changes. Then, if you find that something is missing, you can run [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover that missing partition.

One comment, though: You appear to have a conventional partitioned Linux installation. You could also have a WUBI installation in addition to that, but the partition identities and layout imply a regular partitioned Linux installation.

---

### Post by user_linux on 2011-07-26
Hi, so I ran fixparts with w and I am putting the output again in [http://imagebin.org/165044](http://imagebin.org/165044) under heading Output_1. Surprisingly, booth my screenshots look same. What should I do next?

---

### Post by srs5694 on 2011-07-26
What problem are you experiencing now? For instance, can you not boot an OS, or not use certain partitions, or what?

---

### Post by user_linux on 2011-07-27
So I tried to boot into Ubuntu again, it gets past the % installation screen where I was experiencing the problem earlier,but now in "Checking the installation" window title, I receive the following message: 
Installing the system
0% (progress)
Formatting swap space in partition #1 of /host/ubuntu/disk...

and it just sits there.

Any advice? 

Thanks!

---

