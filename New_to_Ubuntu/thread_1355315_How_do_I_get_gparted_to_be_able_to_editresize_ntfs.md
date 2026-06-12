---
title: "How do I get gparted to be able to edit/resize ntfs partitions"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by josephellengar on 2009-12-14
For some reason the gparted that I have isn't able to do anything with ntfs partitions, which is obviously a problem considering that I need to be able to have windows on the computer as well.  Any help would be great.  Thanks!

---

### Post by cartisdm on 2009-12-14
What errors are you getting when trying to resize the NTFS partitions?  Are you running a LiveCD or within Ubuntu?

Here is a good graphical guide on resizing partitions, [take a look]("http://gparted.sourceforge.net/larry/resize/pdf/Resizing.pdf")

---

### Post by audiomick on 2009-12-14
I think that either you are trying to do things in a wrong order, or maybe the partition is mounted.

One thing that stumped me for a while is that gparted is very step by step.

for instance:
If you have, say, three partitions, a bit of unallocated space between 2 and 3, and want to make 1 bigger, you have to move the right side of 2 to the right, then the left side of 2, then the right side of one.

gparted can deal with ntfs, definitely.

here is some reading.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by tom.swartz07 on 2009-12-14
if youre using it from the installed desktop, you need to install the ntfsprogs package

sudo apt-get install ntfsprogs

restart or refresh your gparted and youll be all set

---

### Post by drs305 on 2009-12-14
> **rossholley said:**
> For some reason the gparted that I have isn't able to do anything with ntfs partitions, which is obviously a problem considering that I need to be able to have windows on the computer as well.  Any help would be great.  Thanks!

I was surprised to find my current Karmic gparted version didn't support ntfs by default. You can check gparted's capabilities by selecting View, File System Support. If ntfs isn't supported, install ntfsprogs and restart gparted.
```

sudo apt-get install ntfsprogs
gksu gparted

```

---

### Post by josephellengar on 2009-12-14
> **cartisdm said:**
> What errors are you getting when trying to resize the NTFS partitions?  Are you running a LiveCD or within Ubuntu?

Here is a good graphical guide on resizing partitions, [take a look]("http://gparted.sourceforge.net/larry/resize/pdf/Resizing.pdf")

I'm not getting an error.  On both the live cd and the installed system the option to deal with the partition (which is not mounted) is simply grayed out.  I also tried using the gparted live cd.  And I tried it with ntfsprogs installed.  I'm doing this on a clean dell notebook system, only with the recovery partition deleted, so I was beginning to think that dell had somehow locked the hard drive so it couldn't be repartitioned.

---

### Post by oldfred on 2009-12-14
If you do not have a clean shutdown on the windows partition gparted (and ubuntu) will not work with it. And it cannot be in hibernation. You may have to run checkdisk in windows to make sure it is ok.

My install of Karmic worked just fine with the fat & NTFS partitions that I am mounting. Well I was originally having every text file as executable but I changed my fstab and it is fine.

---

### Post by josephellengar on 2009-12-14
Oh, okay.  That's really helpful.  Thanks!  Will the gparted livecd also be able to edit/create ntfs partitions?  That's what I typically use.  I'm just trying to eliminate possibilities of why I'm having this problem.  My cd has the latest version.  I burned it today.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Yes, you can create and edit NTFS partitions.

---

### Post by josephellengar on 2009-12-14
> **ST3ALTHPSYCH0 said:**
> Yes, you can create and edit NTFS partitions.

OK, thanks.  I'll try all of this out and report back tomorrow once I'm in front of my computer.

---

### Post by mikechant on 2009-12-15
If you haven't already done this I'd advise you stop right now and read this first:

Although gparted can resize NTFS partitions, Windows doesn't always like it.

I resized my main Vista partition with gparted and when I attempted to boot windows I got a blank screen. However, I decided to be patient. About 4 hours later, Windows finally booted after doing some sort of filesystem check/rebuild, and was OK after that. However, other people have reported not being able to boot at all in this case, and it seems like a common problem, specifically when shrinking NTFS partitions.
It doesn't always happen, but the reccomendation is to always use the relevant Windows utility if shrinking NTFS, then use gparted for anything else.

If you search these forums I think you should be able to find some examples of this problem.

---

### Post by josephellengar on 2009-12-15
> **mikechant said:**
> If you haven't already done this I'd advise you stop right now and read this first:

Although gparted can resize NTFS partitions, Windows doesn't always like it.

I resized my main Vista partition with gparted and when I attempted to boot windows I got a blank screen. However, I decided to be patient. About 4 hours later, Windows finally booted after doing some sort of filesystem check/rebuild, and was OK after that. However, other people have reported not being able to boot at all in this case, and it seems like a common problem, specifically when shrinking NTFS partitions.
It doesn't always happen, but the reccomendation is to always use the relevant Windows utility if shrinking NTFS, then use gparted for anything else.

If you search these forums I think you should be able to find some examples of this problem.

Oh ... thanks for the warning.  I'll keep this in mind when I install.  Is this a vista-only issue?  I didn't have a trouble when installing it on my XP machine.  (Which, for some reason, did allow me to edit ntfs partitions)

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
I don't know about shrinking, etc, but I can say that linux won't use partitions that have been joined with the windows partition utility. That makes them dynamic partitions, and linux won't deal with them. I have only dealt with data partitions with Gparted, never system, so I'd say that the above advise is prudent.

---

### Post by natravis on 2009-12-15
> **rossholley said:**
> Oh ... thanks for the warning.  I'll keep this in mind when I install.  Is this a vista-only issue?  I didn't have a trouble when installing it on my XP machine.  (Which, for some reason, did allow me to edit ntfs partitions)

You originally said you were installing to a "clean" system, meaning you wanted to wipe out windows completely. If that is true, you can erase all partitions.

If you have a Windows partition and you would like to keep it, then boot into windows and shrink the partion from the Disk Management utility (Start>Rt click on My Computer>Manage>Storage>Local Disk Management> Find correct partition>Rt click on partition>Shrink Volume) then use GParted to expand into the newly freed up space. You will avoid all of the unpleasant issues mentioned about Windows having to rebuild files.

---

### Post by oldfred on 2009-12-15
Herman on Gparted old gparted error and not in Ubuntu but still use Vista partitioner for safety.
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by mikechant on 2009-12-17
oldfred said:
> Herman on Gparted old gparted error and not in Ubuntu but still use Vista partitioner for safety.
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.

Thanks, that's interesting. I did suspect the 'round to cylinder' option might have caused the start of the windows partition to move rahter than just the end, as you would expect with a shrink-from-end operation, but it was only a guess.
I think it's still best to use Windows for shrinking its own partitions if that's possible since MS could make other changes at any time which might cause gparted to screw up.

rossholley said:
> Is this a vista-only issue?

Looks as if it applies to Vista and Win7, not to XP, but my only experience is with Vista.

---

### Post by cartisdm on 2009-12-17
> **mikechant said:**
> If you haven't already done this I'd advise you stop right now and read this first:

Although gparted can resize NTFS partitions, Windows doesn't always like it.

I resized my main Vista partition with gparted and when I attempted to boot windows I got a blank screen. However, I decided to be patient. About 4 hours later, Windows finally booted after doing some sort of filesystem check/rebuild, and was OK after that. However, other people have reported not being able to boot at all in this case, and it seems like a common problem, specifically when shrinking NTFS partitions.
It doesn't always happen, but the reccomendation is to always use the relevant Windows utility if shrinking NTFS, then use gparted for anything else.

Wow that's really interesting.  Good info!

---

