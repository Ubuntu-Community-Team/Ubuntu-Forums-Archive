---
title: "&quot;No init found&quot; - Ubuntu isn't able to start"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by illmatic on 2009-03-19
hey guys,

i really hope you can help me.
So first of all, The Problem is following. I got 4 partitions on a raid 0 array.
140gb - ubuntu ext3
360gb - ext 3 for data
2gb   - swap
80gb  - not partitioned.
Now today I tried to install windows on the 80gb partition, but I had no luck. I was in the partition table and wanted to format the 80gb partitoin, but windows failed. And i think windwos wrote something into my ext 3 partitions because after they didn't work, and chdsk failed, so I couldn't  or repair ubuntu. I read in some forums and i tried a command similar to this one "fchdsk -f" (f to force)
But that made everything even worse I think.
Now I get following message:

Target filesystem doesnt have /sbin/init
No init found. Try passing init = bootarg

BusyBox v1.10.2 (ubuntu 1:10.2.-1ubuntu7) built in shell (ash)
Enter "help" for a list of built in commands

(initramfs)

I really didnt know what to do and so I started the live cd and tried to recover my data but I couldn't manage to save it, even with the raid programm installed with synaptic (maybe the wrong commands but i simply typed mount /dev/xxx/nvidia xxx but this didn't work).
After I tried to install ubuntu on the 80gb partition, but there was only 1 available installation place.
Than I tried to repair with the ubuntu cd and there were partitions like sda /sdc  (total 4 partitions), but nothing with a RAID.

Last time I nearly lost my data through the raid 2 and I hope that this time I can at least save the data if I can't save my ubuntu.

I really hope that you got a solution for me because, I'm really upset :(

thank you for the answers
regards illmatic

---

### Post by jerrrys on 2009-03-26
this is probably a dumb question since you been around for a while, BUT is windows your first partition...

---

### Post by 123456789123456789123456 on 2009-03-26
The problem is in GRUB
more than likely, windows wrote ntldr.exe into the MBR, that either erased GRUB part1, or damaged it some how.  Try getting the supper grub disk, and repair GRUB in the MBR.

---

### Post by illmatic on 2009-03-27
Windows wasn't my first partition.
And i also fixed the grub with super grub disc :)
I think I'm going to just install ubuntu again, but I still got some data on the 2 ext3 partitoins, so I need to backup them but I actually don't know exactly how.
I tried the live cd and installed dmraid but somehow i couldn't mount the partitions eventhough they were recognized by the os.
And after I tried acronis true image and acronis recognized my partitions but when i clicked on the ubuntu main partitions to select the data I wanted to save Acronis crashes.
And if I click on the data partition (ext 3, too ) it just works.
Hm I guess I need to see how I'll save my data.
But in fact I'll start at tuesday with that because on tuesday there's my lanst exam (in english xD).
Is there any step by step tutorial how to mount ext3 partitoins on a raid array with the live cd?

---

### Post by stereomuffin on 2009-03-27
This thread might help: [http://forums.fedoraforum.org/archive/index.php/t-159780.html](http://forums.fedoraforum.org/archive/index.php/t-159780.html)

I not an expert but i&#314;l try to look a bit more for you :)
Perhaps you can use mdadm to view the status of the RAID, according to that article you should be..
Maybe assemble it and then you will be able to mount.

---

### Post by illmatic on 2009-04-02
well I just reinstalled everything and everything works fine.
I copied all of my data with acronis true image on an external device ( that took my about 6 hours! :D)
And after, today I reinstalled ubuntu.
And now I'm just trying to get everything to work :).
Thanks for the help :)

---

