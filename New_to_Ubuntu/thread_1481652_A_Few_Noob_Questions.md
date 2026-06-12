---
title: "A Few Noob Questions"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by PipeBoss on 2010-05-12
Hi,

Not sure where to post this....

I've just finished downloading the 10.04 ISO and will burn it tonight or tomorrow morning.  This is my first ever attempt at Linux.  The computer I will put this on is an Abit IC7-G motherboard, 3.2 GHz Intel cpu, an 80 Gig C: drive, a 150 Gig D: drive, and (only) 512 Gig RAM.  I'm ordering some more memory shortly.

1.  Should I wait until my new memory arrives before installing Ubuntu?  Or can I install it now, and just plug in the new memory when it arrives?

2.  The 150 Gig drive is a storage drive, formatted NTFS (Windows XP Home) and does not actually have an OS on it - just file storage (mostly music and videos).  Can I just unplug the drive, install Ubuntu on the 80 Gig drive, then plug the Storage Drive back in?  Will it be recognized?  Do I need to backup the files somewhere, then reformat that drive and reload the files onto it?  

3.  Video card driver - when does it get loaded up?  It's been so long since I've started with a fresh install (of Windows XP on this machine), I've kind of forgotten the order of things....does the Ubuntu ISO prompt me for things as it goes along?

TIA for the help!

---

### Post by Ozymandias_117 on 2010-05-12
> **PipeBoss said:**
> Hi,

Not sure where to post this....

I've just finished downloading the 10.04 ISO and will burn it tonight or tomorrow morning.  This is my first ever attempt at Linux.  The computer I will put this on is an Abit IC7-G motherboard, 3.2 GHz Intel cpu, an 80 Gig C: drive, a 150 Gig D: drive, and (only) 512 Gig RAM.  I'm ordering some more memory shortly.

1.  Should I wait until my new memory arrives before installing Ubuntu?  Or can I install it now, and just plug in the new memory when it arrives?

2.  The 150 Gig drive is a storage drive, formatted NTFS (Windows XP Home) and does not actually have an OS on it - just file storage (mostly music and videos).  Can I just unplug the drive, install Ubuntu on the 80 Gig drive, then plug the Storage Drive back in?  Will it be recognized?  Do I need to backup the files somewhere, then reformat that drive and reload the files onto it?  

3.  Video card driver - when does it get loaded up?  It's been so long since I've started with a fresh install (of Windows XP on this machine), I've kind of forgotten the order of things....does the Ubuntu ISO prompt me for things as it goes along?

TIA for the help!



1. As long as it doesn't run too slowly for you, you can just install it now and upgrade your RAM later.

2. Yes it's fine to unplug the one, load the OS on the other, then plug it back in. Just make sure the 80 Gig is the master and the other is the slave (If it's IDE that generally means changing jumpers on the HDDs, if it's Sata, usually you have to change the location of the cables)

3. After you install the OS you will add the Graphics Driver.

---

### Post by earthpigg on 2010-05-12
> 1.  Should I wait until my new memory arrives before installing Ubuntu?  Or can I install it now, and just plug in the new memory when it arrives?

install now, no reason not to.


> 2.  The 150 Gig drive is a storage drive, formatted NTFS (Windows XP Home) and does not actually have an OS on it - just file storage (mostly music and videos).  Can I just unplug the drive, install Ubuntu on the 80 Gig drive, then plug the Storage Drive back in?  Will it be recognized?  Do I need to backup the files somewhere, then reformat that drive and reload the files onto it?  

leave both hard drives in, but click 'custom' and 'advanced' every time you see that option. take your time, go slow, and pay attention. if unsure about what you are looking at, don't be afraid to hit 'back' and review what's going on to make sure or open firefox and find more information on the internet before hitting 'next' again. (if you click 'try ubuntu 10.04 without making any changes', you will be able to have both the installer and firefox going at the same time.)

> 3.  Video card driver - when does it get loaded up?  It's been so long since I've started with a fresh install (of Windows XP on this machine), I've kind of forgotten the order of things....does the Ubuntu ISO prompt me for things as it goes along?

it won't ask you for a video card driver, or any other hardware details. it detects all of this. the only questions the install process asks you about are personal preferences ("which hard drive should ubuntu use? what do you want to name this computer?" etc). do you know the exact model/make of your video card? check here: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Sealbhach on 2010-05-12
Hi, here's a guide to installing Ubuntu which will give you an idea of what to expect.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

When you boot up from the Ubuntu CD or USB, you will be in a Live desktop session of Ubuntu, this will give you more of an idea of how well your hardware is detected.

Once you have tried out the Live session and decided to install Ubuntu (hopefully), then the system will recognise your graphics card and you can install the driver from the Hardware Drivers dialog box. That's assuming your graphics card is supported.


.

---

### Post by skibum3027 on 2010-05-12
1. No you meet the system requirements now. Just put your memory in when it gets there.

2. You don't need to unplug it at all. Just watch and make sure you don't apply any changes to it during partitioning.

3. Hardware drivers are added after the installation. In GNOME, the Hardware Drivers utility is under System->Administration->Hardware Drivers. In KDE it's just System->Hardware Drivers.

---

### Post by kevinatkins on 2010-05-12
Hi,

Just my tuppence worth..

Both replies to your questions are fine. In respect of your second 150G storage drive, I'd be inclined to unplug that during the install if you're new to this.

Then, assuming you wish to completely replace your existing OS on the 80G drive, you can go ahead and install Ubuntu, but when it comes to 'Prepare disk space', just select 'Erase and use the entire disk' - see the following link for more information -

[http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html](http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html)

When Ubuntu is installed, power down the machine and reconnect your 150G drive. When you reboot, the 150G drive will be available under the 'Places' menu. If you click the name of your 150G drive, you will be asked for your password, after which you can access all the files just as if you were using Windows. If you'd prefer to have the files available natively, without entering passwords etc, you'll need to arrange for the 150G drive to be 'mounted' when the system boots. This is easy to do, but I'd suggest you get Ubuntu installed first, then Google or ask questions here if you get stuck.

Hope you enjoy your new adventures with Linux - it's different to Windows, but once you get comfortable with it, you won't look back!

---

### Post by PipeBoss on 2010-05-12
All right!  Eased my fears...LOL.  Thanks for all the fast replies everyone!  Guess what I'm doing tomorrow! \\:D/

---

### Post by KdotJ on 2010-05-12
Good luck with it all! And remember the forums is a great place for help when you need it! Because you will, but it will all be worth it

---

### Post by wilee-nilee on 2010-05-12
> **PipeBoss said:**
> All right!  Eased my fears...LOL.  Thanks for all the fast replies everyone!  Guess what I'm doing tomorrow! \\:D/

The only things not asked here are what version of windows do you have right now? and do you want to keep it?

So if you want the dual boot set up, defrag with the free auslogics optimizer, set the preferences to move everything to the beginning of the disc. Then use gparted  to resize the partition, leaving a open space for Ubuntu. 

Then restart XP making sure it is working, then install Ubuntu into the free space and make sure on the last screen of the install to hit the advanced, and install grub to the mbr=sda not a partition which would be sda1 or any other. sda should be the hard drive your dealing with if you only have one plugged in when installing, but make sure this is the case by looking at the hard drive from gparted.

---

### Post by sXeChris on 2010-05-12
There are no consequences in updating the memory while already having Ubuntu installed. Just install it now.

---

### Post by earthpigg on 2010-05-13
> **PipeBoss said:**
> All right!  Eased my fears...LOL.  Thanks for all the fast replies everyone!  Guess what I'm doing tomorrow! \\:D/

i just want to re-emphasize how vital it is to read every screen before clicking 'next' if you choose to leave the storage hard drive inside the computer. there are no hidden messages or anything, but the assumption ubuntu makes is that you are doing that reading.

:D

---

### Post by Paqman on 2010-05-13
Back up your data before you start. It's unlikely anything will go wrong, but better safe than sorry!

---

### Post by PipeBoss on 2010-05-13
> **earthpigg said:**
> i just want to re-emphasize how vital it is to read every screen before clicking 'next' if you choose to leave the storage hard drive inside the computer. there are no hidden messages or anything, but the assumption ubuntu makes is that you are doing that reading.

:D
Thanks.  Yeah, in situations like this I'll read things several times - if you couldn't tell, I'm a bit paranoid about screwing things up.

I'm not installing it on my main computer.  The one it's going on is running XP, but it's not necessary I keep it so I'm just going to wipe that drive when I install Ubuntu (after I back up the files I need to keep).

---

### Post by Randypan on 2010-05-13
...Just one remark about the 150 GB Drive: Why stick to NTFS?
If you are planning on using that drive solely with Ubuntu, you can reformat it to a Linux compatible Filesystem like ext3 or ext4. That way you will have write support by default and avoid defrag issues. Copy all your files over to another disk and reformat the drive, using GParted from the live-CD or by downloading and installing it via Synaptic.
You can do that after you are done with the installation.

---

### Post by CharlesA on 2010-05-13
> **Paqman said:**
> Back up your data before you start. It's unlikely anything will go wrong, but better safe than sorry!

+1 to backups. Definitely.

> **Randypan said:**
> ...Just one remark about the 150 GB Drive: Why stick to NTFS?
If you are planning on using that drive solely with Ubuntu, you can reformat it to a Linux compatible Filesystem like ext3 or ext4. That way you will have write support by default and avoid defrag issues. Copy all your files over to another disk and reformat the drive, using GParted from the live-CD or by downloading and installing it via Synaptic.
You can do that after you are done with the installation.

Inter-OS compatibility? Other then that, if you format to a different file system, it'll be a destructive conversion. Always backup before doing anything with partitions.

---

### Post by 3rdalbum on 2010-05-13
Don't unplug the other drive - if you do, then you might have a situation where the GRUB bootloader is pointing to the wrong disk. You might be installing Ubuntu on the "1st" hard disk, but then when you plug in the other hard disk again, Ubuntu is on the "2nd" hard disk and GRUB will still be pointing to what is numerically the first hard disk.

---

### Post by PipeBoss on 2010-05-13
> **Randypan said:**
> ...Just one remark about the 150 GB Drive: Why stick to NTFS?
If you are planning on using that drive solely with Ubuntu, you can reformat it to a Linux compatible Filesystem like ext3 or ext4. That way you will have write support by default and avoid defrag issues. Copy all your files over to another disk and reformat the drive, using GParted from the live-CD or by downloading and installing it via Synaptic.
You can do that after you are done with the installation.

No, I was hoping to be able to access the drive both through the Ubuntu computer and my Vista computer.

Which brings up another set of issues, I guess.  Right now both my XP and Vista computers are networked - mainly just so the Vista computer can access the 150G storage drive.  Maybe what I should do for now is just swap that drive over into my Vista box for now....

---

### Post by nothingspecial on 2010-05-13
Ubuntu can read and write to ntfs so don`t worry about it.

---

### Post by PipeBoss on 2010-05-13
> **kevinatkins said:**
> Hi,

Just my tuppence worth..

Both replies to your questions are fine. In respect of your second 150G storage drive, I'd be inclined to unplug that during the install if you're new to this.

Then, assuming you wish to completely replace your existing OS on the 80G drive, you can go ahead and install Ubuntu, but when it comes to 'Prepare disk space', just select 'Erase and use the entire disk' - see the following link for more information -

[http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html](http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html)

When Ubuntu is installed, power down the machine and reconnect your 150G drive. When you reboot, the 150G drive will be available under the 'Places' menu. If you click the name of your 150G drive, you will be asked for your password, after which you can access all the files just as if you were using Windows. If you'd prefer to have the files available natively, without entering passwords etc, you'll need to arrange for the 150G drive to be 'mounted' when the system boots. This is easy to do, but I'd suggest you get Ubuntu installed first, then Google or ask questions here if you get stuck.

Hope you enjoy your new adventures with Linux - it's different to Windows, but once you get comfortable with it, you won't look back!
Stuck.  I shut my computer down, unplugged the 150G drive (IDE), installed Ubuntu, messed around with it a bit (using it right now as I type this, actually..LOL), shut the system back down, plugged in the 150G drive, looked in the "Places" menu......nothing.  Looked in Places>Computer....nothing....hmm....

I'm heading out, I'll shut it all down and will try again when I return....

Thanks again, everyone!  I've got Ubuntu up and (mostly) running!

---

### Post by Ozymandias_117 on 2010-05-13
Can you post the results of

```
sudo fdisk -l
```

and 

```
sudo lshw | grep disk
```

Note: Just remember that commands, file names, etc. are case sensitive in Linux.

---

### Post by PipeBoss on 2010-05-13
I'll get that for you in a second, Ozy....I had just come back in to say that the drive shows in BIOS, and also in System>Administration>Disk Utility....but I can't seem to access it...

Let me go run those commands, I'll put them up shortly...

---

### Post by PipeBoss on 2010-05-13
> **Ozymandias_117 said:**
> Can you post the results of

```
sudo fdisk -l
```
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

> **Ozymandias_117 said:**
> and 

```
sudo lshw | grep disk
```
*-disk
*-disk

---

### Post by -humanaut- on 2010-05-13
I might be a minority here but I think you should wait till you get the RAM it will be a much better experience just my two cents though.

---

### Post by PipeBoss on 2010-05-13
Thanks -humanaut-.   Too late, though...


Maybe this will help?

[ATTACH]156845[/ATTACH]

---

### Post by Ozymandias_117 on 2010-05-13
That was a lower case L in the first command :P

Question, do you want the drive automatically mounted every time you boot? Not sure why it's not showing up in places, but we can get it mounted :)

---

### Post by PipeBoss on 2010-05-14
> **Ozymandias_117 said:**
> That was a lower case L in the first command :P

Question, do you want the drive automatically mounted every time you boot? Not sure why it's not showing up in places, but we can get it mounted :)
I don't know what happened, because I copy/pasted the command from your post....weird.  Here's the corrected info:

> Disk /dev/sda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13e3edf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21175   160082968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c11d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9544    76658688   83  Linux
/dev/sdb2            9544        9730     1489921    5  Extended
/dev/sdb5            9544        9730     1489920   82  Linux swap / Solaris


Yes, I'd like the drive to be accessible every time I boot.  Thanks for walking me through this, Ozymandias.

---

### Post by kevinatkins on 2010-05-14
Hi,

Based on the information you've given so far, to have the drive mounted when you boot the machine, you'll need to -

1. Create a directory in which the drive is mounted. You could put this inside the /media directory. You'll need administrative privileges to do this. For example, to create a 'windows' subdirectory inside media, execute the following at a command prompt -

```
sudo mkdir /media/windows
```

The word 'sudo' elevates your privileges to administrator and mkdir is the command to create a directory. You'll need to supply your normal login password.

2. You then need to tell the system to mount the drive upon boot. This is done by adding the drive to a file which contains information about the various filesystems and drives on your computer. The file is called 'fstab' and it's located in the /etc directory. To edit this file, you will again need administrative privileges, and be very careful - it's a critical system file. So first, it would be a good idea to make a backup copy -

```
sudo cp /etc/fstab /etc/fstab.bkp
```

Then to edit, execute the following command at the terminal -

```
sudo gedit /etc/fstab
```

You'll again be asked for your password. The file will appear in an editor. At this point, please could you copy / paste the contents of the file to the forum so that we can check to see all is in order. Assuming all OK, proceed as follows..

Copy / paste the following line at the bottom of the file -

```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

Then save the file and close the editor. To reload the fstab configuration, execute the following command at the terminal -

```
sudo mount -a
```

This should now mount your windows drive - browse to /media/windows and check that everything looks OK.

---

### Post by PipeBoss on 2010-05-14
> **kevinatkins said:**
> Hi,

Based on the information you've given so far, to have the drive mounted when you boot the machine, you'll need to -

1. Create a directory in which the drive is mounted. You could put this inside the /media directory. You'll need administrative privileges to do this. For example, to create a 'windows' subdirectory inside media, execute the following at a command prompt -

```
sudo mkdir /media/windows
```The word 'sudo' elevates your privileges to administrator and mkdir is the command to create a directory. You'll need to supply your normal login password.

2. You then need to tell the system to mount the drive upon boot. This is done by adding the drive to a file which contains information about the various filesystems and drives on your computer. The file is called 'fstab' and it's located in the /etc directory. To edit this file, you will again need administrative privileges, and be very careful - it's a critical system file. So first, it would be a good idea to make a backup copy -

```
sudo cp /etc/fstab /etc/fstab.bkp
```Then to edit, execute the following command at the terminal -

```
sudo gedit /etc/fstab
```You'll again be asked for your password. The file will appear in an editor. At this point, please could you copy / paste the contents of the file to the forum so that we can check to see all is in order. ...
Here is what I got:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5c05764b-7d60-4c3b-8e7f-b50864751b3f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by kevinatkins on 2010-05-14
Hi,

OK, there's something strange going on here..

The two drives are identified as /dev/sda and /dev/sdb. Normally, your system would reside on the first drive (/dev/sda) and that's how it appears in your /etc/fstab.. However, the output of fdisk that you post appears to show your larger (NTFS windows) drive on /dev/sda and your Ubuntu installation on /dev/sdb.. Your screenshot from the disk utility backs this up, too.

You appear to be running parallel ATA drives, so what I'm thinking has happened is that when you've reconnected the second drive, the machine has swapped the drive ids (the jumpers on the drives are probably set to 'cable select')... 

This little problem is probably part of the reason why the drive isn't showing up in 'Places'...

We'll just need to do a little detective work. Could you power down the machine, and check the jumper settings on both hard drives. If they are both set to 'CS' or 'Cable select', please swap the position of the drives on the cable and reboot. Then post the output of fdisk as above, and also the contents of /etc/fstab.

If the jumpers are not set to CS, please set them to CS and reposition the drives so that the first, 80G (Ubuntu) drive is on the end of the cable, with the second drive fitted to the header in the middle of the cable. Then boot the machine as per above.

---

### Post by PipeBoss on 2010-05-14
Hmm...

The OS drive is  a SATA drive.
The Storage drive is is a PATA drive, plugged into the MB using the Master cable end instead of the Slave cable end.  
This is how it was set up when I had XP on the SATA drive; it didn't occur to me that this setup would be an issue.  Could it be as simple as just unplugging the Master cable end and using the Slave cable end?

---

### Post by kevinatkins on 2010-05-14
Oh heck.. PATA drives generally take precedence over SATA drives as far as I'm aware, so your storage drive will always end up as /dev/sda irrespective of whether you change its settings or position on the cable..

OK, to get around this, I think you're first going to need to correct your /etc/fstab file so that it correctly identifies your system drive as /dev/sdb1 (make a backup first, in slightly uncharted territory here - if it goes wrong, we'll need to restore the original fstab file using the Live CD)

So you need to open /etc/fstab for editing, and change -

```
/dev/sda1 / ext4 errors=remount-ro 0 1
```

to -

```
/dev/sdb1 / ext4 errors=remount-ro 0 1
```

Then reboot. If all goes OK, you can then edit /etc/fstab and add your second drive to the bottom of the file -

```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

.. as previously explained.

If things go wrong, post back. Sorry for all the trouble!

---

### Post by PipeBoss on 2010-05-14
Worked like a charm!  Great job!  I can't thank you enough!

---

### Post by kevinatkins on 2010-05-14
Brilliant - glad it's all sorted.

---

