---
title: "partition to install 10.04 on netbook"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by JamieWrites on 2010-05-15
Hi, 

I'm totally new to Ubuntu so please bear with me.

I've got an Asus 1001P with Windows XP that I'm trying to install Lucid Lynx onto via a USB. It's totally new so I don't need to keep anything.

So far so good, but now I've reached the Prepare Disk Space and it's got me completely confused - and none of the other threads that deal with similar issues have been any use whatsoever, mostly because they seem to refer to other tools/options/settings that don't appear on my screen.

My first question: should I try an older version that has (from what I can see) a more user-friendly (or idiot-friendly) set of options for this part of the install? Or does the netbook version have modifications that make this easier - and should I try that instead?

Alternatively, can I get some straightforward, thorough (and preferably step-by-step) instructions on what to do to get 10.04 installed?

Right now it's giving me two choices: wipe Windows completely and only   run 10.04 or specify partitions manually - which I've looked at but   which doesn't seem to give me the options that other posters have   suggested - i.e the partition with Ubuntu isn't specified, it doesn't   seem to allow me the option of creating any new partitions unless I   select the 'new partition table'.

Here's what the 'prepare partitions' page looks like:

**Device.....Type.....Mount Point...Format?..Size.....Used**
/dev/sda
    ../dev/sda1.ntfs.....................................                                                                                85904MB  8271MB
  ../dev/sda2  ntfs.....................................                                      66739MB  3221MB
    ../dev/sda3  fat32.....................................                                                                            7345MB    5113MB
  ../dev/sda4...............................................                                              49MB           unknown



Do specific instructions exist anywhere?

---

### Post by Ozymandias_117 on 2010-05-15
> **JamieWrites said:**
> **Device.....Type.....Mount Point...Format?..Size.....Used**
/dev/sda
    ../dev/sda1.ntfs.....................................                                                                                85904MB  8271MB
  ../dev/sda2  ntfs.....................................                                      66739MB  3221MB
    ../dev/sda3  fat32.....................................                                                                            7345MB    5113MB
  ../dev/sda4...............................................                                              49MB           unknown

Do you know what the current partitions are? There is an 85 gig, 66 gig and 7 gig... I would assume the 7 gig is a recovery partition... One of the other two is Win XP, but what's the last?

---

### Post by cariboo on 2010-05-15
I bought a netbook about 2 month ago, what I did is run the backup utility to backup the Windows installation, then used the manual formatting option to delete the existing xp partition and then created a 10GB partition for / , 2GB swap and the rest for /home.

I tried many of the different netbook remixes before deciding on the UNE. I'm quite happy with it, as everything worked out of the box.

---

### Post by JamieWrites on 2010-05-15
I've got no idea what any of it means, sorry - that's just what's there. 

And the whole thing is giving me a headache. Would I be better off with a version that I don't have to do so much guessing with?

---

### Post by Ozymandias_117 on 2010-05-15
If you don't want to damage your XP partition, I'm afraid to give you any advice. Your partition table is somewhat strange, you have 3 partitions where, with what you've said, there should only be two...

---

### Post by JamieWrites on 2010-05-15
At this point it's looking like I've made a huge mistake in going for 10.04 because this partitioning business is so complicated and, because there aren't any clear instructions anywhere on how to make it work I've done all sorts of weird things to my hard drive and have no idea how to fix it.

I've attached a screen shot of how it currently looks - any idea how to get it back to how it was? Once that's done I think I'm going to download and try and install the previous version which seems about a million times simpler to run as dual-boot.

---

### Post by miyagison on 2010-05-15
I have a eee netbook and they partitioned the disk exactly lie that. If you are inexperienced with partitioning I do not recommend installing unless you are willing to give up your XP install ... its not a bad thing tho .. lol; however, after a few years of dealing with people and their computers I understand they like what they are familiar with .... so you still want XP ... when you install select the side by side installation and the second partition and it will dual boot for you and auto partition the space you designate.

---

### Post by miyagison on 2010-05-15
To fix that you need to reformat that partition. 
[http://windows.microsoft.com/en-us/windows-vista/Create-and-format-a-hard-disk-partition](http://windows.microsoft.com/en-us/windows-vista/Create-and-format-a-hard-disk-partition)

---

### Post by JamieWrites on 2010-05-15
> **miyagison said:**
> I have a eee netbook and they partitioned the disk exactly lie that. If you are inexperienced with partitioning I do not recommend installing unless you are willing to give up your XP install ... its not a bad thing tho .. lol; however, after a few years of dealing with people and their computers I understand they like what they are familiar with .... so you still want XP ... when you install select the side by side installation and the second partition and it will dual boot for you and auto partition the space you designate.

Thanks for the link to fix my current partition.

But the ongoing problem is that there is no option for side by side installation in 10.04 - at least not the desktop version. Would that be something that would be standard for the UNE? If so, I'll download that and try it instead.

---

### Post by miyagison on 2010-05-15
> **JamieWrites said:**
> Thanks for the link to fix my current partition.

But the ongoing problem is that there is no option for side by side installation in 10.04 - at least not the desktop version. Would that be something that would be standard for the UNE? If so, I'll download that and try it instead.

Definitely use the standard Ubuntu Desktop rather than the netbook version. I run Win 7/Ubuntu Desktop on mine and runs great.

---

### Post by JamieWrites on 2010-05-15
Okay, by some complete accident, whatever I did has now given me the option to have both side by side. 

Problem inadvertently solved - but thanks for the tips anyway.

---

