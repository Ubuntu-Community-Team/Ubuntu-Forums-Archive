---
title: "Power Outage and Improper Shutdown"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by LRT on 2010-02-05
today i had a power outage and my ubuntu server was running (not plugged in to an UPS) so it was immediately shutdown. i booted the machine, how do i check if everything is ok on it? it wasn't really running anything when it got shutdown, i don't think it was even logged in, but it was powered on.

what kind of checks should i do? is there something i could do like chkdsk on windows?

---

### Post by audiomick on 2010-02-05
I think one possibility is "fsck"
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by LRT on 2010-02-05
ok so I was about to execute this command when it tells me the following:

```
fsck -yt ext3 /
```

```
WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage. 

Do you really want to continue (y/n)?
```

I said no because this scared the crap out of me... what am I supposed to do?

---

### Post by Ichtyandr on 2010-02-05
do not fsck mounted partitions, rather you could force a check on next reboot, run this "sudo touch /forcefsck" and reboot

---

### Post by Grenage on 2010-02-05
If the drive you are checking is mounted, don't run the scan.  Best thing to do is boot from a live CD and run a check there.

EDIT: Or follow **Ichtyandr**'s advice, which is way simpler.

---

### Post by audiomick on 2010-02-05
Easiest would be to run it from the live CD. I am pretty sure it is on there. I used it about 4 weeks ago, and can't remember having had to download it to do so.

---

### Post by LRT on 2010-02-05
> **Ichtyandr said:**
> do not fsck mounted partitions, rather you could force a check on next reboot, run this "sudo touch /forcefsck" and reboot

will this command automatically attempt to fix errors?

EDIT: I've ran this command twice and both times it has rebooted and told me that /dev/sda3 has 1.1% non-contiguous files and /dev/sda2 has 2.3% non-contiguous files. Does this mean there are errors on the disk? How do i know if the errors were fixed?

---

### Post by audiomick on 2010-02-05
read
```
man fsck
```
for a full explanation of the options. I don't know enough about what it does to be willing to make a statement.

---

### Post by Ichtyandr on 2010-02-05
> **LRT said:**
> will this command automatically attempt to fix errors?

well "man fsck" says that "fsck is used to check and optionally repair one or more Linux file systems" read if for the explanation of what it does, or look here: [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

generally however I never had errors on power outages on Linux so far it behaves really well. Today e.g. I had about 10-15 sudden power interruptions due to abnormal weather conditions, last one while I was typing this and so far its ok

---

### Post by LRT on 2010-02-05
> **Ichtyandr said:**
> well "man fsck" says that "fsck is used to check and optionally repair one or more Linux file systems" read if for the explanation of what it does, or look here: [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

the manpage for fsck says to use the -a flag to "Automatically repair the file system without any questions". But how do I use this flag with:

```
sudo touch /forcefsck
reboot
```

there is no manpage for forcefsck.

please read my edit from post #7.

---

### Post by audiomick on 2010-02-05
There is no "man" for /forcefsck because, I think, that is a file.
According
```
man touch
```touch is a command to change the timestamp on something, so I think
```
sudo touch /forcefsck
```doesn't directly call up "fsck" itself, but rather, it "tricks" the mechanism that invokes the regularly scheduled file check into thinking it is due on the next boot.

I think if you want to run "fsck" with specific options, the easiest would be to run it from a live CD.

"non-contiguous" is the state that is corrected by a de-fragmentation. It means that bits of a file are stored at different locations, instead of the file all being in one block. I don't think that this is a problem, particularly at that low percentage, but maybe someone else knows something to the contrary.

---

### Post by LRT on 2010-02-05
> so I think
```
sudo touch /forcefsck
```doesn't directly call up "fsck" itself, but rather, it "tricks" the mechanism that invokes the regularly scheduled file check into thinking it is due on the next boot.

this makes sense, thanks.

> I think if you want to run "fsck" with specific options, the easiest would be to run it from a live CD.

I'm going to try this, but it would be nice to know if there is a way of doing this (filesystem check with automatic repairs at boot time) without the live CD. This is what I really want to be able to do.

> "non-contiguous" is the state that is corrected by a de-fragmentation. It means that bits of a file are stored at different locations, instead of the file all being in one block. I don't think that this is a problem, particularly at that low percentage, but maybe someone else knows something to the contrary.

Well, before the power outage, I've never seen this "non-contiguous" message during one of the regularly scheduled disk checks that happen every 20 boots or so... So was this fragmentation caused by the power outage? I don't know.

---

### Post by bodhi.zazen on 2010-02-05
There is always some degree of fragmentation, a few % is nothing to be concerned with.

Fragmentation is only a problem when it becomes severe enough to affect performance, and is rare with Linux.

ext4 and btrfs have the capability, in theory, for defragementation, but I have not seen it implemented as of yet.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

By comparison, I have seen scans on Windows boses running slowly where fragmentation is in striking, 50 %, 200 % , and up.

Here you can see , Windows seems to feel 7 % fragmentaion is "OK"

[http://blogs.technet.com/askperf/archive/2008/03/14/disk-fragmentation-and-system-performance.aspx](http://blogs.technet.com/askperf/archive/2008/03/14/disk-fragmentation-and-system-performance.aspx)

---

### Post by audiomick on 2010-02-05
> **LRT said:**
> ...if there is a way of doing this (filesystem check with automatic repairs at boot time) ...
I really don't know for sure, but I have a feeling that this is what it does. Don't know where to look to find out, sorry.


> Well, before the power outage, I've never seen this "non-contiguous" message during one of the regularly scheduled disk checks that happen every 20 boots or so... So was this fragmentation caused by the power outage? I don't know.

I doubt that the "out" caused it. Fragmentation happens when the file system is running correctly and decides it needs to break up the file. Imagine putting your shoes in an overfull cupboard. If you are able to complete the job, you might end up with one on the top shelf and the other on the bottom shelf. If the door bell rings in the middle of things, you might end up with one in the shelf, and the other on the floor, i.e. a broken file.

as bodhi.zazen pointed out, windows systems create some astonishing amounts of fragmentation and live with it fine, if slowly. A couple of percent is not an issue.

---

### Post by LRT on 2010-02-05
well i ran fsck from an ubuntu live cd. the check was very quick, practically instant.

```
fsck -aCVt ext3 /dev/sda3
```

output told me the filesystem was clean, so i guess all is good. thanks for the help!

like i said, would be nice if i can do this without the live cd, and on the next boot instead.

---

### Post by tgalati4 on 2010-02-05
Well if you look at the bootup messages (Alt-F1) if you don't see them during boot, you will see that an fsck is automatically performed on all filesystems that are mounted.  So a hard power off will automatically trigger an fsck on the next power-on.

If fsck encounters errors that can't be fixed automatically, then you are dropped to a limited shell where you can run fsck manually and interactively and try to recover the disk.  Normally, a severe head crash will lose some files and the fragments will appear in /lost+found.  

That is why an UPS is important.  You want to keep those disks spinning and the server humming along.

---

