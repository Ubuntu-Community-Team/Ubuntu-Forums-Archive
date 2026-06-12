---
title: "Allocating more hard drive space to Ubuntu"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Musicmaker384 on 2011-03-21
I'm a noob to Ubuntu, and you can probably tell by the way I'm going to write this thread.

So anyway, I gave Ubuntu 17.0GiB of space on my hard drive when I installed it. That's alright for now, but since I seem to be using Ubuntu as much as I use Windows now I'd like to allocate a little more. I downloaded the GParted Partition Editor, but I when I run it I have no idea what I'm doing and I'm afraid I'll do permanent damage to my computer by messing with partitions. I simply want to take a bit more hard drive space and add it to the Ubuntu partition.

I know that dev/sda2 is the host partition and where most of the drive space is and the other two partitions are the recovery drive and HP Tools. That's about all I can really understand.

I guess I'm asking for sort of a tutorial on how to give more hard drive space to Ubuntu, any help would be appreciated.

I am running Ubuntu Netbook 10.10.

---

### Post by perspectoff on 2011-03-21
The problem isn't Ubuntu -- the problem is Windows. If you don't shrink the Windows partitions right, it won't boot properly.

Windows has utilities within it to shrink partitions. They should be used to rescue hard drive space.

An alternative is to use something like PerfectDisk to shrink the Windows partition (and in my experience is a great solution). PerfectDisk has a trial edition you can use.

Then you can use GParted to expand the Ubuntu partition.

I like this advice:

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

or

Kubuntuguide:
[http://www.kubuntuguide.info/index.php/All#Dual-Booting_Windows_and_Kubuntu](http://www.kubuntuguide.info/index.php/All#Dual-Booting_Windows_and_Kubuntu)

---

