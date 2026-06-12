---
title: "[SOLVED] dd image of backed up /home"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-05
I don't know if I'm posing this question intelligently, but, here goes:

I had an external usb 2.0 80-gig drive. I had copied my /home to it. After some time, I shift-deleted the /home copy on the usb drive. I now want to make a bit-copy of the drive. I have plenty of room to copy it to my main drive (over 250 gig of free space). I want ... I don't know how to ask ... a mirror **image** of the drive. Or I want a bit-copy. That's so I can work on a copy of it and if I blow something up, I still have a way to copy the /home from the usb to a folder on my Desktop I'll call recovery-usb or something like that.

---

### Post by bodhi.zazen on 2008-12-05
Not sure what you are wanting exactly, but there are several ways to back up.

    [uhelp]community/BackupYourSystem[/uhelp]

---

### Post by ktrnka on 2008-12-05
Sounds like you if you just need your /home backed up, you could use [rsync]("http://samba.anu.edu.au/rsync/") or could try [flyback]("http://code.google.com/p/flyback/").

I personally use rsync, if you need a gui frontend for rsync, checkout [grsync]("http://www.opbyte.it/grsync/").

Flyback doesn't look too bad either.

---

### Post by snova on 2008-12-05
If you know this is what you want, this command would do it:

```
sudo dd if=/dev/<device> of="<backup>"
```

<device> is the file identifying the partition (sda3 or similar, **check first**), <backup> is where you want to put what will be a *voluminous* image.

sudo is necessary because you need root permissions to access block devices. But please, be careful with this... one false step, when playing with dd, could be disastrous.

It also requires that /home be a separate partition.

But really, there are better ways to do it... rsync is my preferred tool.

---

### Post by hyper_ch on 2008-12-05
you shouldn't use DD on a filesystem that's mounted.

---

### Post by Mark_in_Hollywood on 2008-12-05
OK, I'm not asking the question correctly.

I had /home on an external usb 2.0 hard disk drive. I shift-deleted it. All that is on that drive now is a folder named: Lost+Found. No other files have been written to the drive. I suppose technically the folder was named:

/media/marks80/home/home

but that should be beside the point.

I am trying to find a way to restore the 'damage' done by the delete. I have heard of testdisk with photorec as well as ext3grep. Either or both of these may do what I want.

In the meantime, I'm trying to make a literal, exact copy of the "state" of the external, usb 2.0, 80 gig drive. The reason for this is if photorec doesn't work, I would have a 2nd copy (is that, in computer speak, an "image" of the contents of the drive, blocks, inodes and all the rest, just the way they were immediately after the shift-delete was performed?

I am trying to make a 'copy' of it I suppose, but not in the mere commonplace meaning of the word.

---

### Post by handydan918 on 2008-12-05
OK, with that clarification, I think the dd approach is correct for your situation.

Good luck...

---

### Post by Mark_in_Hollywood on 2008-12-05
> **hyper_ch said:**
> you shouldn't use DD on a filesystem that's mounted.

So, I unmount the 80-gig usb drive BEFORE issuing the dd command? Or do you mean I MUST be in LiveCD session?

---

### Post by snova on 2008-12-05
Unmount the drive first. Things might go bad if it's mounted while you create a disk image. (On-disk filesystem structure might be corrupted or something, I don't know exactly.)

It'll be big...

---

### Post by Mark_in_Hollywood on 2008-12-05
Can I say this: Honestly!!! Size doesn't matter!!!

Thanks community, I'm marking this as solved.

---

### Post by Mark_in_Hollywood on 2008-12-05
Ok

---

