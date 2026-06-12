---
title: "Dualbooted but Cannot boot any OS - please help"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2010-07-24
I had dual booted Windows Vista and Ubuntu 9.04. I opened the comp after a long time. and found that the Grub Bootloader did not load it displayed error 16. To troubleshoot this, I thought of reinstalling Ubuntu and inserted the Cd. While installing, it gave me another error with a lot of code
a DRDY error. I did a cold shutdown by pressing the power button as there was no other option. when I turned my comp on again the screen goes blank it does not even load the bootloader. I am not able to boot either OS.
I pressed esc to the bootmenu and the option to boot from hard disk has disappeared. In trying to boot from the liveCD, I selected the option "boot from local hard disk" and it throws up this error.
[B]Booting from local hard disk
isolinux : Disk error 01, AX=0201, drive 80
Boot failed Press any key to continue..[/B] 
When I try to install Ubuntu 9.04
**The partition manager shows NO partitions. says no root file system is defined.**

So I have a dual boot OS but cannot boot etther of them. Is there any way to solve this problem or at least recover my HDD data??

---

### Post by headbuster on 2010-07-24
You can fix the boot loader with your windows cd. But this will override grub and will only boot windows.
You can also try to install windows and format the HD so that it's clean.
Tell me what you want to do :)

---

### Post by uRock on 2010-07-24
Can you fully boot the LiveCD? 

What are your system specs?

When you say, "I opened the comp after a long time," do you mean it has been sitting unused for a while or do you mean you opened and tinkered with the internals?

If you are needing to get Windows booted, then you can fix the MBR(Master Boot Record) and it will boot Windows. This is provided that there is nothing wrong with the hard drive.
To do this follow the instructions listed in this quote; > **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc
We prefer to try and reinstall Ubuntu and get them both working again.

uRock

---

### Post by Ajay Ramaseshan on 2010-07-24
Regarding the query posted by uRock,
I have not used the comp for about 2 months.
The live CD works fine. But while installing
in the Prepare Partition step no partitions get listed.
Nothing is displayed.
What do you think could be the problem?
Do you think I need to repair the MBR first?

---

### Post by uRock on 2010-07-24
I am not sure what may be causing this, but it sounds possible that the hard drive has been corrupted. I would try fixing the MBR so that you can get to Windows and back up your data before going any further.

---

### Post by headbuster on 2010-07-24
Try this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Ajay Ramaseshan on 2010-07-24
Hey uRock I had a query.
tried to install Lilo through Synaptic Package Manager but got this error
E: man-db: subprocess installed post-installation script returned error exit status 1
E: lilo: subprocess installed post-installation script returned error exit status 1

Is it fine?

---

### Post by Ajay Ramaseshan on 2010-07-24
@headbuster :
 I tried to restore the Grub by first finding the name of my disk drives.
I used a Ubuntu 10.04 Live USB.This was a 1GB USB.
When i typed the command
sudo fsidk -l
to my shock there was only 1 entry
Disk /dev/sda: 1006 MB, 1006632960 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         946      983024    6  FAT16

which means that this device is the USB drive from which im running Ubuntu.
None of my other partitions NTFS or earlier Ubuntu installations are showing up.
Any idea what could be done?
Any idea what has to be done?

---

### Post by gordintoronto on 2010-07-24
It looks like a cable has come off your hard drive.

---

### Post by uRock on 2010-07-25
To me it looks like something went wrong during partitioning and killed the partition table. Only way I know to fix is reinstalling everything and creating backups of data before doing installs in the future.

---

### Post by Ajay Ramaseshan on 2010-08-07
@uRock : I tested the BIOS and tried to see if my hard drive is detectable,
The BIOS shows up "No IDE Device" so which raised my douts of a physical crash.
Then I did another thing. Connected the hard disk to a SATA - USB interconnector
and connected to another computer running it as an external hard disk. The hard disk 
serial No deos not show up and the storage media is inaccesible .NO Files show up.
So looks like a clear case of physical failure. What is your opinion??

---

### Post by krishnandu.sarkar on 2010-08-07
Same as yours.. :(

---

