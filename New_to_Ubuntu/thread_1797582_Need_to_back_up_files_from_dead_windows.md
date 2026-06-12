---
title: "Need to back up files from dead windows"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Psoleos on 2011-07-05
My girlfriends laptop completely froze up while she was using it, she turned it on and now when she trys to turn it back on after a while of vista 'scrolling' she gets a black screen and nothing else. I have tried to boot off multiple vista recovery CDs to try and sort out the problem but these do exactly the same.

As she needs files on it for college, I decided I would boot up ubuntu on a usb and try to retreive the files this way and worry about the OS not working later. However, after going through multiple forums and reading what other people have written, I cannot mount the windos drive to take files off it.

When I try to do this specific tutorial:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

I get the following error:

> root@ubuntu:~# mount -t ntfs-3g /dev/sda2 /media/disk -o force
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

It is telling me to run chkdsk on windows, however I cannot get on to windows to run this command...

Can anyone enlighten me on what I am doing wrong, I would greatly appreciate it?

Thank you very much.

Edit:

Something else I tried that didn't work:

> root@ubuntu:~# sudo ntfsfix /dev/sda2
Mounting volume... pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... Failed to empty $FILE_LogFile/$DATA: Input/output error.
FAILED
Failed to reset $LogFile: Input/output error.

Also, I do not know if this will help however this is the result when I do sudo fdisk -l

> root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ef63dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       30402   233956352    7  HPFS/NTFS

Disk /dev/sdb: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         255     2047936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(253, 254, 63) logical=(254, 245, 55)


---

### Post by in-dust-rial on 2011-07-05
hey,


so it seems you might want to try two non-linux related issues.

first: use a external-monitor to exclude the possibility that only the screen goes down.

second: get a windows-cd and repair windows. if repairing doesnt work you can at least check disc from the recovery console (from windows CD).
how to do this might be different for the type of windows CD you are using. normally you just say: want to repair or drop me to recovery shell.


about the usage of the force flag (-f). 
try not to use the force flag until you are completely familiar with the consequences. 
especially when there is disc inconsistancy, you should try to find help before issuing a force flag.

alternative solutions:
a)
use a usb-HD plug (for external hard drives). those are available for laptop drives as well. they are cheap and you can access the harddrive from another windows with ease.
b)
use the DD command to backup whole disc.
as i see it it might also work with inconsistencies (but you should ask some pro or google it).


good luck.

---

### Post by Psoleos on 2011-07-05
I have tried to use a CD to repair and I get the same, just a black screen, I can't understand why this would be the case but it is. However I will go and try plugging it into the monitor now.

Just to confirm, I have tried windows CDs and they will not work either, it trys to load then the screen goes black. Also, just tried it with a monitor and same problem, black screen.

Any other ideas?

Thanks

---

### Post by in-dust-rial on 2011-07-05
okay,
if the live-windows doenst work I fear the live-linux repair wount work too.

(follow this only if the HDD doesnt make unexpected noises)
to be onn the save side, just get the HDD out of the laptop before it is damaged too.

dont be afraid, consult the manual!
normally HDs can be removed easily.

plug it into a external USB case 2.5'' or into another laptop (exchange HDs).

rescue data
and 
repair HD

I fear solving the inconsitancy is not possible from linux (at least i could  not do it in 2010)

GOOD LUCK

---

### Post by in-dust-rial on 2011-07-05
ANNNDD *sorry hurry*
try windows-7 CD...
MAYBE!

---

### Post by wildmanne39 on 2011-07-05
Hi, from the looks of the results you have gotten it looks like the disk is dead.

---

### Post by aeiah on 2011-07-05
> **wildmanne39 said:**
> Hi, from the looks of the results you have gotten it looks like the disk is dead.

not necessarily dead, but certainly not healthy.


id try and do these things:

try and take a copy of the whole drive, using dd, and continue poking around with the copy rather than the actual disk. 

use linux and windows tools to try and fix the filesystem. tools contained on Ultimate Boot CD (both linux and windows based versions), and the standard windows chkdsk which you'll find on a WinPE disc.

try running the copy through testdisk and photorec

look into sending it to a data recovery specialist (cheaper than it used to be)




oh, and teach her how to back up :p we take half-hourly snapshots for important work.

---

