---
title: "Harddisk problem"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by dtommy79 on 2010-05-23
Hi,

I've just installed ubuntu, and after installation it displays a warning that there are problems with my harddisks.

I've got two hard disk in my pc.

For the first it says:

> Disk has many bad sectors.

Reallocated sector count.
Count of remapped sectors. When the hard drive finds read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area).

For the second it says:

> Disk failure is imminent.

Uncorrectable sector count.
The total number of uncorrectable errors when reading/writing a sector. A rise in the value of this attribute indicates defects of the disk surface and/or problems in the mechanical subsystem.

Any help is appreciated.

---

### Post by wojox on 2010-05-23
Is this from Disk Utility (Pamiliset)?

I get those errors as well. Haven't had any problems yet.

---

### Post by dtommy79 on 2010-05-24
Palimpsest disk utility, yes

I'm also getting this error message when trying to open it:

[IMG]http://i45.tinypic.com/so50gn.jpg[/IMG]

---

### Post by dtommy79 on 2010-05-24
I think I ran into this bug:

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Can an upgrade solve the problem?

---

### Post by bumanie on 2010-05-24
That message is consistent with telling you that windows has not been shutdown correctly (ie, it's had a hard shutdown or is a usb that has been pulled out, rather than removed safely). To fix - boot in to windows and shutdown the OS or device correctly and then everything should work fine.

---

### Post by dtommy79 on 2010-05-24
> **bumanie said:**
> That message is consistent with telling you that windows has not been shutdown correctly (ie, it's had a hard shutdown or is a usb that has been pulled out, rather than removed safely). To fix - boot in to windows and shutdown the OS or device correctly and then everything should work fine.
But how can I do that?

Didn't ubuntu remove the windows when it was installed?

---

### Post by mikewhatever on 2010-05-24
> **dtommy79 said:**
> But how can I do that?

Didn't ubuntu remove the windows when it was installed?

Well, it doesn't have to, not unless you overwrote the Windows partition. Anyway, the existence of an ntfs partition probably suggests this isn't the case. What exactly are you trying to open.

---

### Post by dtommy79 on 2010-05-24
> **mikewhatever said:**
> Well, it doesn't have to, not unless you overwrote the Windows partition. Anyway, the existence of an ntfs partition probably suggests this isn't the case. What exactly are you trying to open.
In the  'Places' option I have

Computer
Floppy Drive
120 GB Filesystem

I get the error when i'm trying to open the "120 GB Filesystem" (my other hard drive)

---

### Post by bumanie on 2010-05-24
If you don't have ntfs partitions left on some device, you should not be getting that message. Please connect all devices and post terminal output of > sudo fdisk -l this can be done from within an installed ubuntu or from a live cd. *NB: That is a lower case L, not the digit one.

---

### Post by dtommy79 on 2010-05-24
> **bumanie said:**
> If you don't have ntfs partitions left on some device, you should not be getting that message. Please connect all devices and post terminal output of this can be done from within an installed ubuntu or from a live cd. *NB: That is a lower case L, not the digit one.
Thanks.

This is the result:

[IMG]http://i47.tinypic.com/33y2hco.gif[/IMG]

---

### Post by warfacegod on 2010-05-24
Looks like these guys have you on track for the mounting problem.

As far as the notifications in your first post, I suggest:

```
sudo apt-get install gsmartcontrol
```

This will install gsmartcontrol a much better HDD tool than Disk Utility (Palimpset). Palimpset is known for throwing false positives. If *gsmart* also tells you there are errors, you have a problem. If not then don't worry about it and go to:

System> Prefs.> Startup Applications> and disable Disk Notifications. No more Error messages when you boot.

---

### Post by dtommy79 on 2010-05-24
But even if I disable Disk Notifications I won't be able to open the other drive.

---

### Post by warfacegod on 2010-05-24
> **dtommy79 said:**
> But even if I disable Disk Notifications I won't be able to open the other drive.

My post wasn't about opening the drive. Just about the potential failures you referred to in your first post. As the guys said before, you'll need to plug the drive into a Windows machine and "Safely Remove Hardware", if its an external. The icon will be located in the System Tray, bottom right corner of the screen. If its an internal drive, you'll need to pull it out and put it inside a Windows computer, being sure to put the drives jumper to Slave if its IDE (old school ribbon cable) and setting it back when your done. I don't know if SATA drives even have jumpers or not. With the drive in Windows, turn the computer on, let Windows load, and then turn it off.

There *are* ways to get around plugging it into Windows but they aren't safe for your data files on the drive.

---

### Post by jerome1232 on 2010-05-24
In the future instead of posting  a screenshot of the output of commands copy and paste it. wrap it in code tags (looks like a number symbol if your have advanced mode on) 

ctrl+shift+c to copy text out of a terminal.

When you first boot the computer hold shift down, and see if a grub menu comes up that allows you to boot into Windows, try booting into that. If you can then schedule it to run chkdsk on itself on the next boot, and reboot into windows again. Chkdsk is the prefered method of repairing a ntfs partition. **If this is an external make sure you safely remove it before disconnecting it**.

If you cannot boot into windows or have no windows computer at your disposal try using ntfsfix on the partition. Do so at your own risk, although I will say I've never had it harm an ntfs partition, I've also only used it twice.

```
sudo ntfsfix /dev/sdb1
```

---

### Post by warfacegod on 2010-05-24
> **jerome1232 said:**
> In the future instead of posting  a screenshot of the output of commands copy and paste it. wrap it in code tags (looks like a number symbol if your have advanced mode on) 

ctrl+shift+c to copy text out of a terminal.

When you first boot the computer hold shift down, and see if a grub menu comes up that allows you to boot into Windows, try booting into that. If you can then schedule it to run chkdsk on itself on the next boot, and reboot into windows again. Chkdsk is the prefered method of repairing a ntfs partition. **If this is an external make sure you safely remove it before disconnecting it**.

If you cannot boot into windows or have no windows computer at your disposal try using ntfsfix on the partition. Do so at your own risk, although I will say I've never had it harm an ntfs partition, I've also only used it twice.

```
sudo ntfsfix /dev/sdb1
```

Pretty sure you need "ntfsprogs" and I can't remember if that comes installed by default.

---

### Post by jerome1232 on 2010-05-24
> **warfacegod said:**
> Pretty sure you need "ntfsprogs" and I can't remember if that comes installed by default.

Good point, I didn't think about that. I'm pretty sure it only installs file system specific tools if you had a partition with the respective file-system present during the installation.

So along with what warfacegod said, if you have to resort to ntfsfix and you get an error about no such command. Use apt-get/aptitude/synaptic to install ntfsprogs and reattempt the ntfsfix command.

---

### Post by exodus_ on 2010-05-24
> **jerome1232 said:**
> Good point, I didn't think about that. I'm pretty sure it only installs file system specific tools if you had a partition with the respective file-system present during the installation.


I am unsure of other versions, but I only have Ubuntu installed (currently 10.04) and it has the ntfsfix program installed by default, and I don't use NTFS on any of my filesystems ;)

Also to the OP:

Are you using windows on this machine still?  From some earlier posts it might look like no, but I don't want to assume.  If you are indeed not using windows, you might consider backing up any data from the NTFS filesystem and re-creating it as something more native to Linux such as ext3/4 or any of the other well supported ones.  It'll make it easier to troubleshoot in the future.

---

### Post by mikewhatever on 2010-05-24
What's ntfsfix?

```
aptitude show ntfsfix
E: Unable to locate package ntfsfix

```

---

### Post by jerome1232 on 2010-05-24
ntfsfix is a program included with the package ntfsprogs.

See man ntfsfix for details.

---

### Post by dtommy79 on 2010-05-24
Hi,

Thanks for all the answers.

I ran the 

```
sudo ntfsfix /dev/sdb1
```

command. This is the result:

```
tommy@tommy-desktop:~$ sudo ntfsfix /dev/sdb1
Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.
```

---

### Post by jerome1232 on 2010-05-24
I think your drive has or is dieing hard, warfacegod was recommending you check another smart monitor tool. Did you have important stuff on this drive?

The best way I know of to attempt recovering files would be to image the drive then hit the image with photorec or foremost to try and recover some files out of it. 

But don't get into that until we confirm that the drive is dying, it may be possible that chkdsk could recover it still (didn't I say to try chkdsk first?)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by dtommy79 on 2010-05-24
Yes i tried the chkdsk before it, but there is no windows on my pc. There was a pop up window coming up when I hit the shift, but the only choice was linux. So I guess when i installed ubuntu it removed windows as well. 

Well, it would be cool not to lose the data, but I'll survive if it happens otherwise.
The important thing is that I could use both hard drives.

---

### Post by warfacegod on 2010-05-24
Give gsmart a try. See post #11. See if the drive is indeed failing as we suspect. If it reports a few bad sectors, say around 50, you should be okay for a while but get the drive to a Windows machine so you can shut the driver down properly and then make a backup of the data on it. If you get much more than 100 bad sectors, its likely that failure is eminent so get your data as quickly as possible.

Just for a goof, open a Terminal and do:

```
sudo update-grub
```

And then reboot. When it starts back up, hold Shift to see if Windows is there.

I'm not entirely convinced that Windows isn't on your system but then, I'm not entirely convinced it is either.

---

### Post by dtommy79 on 2010-05-24
> **warfacegod said:**
> Give gsmart a try. See post #11. See if the drive is indeed failing as we suspect. If it reports a few bad sectors, say around 50, you should be okay for a while but get the drive to a Windows machine so you can shut the driver down properly and then make a backup of the data on it. If you get much more than 100 bad sectors, its likely that failure is eminent so get your data as quickly as possible.

Just for a goof, open a Terminal and do:

```
sudo update-grub
```

And then reboot. When it starts back up, hold Shift to see if Windows is there.

I'm not entirely convinced that Windows isn't on your system but then, I'm not entirely convinced it is either.


Result for sudo update-grub

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I'll try gsmart

---

### Post by exodus_ on 2010-05-24
EDIT: Nevermind, I justg saw your post, and update-grub definitely does not seem to be finding windows.

However, did you make any changes to the drives before installing Ubuntu? Are they IDE or SATA drives?  Did you make one a master when before it was a slave?  Did you make sure the cables are connected securely?

Also have you tried to boot from a live CD of some sort to see if you have any success/failure accessing the drive to rule out an issue with your installation?

---

### Post by dtommy79 on 2010-05-24
OK, is there an "easy" way to fix this, even if i lose all the data? at this point I don't care anymore.

EDIT:

I didn' make any changes. They are IDE. Cables are ok. 

> Did you make one a master when before it was a slave?

I'm not sure about this, they are quite old now.

---

### Post by jerome1232 on 2010-05-24
What we are saying is SMART (Self-Monitoring, Analysis, and Reporting Technology) is showing bad sectors, if those continue to rise your drive is going to die. The only fix is to buy a new drive and salvage your data before the drive actually fails.

warfacedgod is recommending that you check a second more reliable SMART tool

exodus_ is recommending you check your cables, it's entirely possible a connector wiggled loose or something.

I hope I summed that up in a way that is understandable and accurate.

---

### Post by dtommy79 on 2010-05-24
OK, i've installed gsmart, but I cannot open it.

> **Could not launch 'GSmartControl'**

Failed to execute child process "su-to-root" (No such file or directory)

---

### Post by warfacegod on 2010-05-24
> **dtommy79 said:**
> OK, i've installed gsmart, but I cannot open it.

I had that same problem about 10 minutes ago. right click your menu and select "Edit Menus". Find gsmartcontrol in System Tools> right click it> select "Revert To Original".

If that doesn't work then: hit Al+F2 and type gksudo gsmartcontrol

---

### Post by dtommy79 on 2010-05-24
Thanks the second one worked.

Gsmart says for the first drive that

Basic helath check: passed

The second failed. do you need any specific info from gsmart?

---

### Post by warfacegod on 2010-05-24
> **dtommy79 said:**
> Thanks the second one worked.

Gsmart says for the first drive that

Basic helath check: passed

The second failed. do you need any specific info from gsmart?

Nope. And you know what you need to know now too. Your drive is going to die. Do the Windows thing like we've said, get your stuff off the drive, buy a new one. If you're not going to use Windows, I suggest you format the new drive as ext4.

---

### Post by dtommy79 on 2010-05-24
OK, thanks

---

### Post by exodus_ on 2010-05-24
I am sorry to hear your disk is most likely going to die or already has..

If you are satisfied with the outcome here, you should mark this as [SOLVED] so that others can benefit from it, too :)

---

