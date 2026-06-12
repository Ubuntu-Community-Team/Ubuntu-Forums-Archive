---
title: "Can someone briefly explain the whole disk mounting thing to me?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-07
I've looked on several sites for an explanation, but it's always about how to mount a drive and not what that actually means.

Why does Ubuntu have to mount drives?  What does "mounting" actually mean?   Does Windows do something similar that's just transparent to the user or is it a fundamental difference in how the OSes work?  The only things I've ever had to mount are disc images in Daemon Tools and such, but I'd imagine this is different.

---

### Post by sgosnell on 2010-03-07
Windows does the same thing, but just doesn't call it that.  When you plug a USB drive into a Windows machine, it mounts it, but asks what you want to use to open it.  Windows, by default, mounts every drive it finds automatically, while Linux doesn't.  Automounting every drive can be a security issue, and thus Linux makes you decide if you want to automount it.  You can tell Linux to automount all drives it finds, and it does that with every drive in fstab, and usually every drive attached at boot, but that isn't the default.

---

### Post by Everynameistaken on 2010-03-07
Insecure to automatically mount a local disk drive?  How so?

---

### Post by mosshorn on 2010-03-07
Mounting drives is just a fancy way of saying constant access. For instance, if you have a Windows partition, Ubuntu will not give access to that unless YOU click on it and give it privileges to. Kind of a "keep to your own so we don't hurt each other" thing. It treats Physical Drives (jumpdrives, portable Hard drives, dvds, etc) in the same fashion. Just access (in a nutshell).

---

### Post by steveneddy on 2010-03-07
> **Everynameistaken said:**
> Insecure to automatically mount a local disk drive?  How so?

Since you are the admin on your machine, you must tell the OS how to do certain tasks, not the OS telling you what you can do.

If you set your machine up to auto-mount drives, then it will.

You can set this up in the fstab.

---

### Post by candtalan on 2010-03-07
> **Everynameistaken said:**
>  What does "mounting" actually mean? 

Mounting a (drive) is effectively plugging it (not physically, but electronically, logically) into the existing running system so that it can be used. Saying Mounting is a quick way of saying that the existing running system is told to also use another system, what type the new system is, and some details like where to join it up, what is its name, which users have rights to use it  etc etc.

In more exactness, it is the file system that is mounted, not the hardware. The hardware drive might contain more than one partition, each with its own file system. It is the file system with its particular structure which is 'mounted', that is made to interface with the host running file system.

When you plug in a USB memory stick for example, in Ubuntu, it should normally auto mount. Then you use it. Then you arrange to safely remove it. This means 'unmount'.

If you wish, you can tell it to 'unmount' but leave it physically plugged in. It will not affect to running system now.

The 'unmount' (actually 'umount') command causes any uncompleted promises about data transfer to be actioned, making sure no data is lost. 

File system data actions are full of promises of action 'soon', but not necessarily 'right now'. A removable device Must be unmounted to ensure a completion of scheduled data changes.

this might help:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

You can see what stuff is mounted by using a terminal and just type 
mount

hth

---

### Post by J V on 2010-03-07
> **Everynameistaken said:**
> Why does Ubuntu have to mount drives?Its just the way it works, windows has to too> What does "mounting" actually mean?Activating the partition and hooking it up to the kernel> Does Windows do something similar that's just transparent to the user or is it a fundamental difference in how the OSes work?In windows it just mounts everything off the bat> The only things I've ever had to mount are disc images in Daemon Tools and such, but I'd imagine this is different.Nope, exactly the same, in fact, linux uses the same command, mime type, etc, for mounting images, CDs, HDs, SDs, etc etc ad infinitum

---

### Post by lisati on 2010-03-07
If memory serves correctly the origin of the term "mount" lies in actually physically putting something like a spool of tape or disk platter on a on the tape or disk drive, making it ready for access by the computer. I think there's a connection somewhere with the meaning of "mount" as in "mount a horse and get ready to ride it"

---

### Post by The Cog on 2010-03-07
Another concept you need to understand is the **mount point**. When you mount a partition, you have to specify where the contents of that partition should appear. For reasons I don't understand, you have to nominate a pre-existing directory to mount to. When you mount the partition, any contents in the mount point directory disappear and get replaced with the mounted disk contents, and the original contents become visible again once the partition is unmounted. I would have thought it would make sense for the mounted partition to appear as a new directory (like windows creating a new "drive letter"), but that just isn't how it works.

There is a file called /etc/fstab that specifies which partitions should be mounted at boot time, and where they should be mounted to.

---

### Post by asmoore82 on 2010-03-07
> **Everynameistaken said:**
> Insecure to automatically mount a local disk drive?  How so?

automounting is a mixed blessing, autorunning OTOH is just dumb:
[http://answers.yahoo.com/question/index?qid=20091101014702AAmGBdZ](http://answers.yahoo.com/question/index?qid=20091101014702AAmGBdZ)

---

### Post by asmoore82 on 2010-03-07
> **The Cog said:**
> Another concept you need to understand is the **mount point**. When you mount a partition, you have to specify where the contents of that partition should appear. For reasons I don't understand, you have to nominate a pre-existing directory to mount to. When you mount the partition, any contents in the mount point directory disappear and get replaced with the mounted disk contents, and the original contents become visible again once the partition is unmounted. I would have thought it would make sense for the mounted partition to appear as a new directory (like windows creating a new "drive letter"), but that just isn't how it works.

There is a file called /etc/fstab that specifies which partitions should be mounted at boot time, and where they should be mounted to.

Yes mount points are important, it's sort-of a Unix law to "Keep it Simple."
A by-product of that is the simple rule that there can be only one filesystem.
ALL devices must somehow expose themselves under this filesystem, hence mount points.

This provides the advantage of being totally transparent to users and their software.
My root partition and home folder are one 2 different physical partitions;
but I never had to do a bunch of tweaking where I moved the system "home" to
this other partition, I simply set this partition to mount at "/home" and
the OS and software couldn't really care less.

The Window's "Drive Letters" just turn my stomach, and BTW it is something
that was stolen verbatim from CP/M: [http://en.wikipedia.org/wiki/CP/M](http://en.wikipedia.org/wiki/CP/M)

---

