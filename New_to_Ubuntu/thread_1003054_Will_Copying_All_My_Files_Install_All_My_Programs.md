---
title: "Will Copying All My Files Install All My Programs?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by justinram22 on 2008-12-05
Hello, I switched to ubuntu about 1 year ago, and i've been longing to play my games again!, so i figured i'd reinstall ubuntu, and then install windows again on a 30 gb Partition (i have a 160 gig hard drive) and install my games.  Now my question is, I have a external hard drive, so i already figured i'd put all my files on it, but would it be possible to put my application files on it, so that when i copied them all to my freshly installed ubuntu, would they install? or do i have to install them all again 1 by one?  Also, is there a way to shrink my ubuntu partition, without erasing all my data? because i think that might be easier then doing a complete reinstallation, Any and All help i greatly appreciated!

---

### Post by utsuprainfra on 2008-12-05
> **justinram22 said:**
> Hello, I switched to ubuntu about 1 year ago, and i've been longing to play my games again!, so i figured i'd reinstall ubuntu, and then install windows again on a 30 gb Partition (i have a 160 gig hard drive) and install my games.  Now my question is, I have a external hard drive, so i already figured i'd put all my files on it, but would it be possible to put my application files on it, so that when i copied them all to my freshly installed ubuntu, would they install? 


The problem would be libraries and files that your applications may need.  It could be possible to just mount that external drive as /home /lib etc. but tricky and things would end up getting ugly.  You could probably find a way to get the version db and make it re-install itself with apt-get, thus avoiding the piecemeal process.  That would probably be my approach.

> **justinram22 said:**
> 
or do i have to install them all again 1 by one?  Also, is there a way to shrink my ubuntu partition, without erasing all my data? because i think that might be easier then doing a complete reinstallation, Any and All help i greatly appreciated!

Re: shrinking a partition 

You can use gparted I believe or partition magic.  I've used gparted.  There's a bootable disc available somewhere.

---

### Post by handydan918 on 2008-12-05
If you copy your whole system disk, yes, you will copy programs too. rsync is good for this. Something like rsync -av <SOURCE> <TARGET>

---

### Post by utsuprainfra on 2008-12-05
But will that preserve his software version information in synaptic / apt whatever?

---

### Post by Gannon8 on 2008-12-05
I would actually use SystemRecoveryCD to make a partition image and then restore it to your own drive. You can grow it with GParted if you need to.

But yes, copying/pasting will work

---

