---
title: "Help with partitions and data areas"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by ozstar on 2010-06-18
HI,

I have just loaded 10.4 and I am have messing around with a few things and like it a lot.

As a Windows egghead from day 1 Dos, I am trying to get my head around this different concept.

When I loaded 10.4 I accepted the whole 40 GB disk partition. but now I maybe should have an area where my data is kept away from the os in case I need to extricate one from the other.

First up I have 5 GB of MP3's which I want in an MP3 directory.

Can I get some guidance here please?

oz

---

### Post by nhasian on 2010-06-18
hello ozstar,

many people will suggest you create a separate /home partition.  most likely a 12 or 15GB root partition is plenty.  i think my root partition has about 4GB of data now.  All of your settings, preferences, documents are stored in the /home partition so it makes it easy to backup.  Personally I also have a dedicated /data partition where i keep my media (music, videos, etc) since it takes up a lot more space.

you can have up to four primary partitions per hard disk.  you can use one of these primary partitions as an extended volume to make additional logical disks if you need more partitions.

---

### Post by MooPi on 2010-06-18
Through the software center or Synaptic install gparted. Gparted is an exceptional partitioning tool and will let you resize and create a partition just for your personal files.

---

### Post by cariboo on 2010-06-18
The easiest and safest way to resize a partition is to use the Live CD. Boot from the CD and once at the desktop go to System-Administration->Gparted. Once gparted has started just drag the right arrow towards the left.

I normally set my partitions 10Gb for /, twice the amount of ram for swap and the rest of the hard drive for /home. With a separate home partition, if you have to do a reinstall, you only have to install on / and leave /home alone.

---

### Post by nhasian on 2010-06-18
it should be noted that you should not modify any partitions while they are mounted - which is probably why gparted isn't installed on the ubuntu desktop by default but rather is on the live Boot CD :)

so if you want to resize/add/delete any partitions boot from the liveCD and then go to system-> administration-> gparted

[COLOR="Red"]NOTE[/COLOR] as usual always backup any critical data before making changes to your hard disk.

> **MooPi said:**
> Through the software center or Synaptic install gparted. Gparted is an exceptional partitioning tool and will let you resize and create a partition just for your personal files.

---

### Post by MooPi on 2010-06-18
Oops must be drunk on good coffee :-)

---

### Post by ozstar on 2010-06-18
Many thanks guys..

I have Gparted and moved the arrow to the left to give me A 14.65 partition and a 22.69 unallocated one.

Where do I go from here to make this non alloc to be my data area?

oz

---

### Post by ozstar on 2010-06-18
Okay found it.. "+Create in selected unalloc".

I now have

unalloc      1MB
/dev/sda1    ext 4  14.65   3.88 used  boot
New Part 1   ext2 Media  11.72
New Part 2   ext2 Data 10.97
dev/sda2     extended  1.01
/dev/sda5    linux-swap  1.01

How does this look?

I am not sure whether the 2 new part were to be primary , log or extend.

Also is the Swap too small.  As the box is old and old small RAM should this be quite large.

Thanks

oz

---

### Post by nhasian on 2010-06-18
actually you want EXT4 partitions, not EXT2.  your not going to make a /home partition?  I dont think you would need two separate /media and /data partitions.  I'd recommend a /home and /data or /home and /media instead.  Swap only needs to be the size of ram you have.

---

### Post by ozstar on 2010-06-19
Hi and thanks..

I made those changes to reflect this..

They are all primary.

Is this now correct?

Appreciate the help.

unalloc      1MB

/dev/sda1    ext 4  14.65   3.88 used  boot

New Part 1   ext 4           9.89  (I called this Home but it didn't show)

New Part 2   ext 4 Data 12.80

dev/sda2     extended  1.01

/dev/sda5    linux-swap  1.01

---

### Post by k3lt01 on 2010-06-19
I set up my machines with / 10gb, SWAP 2 gb (I have 256mb of RAM so SWAP is often used), and the rest for /home. If I were you I would do what I normally do but have a 10gb /home, and the rest as /media or /data.

Just my 5 cents worth (2 cents isn't legal tender in Australia, lol).

---

### Post by ozstar on 2010-06-19
Hi and thanks..

Yes 2c used to be okay. Won't be long before the $1 will be history the way we are going!!

I am a little confused with what 'Home' is

Is the os partition called Home or is it an extra partition?

I really don't care what I set up as long as it is the best to keep things cleanly separate.

If I leave the set up of 14GB+ as the os  then leave the rest as another partion for Data. Is that the way to go?

I also tried to increase the swap but couldn't see how to do that

Thanks

oz

---

### Post by k3lt01 on 2010-06-19
/home is where your user setting are often, not always, kept. It is like the "user and settings" folder in Windows which most people now put on a D:\ drive. The OS proper is put in / (often called root) and it is like the Windows C:\ drive.

It is best to try and keep them as separate partitions, this helps to make it easier to keep important information safe from loss in the unlikely event of an OS failure. If this does occur you just reinstall to / and leave /home alone.

As far as I know you will require a /home of some sort. Keep it small if you want say about 10gb and then make the rest of your free space a separate /data partition.

---

### Post by ozstar on 2010-06-19
Thanks guys for all the help.. Got it done.. Took a while though..

Part 1 14.65  used 3,51 GiB
Part 2 Home 8.71 used 287MiB
Part 3          13.97 used 378MiB

Ready to rock!!   oz

---

