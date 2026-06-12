---
title: "The recovery issue"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by ed bear on 2011-03-07
THE ISSUE: USING Drive Image and ext2 partitions to manage backup and recovery.

I have dug through piles of posts and archives about backup and restore, but have yet to find a basic way to what we did with DOS computers - format, SYS and copy in our files.

Where's the simple boot disk preparation that lets us set up a disk to receive a backup?  Or a comprehensible way to do it from a LiveCD?

Clonezilla looked good.  But at hundreds of megabytes, it's never going to fit a floppy.  Well, it's a pain, but I can make a boot CD... but I can't download a file that big on dial-up.  And it seems to still not give one a bare-metal installation with boot working that can be made from any storage filesystem.  (I hope I'm wrong on this.)

At this point, I'm ready to reinstall on and ext2 filesystem and use good old reliable boot-from-floppy, run-from-floppy Drive Image.  It would let me make numerous staged backups and keep them on whatever form of media I want, and restore from an image (except for GRUB, but I can always just run an install and abort it if that's trashed).

Is there any reason to really not use ext2, other than its less robust recovery from crashes?  Just how dangerous is it to be considered these days?

Or is there a version of Drive Image out there that handles ext3 or more modern filesystems?  I already own version 6.0 (2002) as well as the newer Norton-Branded version 5.6 (2004).

Every new user needs to start with learning how to save and then restore his system from scratch.  It's a fundamental responsibility of any user.  Why are all the common systems offered unable to do this?  Sure, cp will copy all your files, if you learn which to exclude - but how to get the disk ready to boot it?

Is there a really good guide to the whole Ubuntu boot process, most particularly in 10.04 and 8.04 for my purposes?
ED BEAR

---

### Post by cariboo on 2011-03-07
I use clonezilla all the time, if you are on dialup, you can buy a copy [here]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/clonezilla/clonezilla-live-12659-live-cd-pc.html"). I just cloned a 160Gb Windows 7 hdd to a 500Gb hdd, it took less than an hour using a slow usb connection, that include time figuring out why the old disk was offline after booting from the new disk.

Greetings from Willy's Puddle. :)

---

### Post by ed bear on 2011-03-10
DECLARATION OF SUCCESS
======================
Things went as planned.  The ext2 partition was comprehensible to Drive Image, and I could boot from floppy to create the image.  A virgin Hardy install was 2006MB, and high-compression settings took about 10 hours to reduce that to a 760MB image file.

Part of that slow compression is the result of backing up to the same physical drive, which keeps the heads moving a long way.  It should be faster to a separate physial device.

Drive Image didn't want to write the image to an ect2 or ext3 partition, but my habit has always been to keep four FAT-16 partitions on the disk for use with the simplest of environments and tools.  After writing, I an use the running Linux to move the file out to storage.  In particular, I should probably be able to let my Linux root partition grow to about 6GB and still fit on a DVD-R.  When needed, I could combine some of the FAT-16 partitions to create a FAT-32 temporarily (or longer) when the image exceeds 2GB.

Ideally, I'd hook up an external drive to make the writing go faster, boot to Linux and burn a DVD.

Restoration after replacing the Linux partition with a working DOS boot and system image went very quickly - less than a half hour - I have a lot of confidence in these tools and they work as always.  For those who are not yet confident in hard drive partitioning and formatting under Linux, This is a path of comfort and an insurance policy during learning.

(Now... why does removing intermediate kernels under Synaptic now trash the boot proess?  It didn't used to..)
ED BEAR

---

### Post by ed bear on 2011-03-12
Noting large discrepancies in restore times using different versions of Drive Image, and previous experience having told me I could do better, I tried a few combinations and discovered the 1-hour compressed backup was pretty much a worst-case scenario.  Using a DOS 6.22 disk instead of the Caldera DOS to boot, and PowerQuest's Drive Image 6.0 instead of the later Norton version, I backed up my now fully-configured 3.5GB Hardy install in less than an hour, yielding a 1.8GB image file.

Note that this was achieved WITHOUT turning off any verification or checking options.  Now, even if I do have a disaster that wipes out my ext2 filesystem, I can recover onto any hard drive.

Drive Image and its maker, Power Quest, are sadly no longer with us, but many of us still have copies of it around.  And no self-respecting geek would work on a computer that couldn't boot from a floppy, right?

ED BEAR

---

