---
title: "Having Problems Getting my External Hard Drive to work"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Zoey.Marie on 2009-07-25
(reposted here because I think it's probably where it's supposed to be)

Hi. 

I am a complete ubuntu newbie... but, I think I looked through threads already and I couldn't find anything that fixed my problem (though, I may not have had good search parameters or something). So, I'm posting it here in hopes that someone can help me troubleshoot it (since I don't even know where else to look to troubleshoot problems). I totally suck. :sad:

Anyways.
I have an external hard drive. The case says I/O Magic, but I'm pretty sure that isn't the brand of the hard drive. I followed someone's instructions on a different thread, about accessing the terminal and doing something or other (sorry I can't remember anything else)--and I seem to remember that it might've started with a L...

It worked fine when I had Windows (though, I haaaated Windows), but now it says this when I try to click the "Mount 'New Volume'" thing:

Unable to mount the volume 'New Volume'.
Details:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsisten, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reeboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

Also, it sometimes says (if I try and leave that message open):
DBus error org.freedesktop.DBus.Error.NoReply: Message did not recieve a reply (timeout by message bus)

Any help please?
I know that I should be able to figure this out in time, but I thought it might be best if I asked a group of smart people to help--since I have homework on it that is due tomorrow. :sad:

Thank you SO freaking much for any help/tips/advice/links/etc... that you can give. I wanna become really good at this stuff, but I'm definitely not there yet. :/

<3

---

### Post by drpjkurian on 2009-07-25
Hi 
If your Ubuntu is recognising your hard drive, then click right mouse button by pointing on the hard drive icon and change the permission settings.

---

### Post by Zoey.Marie on 2009-07-25
> **drpjkurian said:**
> Hi 
If your Ubuntu is recognising your hard drive, then click right mouse button by pointing on the hard drive icon and change the permission settings.


It says "the permissions can not be determined" when I click the permissions tab in properties... :(

---

### Post by zeroseven0183 on 2009-07-25
According to some forums I've read, it's seems that it is either an Ubuntu bug or worse, a hardware issue already.

What version of Ubuntu are you using? Please try to install also NTFS Configuration Tool in Add/Remove and see if you can mount the partition again.

---

### Post by halitech on 2009-07-25
if you have a windows computer around, hook it up and then properly unmount it. Then try to connect to the ubuntu machine again and see if it will mount.

---

### Post by zeroseven0183 on 2009-07-25
And run a **Check Disk** also

---

### Post by Zoey.Marie on 2009-07-25
Re: zeroseven0183 and halitech

I don't have any Windows computers laying around. This one *was* my windows computer, haha. I tried it on my partner's mac, but that didn't do anything (and probably wouldn't be the same b/c of the NTFS thingie, huh?).

And I already installed the NTFS config tool. And I'm using 9.04...

any other thoughts? :/

---

### Post by LewRockwell on 2009-07-25
Probably the first thing I would do if your machine were here...

Boot up a LiveCD of Puppy Linux and see if it will mount the drive...

Then, if that doesn't work, I'd slip in a LiveCD PartedMagic and run Testdisk...

With luck Puppy might get your homework in time...

Testdisk, perhaps but doubtful...

.

---

### Post by Zoey.Marie on 2009-07-25
@ LewRockwell: I just might try those. Thanks. Hopefully it will work. I managed to get my homework done, so there's less of a rush... but it'd still be really nice if it could work soon. :)

In the meantime, I figured I'd bump the thread and also provide a little more information:
(warning, I don't know very much, so keep in mind my beginner-ness as I'm describing this stuff)

I tried to take it to a windows machine, and do the "safely remove" thing--'cause I guess with NTFS that can cause it to not mount correctly.
-- That didn't work, and, in fact, on the Windows machine, even though it showed up in MyComputer and in the Device Manager everything was working fine, it didn't read like there was ANY information on there (like, it didn't even say the size of the disk). Plus, it said that the filesystem was "RAW". No clue what any of that means.

So now, I am back on my computer--Ubuntu 9.4--and it's still giving me the same error messages above.

Other stuff:
lsusb shows it.
sudo fdisk -l shows it, AND shows how big it is and that it is NFTS...
sudo mount -t ntfs-3g /dev/sdb1 /mnt/ntfs  does nothing but give me the same error message as when I try and mount it through the GUI
sudo ntfsfix /dev/sdb1  doesn't really do anything either...  it says "pread: Input/Output error
Failed to calculate number of free clusters: Input/Output error.
FAILED
(then it attempts to correct, and everything says OK)"
But then it does the same "pread..... Failed to calculate number of free clusters" thing. Last thing it says is: "Remount failed: Input/output error."

So, while I'm trying this whole "Puppy Linux" and "PartedMagic" thing... Anyone got any other ideas????

HELP!!

---

### Post by Zoey.Marie on 2009-07-25
*bump*

Help me?

---

### Post by presence1960 on 2009-07-26
I know this can be a hassle, but why not boot from the Ubuntu Live CD and see if that will read the files. if so copy what you need over to your internal hard disk. Then unmount the external drive and use Partition Editor - System > Administration> Partition Editor or in terminal ```
gksu gparted
```
to format the drive and then set it up as NTFS or ext3 filesystem.

P.S. when you boot from the live CD choose "Try ubuntu without any changes to your computer". When the desktop loads open Computer in places and see if it will read your external drive. if so proceeed with above.

---

### Post by 3rdalbum on 2009-07-26
> NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware.

You will need to mount this disk manually, with the "force" option. I don't have any NTFS drives so I can't try this to make sure if it works.

First, make a mount point for the drive (where the contents of the drive will appear):
```
sudo mkdir /media/ntfs
```

Make it readable and writable by all users:

```
sudo chmod a+rw /media/ntfs
```

Now find out the device file name for that drive:
```
sudo fdisk -l
```

The first column shows the device file names, which begin in "/dev/", for all your disks. You can identify the NTFS one through the right-hand column.

Now you can put your device file name into this command (instead of "/dev/sdb5"):
```
mount -t ntfs-3g -o force /dev/sdb5 /media/ntfs
```

Copy over all your files from the drive to your home directory, because you'll want to erase the drive in Gparted and put a new filesystem on there that won't have this sort of problem in the future. If you're going to only use the disk on Linux machines, format it as ext3 or ext4. If you're going to share this disk with non-Linux computers, use Fat32 format.

Once you've used Gparted to format the disk, copy all your files back onto it.

---

