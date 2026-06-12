---
title: "gParted does not recognize HD"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Meetloaf13 on 2009-04-17
Hello,

I'm simply trying to reformat a HD.  gParted will only recognize the drive when I mount the drives.  Otherwise it hangs at the "searching partitions" screen.

I get the same result in Puppy & Ubuntu liveCDs.  The gparted live cd hangs also.

If I mount the drives & open gParted, I am able to see the partitions, but they are locked and I can't alter/delete them.

This all happened b/c a copy partition process was cancelled by my daughter.  Somehow it corrupted the disk so gparted is angry with it.  Strangely enough, I was able to copy all the data from the disk in Puppy just a few  minutes ago.

All suggestions welcome, thanks!

---

### Post by unutbu on 2009-04-17
GParted can fail if the drive has an incorrectly written partition table. Your symptoms seem to be consistent with this.

Since you were able to copy data off of the HD, would you be okay with blanking out the partition table and letting GParted rewrite it from scratch?

The partition table is located within the first 512 bytes at the start of the hard drive. What I'm suggesting would only blank out bytes 447--512 (the ones which hold your partition table).

---

### Post by Meetloaf13 on 2009-04-17
Totally, I want a blank disk anyhow.  I was going to remove the recovery partition and all.

Like this:
[http://ubuntuforums.org/showthread.php?t=734250](http://ubuntuforums.org/showthread.php?t=734250)

??

---

### Post by unutbu on 2009-04-17
So we don't make a mistake, please post the output of 
```

sudo fdisk -l
```
So we can make sure of the device name for the problem hard drive.
Please indicate which one it is.

---

### Post by Meetloaf13 on 2009-04-17
> **unutbu said:**
> So we don't make a mistake, please post the output of 
```

sudo fdisk -l
```
So we can make sure of the device name for the problem hard drive.
Please indicate which one it is.

Just one drive in the machine, partitions:

dev/sda1
...2
...3

---

### Post by unutbu on 2009-04-17
> **Meetloaf13 said:**
> 
Like this:
[http://ubuntuforums.org/showthread.php?t=734250](http://ubuntuforums.org/showthread.php?t=734250)

??


Yes, exactly.

The command
```

sudo dd if=/dev/zero of=/dev/hda  bs=512  count=1

```
would erase the partition table (and MBR) on /dev/hda. 
You'll have to change /dev/hda to the correct device name for your problem drive. Make very sure you get this right, since you don't want to blank the wrong drive.

Edit: I just saw your last message. 
```

sudo dd if=/dev/zero of=/dev/sda  bs=512  count=1
```
should do the job.

---

### Post by Meetloaf13 on 2009-04-17
I take it I'll need to be booted up in a LiveCD in order to do this...since the drives aren't mounted in gParted?  (I currently have gParted loaded, it says "No such file or directory").

Could I do this to all of the drives?  The reason I ask, is that it would be nice if I could stay booted in say Puppy or Ubuntu Live and use gparted there without having a "locked" drive.

Thanks a MILLION for your prompt replies, so much appreciated.

---

### Post by unutbu on 2009-04-17
You can use Puppy or the Ubuntu LiveCD.
Open a terminal, and issue the command.
I know "sudo" is needed for Ubuntu; if memory serves, Puppy uses "su" (all by itself first).

I'm not entirely sure if it is necessary or not, but it would not hurt to run
```

sudo umount /dev/sda{1,2,3}
```
first to umount sda1, sda2 and sda3.


> 
Could I do this to all of the drives?
Um, I'm confused. I thought you only have the one drive.
Do you mean partitions? The "sudo dd" command will blank all the partitions all at once, since one drive only has one partition table.

---

### Post by Meetloaf13 on 2009-04-17
Awesome, I'll do that and let you know how it all turns out.

You've been a lifesaver =]

P.S.  Yes, sorry about the confusion, I just barely noticed that I didn't need to put sda#, but just sda.

---

### Post by Meetloaf13 on 2009-04-17
Well, I thought all was going well, I was able to delete the partition table and now I am running into an error in gParted, perhaps I should take it up over in their forum, unless you are able to genious me through this one:

I create the label and begin to format the partition, I get passed teh "calibrate New partition", "create empty partition", set partitiontype on /dev/sda1/", but when it gets to the step "create new ntfs filesystem>mkntfs -Q -vv /dev/sda1" it says:
'The device doesn't exist, did you specify it correctly'?

Not sure what to do about this one :(

UPDATE: Unless you want to update this for future potential problems like mine, I'm in good shape.  The Vista installation formatting procedure worked just fine and I'm on my way!!

Thanks again!

---

### Post by unutbu on 2009-04-17
Hm. I'm not sure I know the answer to this one.
Perhaps try```


sudo partprobe
```
This should make the operating system aware of changes to the partition table. If the LiveCD does not know about partprobe,
then try rebooting.

---

