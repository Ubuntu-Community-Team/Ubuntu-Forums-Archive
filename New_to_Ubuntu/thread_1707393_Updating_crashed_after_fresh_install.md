---
title: "Updating crashed after fresh install"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by resander on 2011-03-15
I have just installed Ubuntu 10.10 on a Fujitsu laptop.
Have restarted and clicked the Update Manager item
on the Admin menu. There were 289 updates available and
I started the update process, but after a few seconds
a dialog with the following popped up:

'Task cannot be monitored or controlled.
The connection to the daemon was lost.
The background daemon probably crashed.
It seems that the daemon died.'


I also tried the following from the command line:

sudo apt-get update
sudo apt-get upgrade

sudo apt-get update showed a list of available updates.

sudo apt-get upgrade produced:
Reading package lists ... Done
Segmentation tree faulty 50%

What might be the cause?

Ken
P.S.
I used the same installation CD and installed successfully on 
a desktop PC a couple of weeks ago.

I selected 'use entire disk' (100GB) for Ubuntu when installing 
for the laptop. Installation stopped during the 'Copying files'
stage (about 30% complete) with error 'could not write to hard disk'.
So I used gparted from the live CD and made a 20GB placeholder NTSF
partition at the start. I flagged it with boot & hidden. I then 
reinstalled Ubuntu choosing 'install along side of other'. All files
were copied this time, so I thought the placeholder partition was
covering the faulty parts of the disk. I did not install anything
in the NTSF partition. Ubuntu starts normally and there is no GRUB 
menu to choose from. It works, except for the updating using 
Update Manager, Synaptic Manager and Ubuntu Software Center.

Would be grateful for advice.

---

### Post by fabricator4 on 2011-03-15
> **resander said:**
> 
Segmentation tree faulty 50%

What might be the cause?


I suspect that the hard drive is failing progressively.  Check the SMART data for the drive in Disk Utility.

Chris

---

### Post by resander on 2011-03-15
Thanks Chris,

I think you are right about the disk....

I thought not having Windows XP in the NTSF partition
might in some way cause this problem, so I successfully 
installed Windows, deleted the Ubuntu partitions and
started reinstalling. This time it failed copying 
an xxxx.DB file (it worked before), but I pressed 
Ignore button hoping it would not matter.
Then during the final stages installer produced the message
'The bootloader cannot be placed as intended'.

So, need to get a replacement disk.

Ken

---

