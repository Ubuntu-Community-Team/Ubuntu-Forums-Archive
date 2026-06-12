---
title: "How do I force a partition to be deleted?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-02-12
Hi!

I have a fat32 partition on one of my flash drives (it just so happens to be an Ubuntu-branded flash drive) that I would like to delete, but GParted complains that there is no response from the device.  I know the partition is somehow broken/corrupted, because Nautilus crashes if I try to open it. . . 

What can I do to force-delete the partition?

Thanks in advance!

---

### Post by MarblePanther on 2009-02-12
> **pi.boy.travis said:**
> Hi!

I have a fat32 partition on one of my flash drives (it just so happens to be an Ubuntu-branded flash drive) that I would like to delete, but GParted complains that there is no response from the device.  I know the partition is somehow broken/corrupted, because Nautilus crashes if I try to open it. . . 

What can I do to force-delete the partition?

Thanks in advance!

dd that sucker!

dd if=/dev/zero of=/dev/sdX bs=4096k   
EDIT: try bs=1M for faster speed on usb2 devices

X being your drive #   ex. sdb or sda
this will wipe your entire drive
then format it with gparted

---

### Post by pi.boy.travis on 2009-02-12
> **MarblePanther said:**
> dd that sucker!

Thanks for your reply!

How might I go about doing this?

---

### Post by MarblePanther on 2009-02-12
> **pi.boy.travis said:**
> Thanks for your reply!

How might I go about doing this?

see my edited post above

---

### Post by pi.boy.travis on 2009-02-12
OK, my both CPU cores are running at 100% for a few minutes now. . .   It's a 4 GB flash drive, should I be concerned. . . ?

Thanks for the dd advice.  That will come in handy. :)

---

### Post by MarblePanther on 2009-02-12
> **pi.boy.travis said:**
> OK, my both CPU cores are running at 100% for a few minutes now. . .   It's a 4 GB flash drive, should I be concerned. . . ?

Thanks for the dd advice.  That will come in handy. :)

it'll take a few minutes, but 100% on both? hmmm, that sounds a little intensive.

---

### Post by pi.boy.travis on 2009-02-12
It's still running.  The CPU's aren't at 100% anymore, but still in the 80% area.

---

### Post by MarblePanther on 2009-02-12
EDIT:

nvm, 4096k is 4M.

yeah 4096k is as fast as you should probably go with dd.

It might take up to 30 minutes

---

### Post by pi.boy.travis on 2009-02-12
SUCCESS!!!

Thank you very much!

---

### Post by MarblePanther on 2009-02-12
> **pi.boy.travis said:**
> SUCCESS!!!

Thank you very much!

No problemo!

---

### Post by pi.boy.travis on 2009-02-13
It came back. . . It came back after I rebooted this morning. . . 

I am beginning to wonder if this is a hardware problem. . . ?

How can I kill this zombie partition?  It has the syslinux boot loader on it, if that makes a difference.

---

### Post by MarblePanther on 2009-02-13
Try going into gparted and right-click on the drive and delete the partition, then select format to.... and choose a type.

Then apply the changes by going to edit, apply all operations.

If this doesn't work after dd'ing the drive, something funny is going on here...

Did your drive come with Ubuntu preloaded on it?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> Try going into gparted and right-click on the drive and delete the partition, then select format to.... and choose a type.

Then apply the changes by going to edit, apply all operations.

If this doesn't work after dd'ing the drive, something funny is going on here...

Did your drive come with Ubuntu preloaded on it?


OK, I get this error:

Attempt to write sectors 128-128 outside of partition on /dev/sdb.

Yes it did, but that original partition is long gone.  It was working perfectly, until I noticed the partition was corrupted yesterday. . .


This is the error I get if I try to create a new partition table:

Can't open /dev/sdb1: No such file or directory
Cannot initialize 'H:'
mlabel: cannot initialize drive

Unable to read the contents of this filesystem!
Because of this some operations may not be available

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> OK, I get this error:

Attempt to write sectors 128-128 outside of partition on /dev/sdb.

Yes it did, but that original partition is long gone.  It was working perfectly, until I noticed the partition was corrupted yesterday. . .

try right clicking on it and check for errors with gparted

It sounds like your drive is dying or the partition table is messed up on it

Anybody else out there got any ideas?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> try right clicking on it and check for errors with gparted

It sounds like your drive is dying or the partition table is messed up on it

Anybody else out there got any ideas?

dosfsck gives me this output this error:

No such life or directory
Abort

Same thing if I use GParted. . .

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> dosfsck gives me this output this error:

No such life or directory
Abort

Same thing if I use GParted. . .

Can you give me a screenshot of it in Gparted? (So I can see the layout and any errors?)

---

### Post by pi.boy.travis on 2009-02-13
[ATTACH]103276[/ATTACH]

[ATTACH]103277[/ATTACH]

[ATTACH]103278[/ATTACH]

Despite all this, I always see:

[ATTACH]103279[/ATTACH]

[ATTACH]103280[/ATTACH]

Thanks for your help with this so far.

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> [ATTACH]103276[/ATTACH]

[ATTACH]103277[/ATTACH]

[ATTACH]103278[/ATTACH]

Despite all this, I always see:

[ATTACH]103279[/ATTACH]

[ATTACH]103280[/ATTACH]

Thanks for your help with this so far.
hmmmm...

Can you write files to the partition?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> hmmmm...

Can you write files to the partition?



No, I can't write, read, or delete, with or without root privileges. . . The syslinux bootloader on the drive doesn't work, either.

---

### Post by unutbu on 2009-02-13
Just for kicks, let's try fdisk:

```
sudo umount /dev/sdb1
sudo fdisk /dev/sdb
```

Then type the commands marked in red:
This deletes partition #1:
```

Command (m for help): [COLOR="Red"]d[/COLOR]
Partition number (1-1): [COLOR="Red"]1[/COLOR]

```
This writes the change to disk:
```

Command (m for help): [COLOR="Red"]w[/COLOR]
```
This prints the partition table, to see the change has been made.
```

sudo fdisk -l /dev/sdb
```
Please post the output of these commands if it doesn't work.

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> No, I can't write, read, or delete, with or without root privileges. . . The syslinux bootloader on the drive doesn't work, either.

try this and see if you can read/write/exec:

sudo chmod -R a=rwx /media/disk/

If not, then I don't know what else...

---

### Post by pi.boy.travis on 2009-02-13
Still no good. . .  The partition still lives!

I get:

The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

from fdisk

Thanks for your reply!

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> Still no good. . .  The partition still lives!

I get:

The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

from fdisk

Thanks for your reply!

the chmod command simply changes the permissions on it

I really can't think of what else to do...

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> try this and see if you can read/write/exec:

sudo chmod -R a=rwx /media/disk/

If not, then I don't know what else...


I think my luck has run out.  It is Friday the 13th, after all. . . 

I still can't get that dang thing eradicated. . .

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> I think my luck has run out.  It is Friday the 13th, after all. . . 

I still can't get that dang thing eradicated. . .

What exactly are you trying to get rid of again? The .sys file?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> What exactly are you trying to get rid of again? The .sys file?

The entire partition would be nice, as I can't seem to get it working. . . 

I figured I could delete it or reformat it. . .

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> The entire partition would be nice, as I can't seem to get it working. . . 

I figured I could delete it or reformat it. . .

You're drive could be dead, but I wouldn't know, I've never had a dead flash drive... How old is it?

Have you tried the chmod command, then try writing to it?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> You're drive could be dead, but I wouldn't know, I've never had a dead flash drive... How old is it?

Have you tried the chmod command, then try writing to it?


Only about six months.  To the best of my knowledge it has not been damaged, or even removed without unmounting. . . 

Yes, and it would appear to be successful, but then Nautilus crashes if I try to unmount it. . . 

I'm at my wit's end.

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> Only about six months.  To the best of my knowledge it has not been damaged, or even removed without unmounting. . . 

Yes, and it would appear to be successful, but then Nautilus crashes if I try to unmount it. . . 

I'm at my wit's end.

What does  

umount /media/disk

say in terminal?

---

### Post by pi.boy.travis on 2009-02-13
> **MarblePanther said:**
> What does  

umount /media/disk

say in terminal?

surprisingly, umount works!  but. . . none of the changes I made since the last mount aren't applied. . . 


I'm about ready to invest in a newer drive.

---

### Post by MarblePanther on 2009-02-13
> **pi.boy.travis said:**
> surprisingly, umount works!  but. . . none of the changes I made since the last mount aren't applied. . . 


I'm about ready to invest in a newer drive.

Yeah, flash drives are really cheap now...sorry I can't further help you...I can't think of anything else

You can get 8gb's for 20$ and cheaper

---

### Post by pi.boy.travis on 2009-02-13
I think I still have an old XP partition on one of my older machines, I'll have to try that and see what happens. . .   I'll report back.

---

### Post by pi.boy.travis on 2009-02-13
I did indeed have an old partition, but it crashed while searching for drivers for the drive. . .

---

### Post by pi.boy.travis on 2009-02-13
Well. . . I'm not sure much more can be done. . .

Is there anything else I can try?

---

