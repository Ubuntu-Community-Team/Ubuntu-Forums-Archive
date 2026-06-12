---
title: "Help, accidently locked myself out of Windows 7 on a dual-boot."
date: 2011-05-23
forum: New to Ubuntu
---

### Post by ultimania92 on 2011-05-23
First and foremost, I had ubuntu 11.04.

I made a stupid mistake while in windows 7, and nuked the partition that contained ubuntu 11.04 and the swap file partition. Now I can't even recover or boot back into windows 7 seeing how I nuked GRUB by accident.

Help? I just want to recover it so I can get Windows 7 back up and running. This is an Acer Aspire One, and I cannot get the recovery partition to respond, in that it just freezes before it can boot in, so that option is out.

---

### Post by ultimania92 on 2011-05-24
> **suvra.saha79 said:**
> I think you may reinstall your windows7 formatting your controller drive.

Actually, after a bit of complacent rage, apparently reinstalling through the live usb seems to be a bit of a fix. We're done here until I figure out my next move.

---

### Post by Hedgehog1 on 2011-05-24
When you deleted the Ubuntu partition, you removed most of the supporting files for grub.

Next time, you can:

1) Reinstall Ubuntu (as you have already found out)

2) Do a windows FIXMBR to boot directly into windows:

Fix MBR

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

***The Hedge***

:KS

p.s. It is worth creating a windows recovery/rescue CD now, so you are prepared for next time.

---

### Post by Sef on 2011-05-24
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk"). It can recover deleted partitions.

---

### Post by Megaptera on 2011-05-24
> **suvra.saha79 said:**
> I think you may reinstall your windows7 formatting your controller drive.
A drastic step _unless_ you've used a live CD to make a backup of all your important docs, pics , vids etc to external media _first_.

---

### Post by Mark Phelps on 2011-05-24
If you're still interested in reclaiming access to Win7 (couldn't tell from your last response ...) then go to the link below,download and burn an ISO of the appropriate Win7 image, boot from that, and run Startup Repair three times (yes ... three times):

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

