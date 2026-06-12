---
title: "Way New to Servers"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by ramburn on 2010-01-15
I was given an old server w/ 3, looks like WD drives (300 GB), that are set up as a RAID.  Mirrored 

Originally was setup w/ redhat but came with no password credentials, so I decided to go with Ubuntu Server.

I created the ISO to a cd and installed over the redhat.

At this point I'm completely lost.

After installing It gets to 

grub>

I have read and tried several commands to get to Ubunto. 

Suggestions to edit files get me files not found.
Other suggestions have gotten me Cannot mount selected partition.  I have tried many combinations.  

I am new to servers so I don't if I'm missing something or a bad install.

Please help

---

### Post by lisati on 2010-01-15
It sounds like there's a "grub" problem (grub is the bootloader that Ubunutu uses.) Unless someone jumps in with a better idea, you might need to get hold of a "live CD" or do a fresh install.

If you're using v9.10 of Ubuntu Server edition, take a look here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
v9.04 and older: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ramburn on 2010-01-15
Thanks for jumping in.

I have looked at the Grub2 document but as simple as Hold down SHIFT to display the menu during boot, doesn't work.

Any other suggestions?

---

### Post by falconindy on 2010-01-15
Hardware or software RAID? Did you actually install Ubuntu? Where did you tell the installer to put GRUB?

---

### Post by minsf on 2010-01-15
at the grub> prompt, what do you get when you enter "ls" (no quotes)? what do you get when you enter "set"?

---

### Post by ramburn on 2010-01-18
Sorry for the delay in Response....

For the question of the hardware or software raid, I'm guessing software but I'm opening the box up today to look.

As for the commands and what the response was, all the same Unrecognized command. 

Where I had grub installed?  well... not sure but I think based on what little I'm looking at, this is what i saw

SCSI1 (0,0,0) 
dev/sda1

Thanks for the help.  If nothing else, I have decided to stop hiding from the server world and just join it.

---

### Post by ramburn on 2010-01-18
A couple of updates.

Looks I was wrong, it looks like a hardware raid.  There is a board is one of the  slots with 3 blue cables going to the drives and a gray one going to the motherboard.

I decided to look at the install again, and tried in rescue mode.  When I got to the 'Device to use as root file system', I received an error when using the default file /dev/sda1

An error occured while mounting the device you entered for your root file system (/dev/sda1)  on /target.

Please check the system logs for more information.

Not sure how to check system logs  but I do have a few more choices while I'm waiting for a response.

Thanks

---

### Post by tgalati4 on 2010-01-18
If it was a real server with real RAID hardware, then you would go into BIOS first and set up the drives in the configuration you want.  Then install Ubuntu server.

If you simply installed Ubuntu, then you probably wiped the partition tables and master boot record blocks on the disks.  That is where the BIOS/RAID keeps its configuration information.  If the BIOS can't see the disks then Ubuntu won't see them either.

---

### Post by ramburn on 2010-01-18
Ok that sounds like a good direction to go.  Any suggestions on setting up the drives in the configuration I want.

I'm not sure what I want.

In the settings utility  (RocketRAID 231xPM BIOS)  it shows Channel, Model Number, Capacity, Make and Status.  Status being 'Configured'

---

### Post by ramburn on 2010-01-18
Update

seems bios can see the disks just not me.

I did manage to get something new.  root (hd1,4)     returned filesystem type is ext2fs, partition type 0x83

Does this mean anything?

I have come to the conclusion that there is nothing wrong with the install, it's just my lack of knowledge.

---

### Post by ramburn on 2010-01-18
Ok with much reading I have found one link that seems to match my issue.

[http://ubuntuforums.org/archive/index.php/t-155864.html](http://ubuntuforums.org/archive/index.php/t-155864.html)

Look to the last thread.

The problem is that he didn't solve the problem really.  

If someone could look at these threads and help me get past this issue, I really want to keep the RAID.

---

### Post by pirateghost on 2010-01-18
> **ramburn said:**
> Ok that sounds like a good direction to go.  Any suggestions on setting up the drives in the configuration I want.

I'm not sure what I want.

In the settings utility  (RocketRAID 231xPM BIOS)  it shows Channel, Model Number, Capacity, Make and Status.  Status being 'Configured'
one of the downfalls of cheap raid cards (i have 2 rocketraid cards)  unfortunately, the drivers are not in the kernel by default and have to be added
[http://www.highpoint-tech.com/BIOS_Driver/rr2340/Linux/newformat/Install_Ubuntu_RR2340.pdf](http://www.highpoint-tech.com/BIOS_Driver/rr2340/Linux/newformat/Install_Ubuntu_RR2340.pdf)

that should be similar, although note the different model numbers and goto [http://www.highpoint-tech.com/](http://www.highpoint-tech.com/) and select support>bios+drivers

there are instructions on how to make it all work as well as drivers needed

---

### Post by ramburn on 2010-01-19
Thanks for all your help to get me this far.  

RocketRAID 2340 Ubuntu Linux Installation Guide says

Create a MS-DOS filesystem and extract the archive file to the (USB) floppy diskette 

or in Linux:

# mkdosfs /dev/fd0
# mkdir -p /mnt/floppy
# mount /dev/fd0 /mnt/floppy
# tar xzvf rr2340-ubutu-8.04.tgz -C /mnt/floppy
# umount /dev/fd0

My system is stuck on grub> 

Can you tell me how to create the archive file or get from grub> to use linux commands?

---

### Post by tgalati4 on 2010-01-20
You need to find a working linux system.  Create the RAID boot floppy on another machine (one that works).

Then boot your server with the boot floppy and it should see the rocketRAID card.

I wish there was an easier way.  When you have used linux for a while, you tend to collect old machines just for this reason.  (Newer machines don't have floppy drives).

As far as configuration, do some research on RAID and answer some questions:

How fast is your current drive?  (probably 66-80 MB/sec)
How fast could it be with striping across the drives? (2x or 3x the above speed depending on 2 or 3 drives)
Does striping reduce reliability?  Yes, so you can add another disk to act as a checksum.  That's a lot of disks spinning.  Drives are so cheap now, that electrical costs of running 24/7 need to be considered.  Your server with a full RAID setup will probably run $200/year in electrical costs.

Does mirroring improve reliability?  Yes, it can, but unless you are selling airline tickets 24/7 do you really need mirroring?

Having a good backup plan for personal data with an external drive (USB perhaps) and storing it away from the primary machine (in case of fire or deluge) is equally important to how you have RAID set up.

---

