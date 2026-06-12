---
title: "n00b needs hard drive help."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by 1BigBore on 2009-03-20
First I would like to thank this forum for all their help, that has enabled me to install and run **Ubuntu r 8.10** on this old clunker of a Dell workstation that I pulled out of a trash bin. (it had dual Pentium III [Coppermine] processers and 250 mb ram and an ATI all-in-wonder card.)  

That is not that much of a problem, but Disk Space is.  The OS install is on a 40gb hard drive (to work with the old BIOS of the computer) and is almost full.  I have a 320gb hard drive formated and installed, but I cannot figure how to mount it, or WHERE to mount it so that I can install stuff to that drive instead of my /home or / drive.  

_Many_ years ago I fiddled with RedHat Linux, but never did very much. I find myself feeling very stupid trying to do even these simple things.  Please help me with this, knowing that I know almost nothing about fstab editing and less about the text editors here in the Ubuntu world.

Thanks again.

---

### Post by PukingPenguin on 2009-03-20
More info than you may want, but [check this out]("http://sblinux.org/pages/symlink-home.html") anyway.

---

### Post by rajan on 2009-03-20
fstab will be helpful to you

i'll post mine when i get home



my fstab:
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/OLDHD    ext3    defaults        0          0

```

it looks like you have enough help though.

---

### Post by dwasifar on 2009-03-20
If you are just using it for yourself, there's no reason not to mount it somewhere in your home folder.

In your home folder, create a folder for a mount point.  Call it whatever you like.  "storage" perhaps.

If you already have the drive formatted, I'll assume you already know what its identifier is.  Let's assume it's at /dev/hdb and formatted to ext3.

Then *sudo gedit /etc/fstab* and add a line for the drive, like this:

/dev/hdb1 	/home/[your username]/storage        ext3    relatime,errors=remount-ro 	0       1

Save and then either reboot or type *sudo mount -a* in terminal and you should be good to go.

---

### Post by egalvan on 2009-03-20
> **1BigBore said:**
> that has enabled me to install and run **Ubuntu r 8.10** on **this old clunker** of a Dell workstation that I pulled out of a trash bin.
 (it had dual Pentium III [Coppermine] processers and[COLOR="Red"] 250 mb ram[/COLOR] and an ATI all-in-wonder card.)

Hey, that's a good machine you got there... 
I run older iron like this at home, and it runs very well, thank you.
but like any old jalopy, it needs a few tweaks here and there...
the best thing you can do for this potential hot-rod is to get more RAM.
256MB is really choking that machine.
Depending on the exact RAM you need, and your scrounging skills,
this can be a cheap upgrade.
 

> That is not that much of a problem, but Disk Space is.
  The OS install is on a **40gb hard drive (to work with the old BIOS of the computer) a**nd is almost full.
0  I have a 320gb hard drive formated and installed, but I cannot figure how to mount it, or WHERE to mount it so that I can install stuff to that drive instead of my /home or / drive.  


The BIOS hard-drive limit may be problematic under Microsoft,
but for Linux, take a look at this tutorial...

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

You will probably find the rest of the web site to be very useful, 
as is aysiu's web site (he's a regular on this forum :)...

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Although having two or more hard drives in the computer is a good idea, maybe because I do it all the time...

> _Many_ years ago I fiddled with RedHat Linux, but never did very much. I find myself **feeling very stupid** trying to do even these simple things.  Please help me with this, knowing that I know almost nothing about fstab editing and less about the text editors here in the Ubuntu world.
Thanks again.

Hey, we were ALL of us beginners at one point... 
(there was a time even Torvalds didn't know what Linux was :P)

And one final thought,

firing up gparted and posting screen shots of your two drives will help us help you.

(screen shots is found under Applications->Accessories,
but there is a short-cut that I don't recall right now.)

---

### Post by 1BigBore on 2009-03-20
Thanks for all the replys.  I am not up to doing screen shots yet, but here is what my hard drives look like:
```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7cbf7cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        4998    39945622+   5  Extended
/dev/sda5              26        1300    10241406   82  Linux swap / Solaris
/dev/sda6            2828        2884      457821   83  Linux
/dev/sda7            1301        2827    12265596   83  Linux
/dev/sda8            2885        4905    16233651   83  Linux
/dev/sda9            4906        4998      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000514c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12764   102526798+  83  Linux
/dev/sdb2           12765       25512   102398310   83  Linux
/dev/sdb3           25513       38913   107643532+   5  Extended
/dev/sdb5           25513       32523    56315826   83  Linux
/dev/sdb6           32524       38913    51327643+  83  Linux

```

It looks like what I expected to see....

My 'gparted' "button" has disappeared, and I have no Idea why...

On a side note, I was going to get more ram, but this uses an obsolete dram that costs $140/250mb.  (or something like that)  I thought not.
I used the smaller disk to boot after I kept getting Grub Error 18 with the other one.  Anyway, can you guys that started with the great generic data help with something a little more exact for a guy that does not know enough yet to make stuff up that isn't exact.  :rolleyes:

I haven't tried anything yet, because for me, fixing a mistake is a re-install...  and the system is working now, and I am in no hurry to "undo" that!  :D

thanks again...

p.s.  here is my fstab file"
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=24c8dc38-bfee-4d72-9770-529cd27b420c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=7052817a-7103-441f-a216-6137e735c1a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
It looks kinda odd, like with extra spaces, but what do I know?

---

### Post by egalvan on 2009-03-20
> **1BigBore said:**
>   I am not up to doing screen shots yet

OK, that is super easy.

First:
Keyboard way:
the "Print Screen/SysReq" key will pop up a generic screen-grabber.

Second:
Mouse way:
Move your mouse to the "Applications" menu; this is at the top-left corner of your screen (if you are using Gnome)
then to the "Accessories" menu;
under this menu you should find a "Take Screenshot" icon.

I prefer the second one because it allows options;
a delay before "taking" the pic.
a choice as to the whole screen, or selected window.

It can't hurt anything to try this... it just writes png files...
you can always delete them... :)

> , but here is what my hard drives look like:
```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7cbf7cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        4998    39945622+   5  Extended
/dev/sda5              26        1300    10241406   82  Linux swap / Solaris
/dev/sda6            2828        2884      457821   83  Linux
/dev/sda7            1301        2827    12265596   83  Linux
/dev/sda8            2885        4905    16233651   83  Linux
/dev/sda9            4906        4998      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000514c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12764   102526798+  83  Linux
/dev/sdb2           12765       25512   102398310   83  Linux
/dev/sdb3           25513       38913   107643532+   5  Extended
/dev/sdb5           25513       32523    56315826   83  Linux
/dev/sdb6           32524       38913    51327643+  83  Linux

```

It looks like what I expected to see....



Yeah, looks good to me  too...

> My 'gparted' "button" has disappeared, and I have no Idea why...

Fire up Synaptic, and search for "gparted"...
if it shows as 'installed' then just the icon is gone...
others will have to chime in on how to resurrect the icon...
if it shows as 'not installed', then select it for intallation.

> On a side note, I was going to get more ram, but this uses an obsolete dram that costs $140/250mb.  (or something like that)  I thought not.

Yeah, at those prices, I think not.
But that is probably a price you got at a box store (like bestBuy), right?
What type exactly does your machine use?

PC133 is going for about $50 for a pair of 512Meg sticks...
about half for a pair of 256Meg sticks.
(if your machine can use ECC-type memory, then you can get it cheaper. It's the 1Gig sticks are the more expensive... lots of folks are upgrading servers)
PC100 is usually cheaper in 256Meg sizes, somewhat in 512Megs.


RDRAM (RamBus) is a bit more expensive...
about $80-100 for a pair of 512Meg sticks.
less for a pair of 256Meggers.

eBay is your friend here.
As are smaller Mom&Pop computer stores/repair centers.
Sometimes they will toss this "obsolete' memory at you...

> **I used the smaller disk to boot after I kept getting Grub Error 18 with the other one.**
  Anyway, can you guys that started with the great generic data help with something a little more exact for a guy that does not know enough yet to make stuff up that isn't exact.  :rolleyes:


Well, that web-site I gave the link for had rather exact instructions... :)

> 
I haven't tried anything yet, because for me, fixing a mistake is a re-install...  and the system is working now, and I am in no hurry to "undo" that!  :D

if this is your only working machine, I can understand your lack of "hurry-up-and-break-it"...
if not, then many of us on this forum will tell you that breaking and fixing Linux is a great way of learning the system. :)

> 
thanks again...

p.s.  here is my fstab file"
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=24c8dc38-bfee-4d72-9770-529cd27b420c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=7052817a-7103-441f-a216-6137e735c1a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
It looks kinda odd, like with extra spaces, but what do I know?

The extra spaces are because of the editor you use.
The *nix world has many, many different text editors...
they don't all show text in the exact same way...


And by the way, just HOW FAR SOUTH are you in South Texas?

I can toss a rock into the Rio Grande from my house...
And it's not too much further to the beach at SPI...
??

We USED to have a Linux User Group at TSC/UTB... but it fell apart after four meetings...
I miss it.

Corpus Christi has an **excellent** group.. CC-Lug.
[www.cclug.org](www.cclug.org)

San Antonio has SatLug
[www.satlug.org](www.satlug.org)

Austin has AustinLug
[www.austinlug.org](www.austinlug.org)

Am I getting warm?

---

### Post by 1BigBore on 2009-03-21
> **rajan said:**
> fstab will be helpful to you

i'll post mine when i get home



my fstab:
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/OLDHD    ext3    defaults        0          0

```

it looks like you have enough help though.

Thanks.  I will look at this closer and try to understand what I need to do.  It sometimes takes a while for me to get back, and I _do_ appreciate the response.

---

### Post by 1BigBore on 2009-03-21
I think that I have attached a couple of screen shots of my hard drives.  Does this help?  I am finding the simple syntax of the fstab hard for me to translate to what I need.  Again, thanks for any help

---

### Post by rajan on 2009-03-22
the syntax and everything is pretty clearly outlined at the ubuntu site -- it's definitely one of the best explanations i've found. if the extra spaces are throwing you off, just remember that a space is as good as 2 spaces. also, definitely back up your file before you start screwing with it. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

where are you right now in the grand scheme of problems?

---

### Post by 1BigBore on 2009-03-22
> 
where are you right now in the grand scheme of problems? 

I got my gparted button back. <<smile>>
I am working on editing my fstab right now.  I am using "gedit" because it seems to work so much easier for me. (I hope that there is nothing wrong with that!!)(like it adds some kind of extra characters or something... 
My fstab that is works looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=24c8dc38-bfee-4d72-9770-529cd27b420c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=7052817a-7103-441f-a216-6137e735c1a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/home/bill	ext3	auto,ro,user	0	0

```
I have only added the last line, but I am not finished... I have to make some more directories, and decide where I need to mount them...
Where do installed programs go when they are installed?  That would be where I need to mount the other large partitions. 
Any suggestions are still appreciated.
~1BB

---

### Post by blandman3 on 2009-03-22
sort of off the subject, but:

you wouldn't happen to know how to view shared files and folders on windows system while operating under ubuntu would ya?

---

### Post by rajan on 2009-03-22
> **1BigBore said:**
> 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=24c8dc38-bfee-4d72-9770-529cd27b420c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=7052817a-7103-441f-a216-6137e735c1a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/home/bill	ext3	auto,ro,user	0	0

```
I have only added the last line, but I am not finished... I have to make some more directories, and decide where I need to mount them...
Where do installed programs go when they are installed?  That would be where I need to mount the other large partitions. 
Any suggestions are still appreciated.
~1BB

the last line looks reasonable, but i think you want it to be pointing to your sdb3 (i think i recall that one being the "extended" type system from your earlier posts). you also of course need to make the directory "/home/bill/" if it is not there already. if that is your home directory i think you should make the fstab entry point to something else to avoid conflicts with the existing files/directories there. 

i did this about a year ago, and i'm just starting to recall how i did it. i did it with a TON of help from the great people on this forum, so i think i better pass some of those things on and pay my debt. i will look at my old threads and see if i can put together a really easy description for it, but it may be a day or two off. this type of thing is really easy if you do it correctly, and it is impossible if you screw something up so i want to make sure i'm not giving you bad advice (hence the couple of days). 

right now i have my computer set up (with 6.06) so that the second HD automatically appears on my desktop like a subfolder of the 1st HD. i'm saying this just to make sure you don't get discouraged because the final product (screenshot incl.) is really convenient and it just works. 

gedit is just as good as anything else

windows server stuff is a bit different and you probably want to do about 20 minutes of googling before you get into it. that sort of thing has to be really common on these forums.

---

### Post by 1BigBore on 2009-03-22
Thanks... Great screen shot by the way...
This is what I am planning to use...I did create these directories, and I just hope that when I try to load new programs, and "stuff" they will work.
What prompted my quest was that my DVD movie player did not work, and when I tried to load the proper drivers and so on it said my directory was full.
<shakes head>   Anyway, here is what I have finally come up with for a fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=24c8dc38-bfee-4d72-9770-529cd27b420c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=7052817a-7103-441f-a216-6137e735c1a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/home/bill/storage	ext3	auto,rw,user	0	0
/dev/sdb2	/root/storage		ext3	auto,rw,user	0	0
/dev/sdb5	/mnt			ext3	auto,rw,user	0	0
/dev/sdb6	/root			ext3	auto,rw,user	0	0

```
I am not sure about the "/mnt" and the "/root" but at least I am making progress.  Will it be usable if I mount it like that?  /dev/sdb5 and /dev/sdb6 are extended partitions within /dev/sdb3.
Will that work?

p.s.
I made the above changes and did 
sudo mount -a 
and nothing locked up.  my next step will be a reboot.  cross your proverbial fingers.

---

### Post by 1BigBore on 2009-03-22
Things seemed to work fine after a reboot.  
I will try and post a little screen shoot of what my second drive looks like now.
I think it worked,  We should mark this thread **[solved]!**
The partitions are mapped.  Are they mapped correctly?   Only time will tell.  For the moment, things are going as desired.

Thanks for all the help and encouragement.  It really helps.

---

### Post by rajan on 2009-03-22
that's great news that you have a functioning computer after a relatively involved upgrade.

as for your last few questions, you notice that the <mount point> is where the /mnt and the /root appear. that means the device in /dev/sdb6 (which is a partition of a larger device, in the ext3 format) contains all of the files in the /root directory. this is an important directory, as is your /mnt directory. 

hope your system gives you many years of reliable computing.


EDIT: by the way, i think that if you set the mount point as a directory in the /media folder, then it will pop up on your desktop automatically and you don't have to create a shortcut or whatever.

---

### Post by broozm on 2009-03-23
> **rajan said:**
> 
EDIT: by the way, i think that if you set the mount point as a directory in the /media folder, then it will pop up on your desktop automatically and you don't have to create a shortcut or whatever.

Not to hijack the post (which is great and useful as I was following along at about the same rate:)

but I was of the impression that the /media was in fact a label for any *removeable* media as in removeable USB drives etc. (as opposed to /dev  *devices*).

(AND DOES NOT cause the shortcut to the item on the desktop [and in the places browser] to appear magically)???

How did I come to this I erroneous conclusion?
Well when I plugged in two 320GB sata drives, the three partitions on each showed up as /media/WORK /media/DATA and /media/MEDIA.
(The second drive showed up with another identical set of the same (as they had been copies of eachother in my Windows lifetime! :)

To cut a long story short, I now have almost finished converting to ext3.

I will put in a screengrab to summarise

---

### Post by 1BigBore on 2009-03-23
Posting from work so I cannot see what is on my box, but If I remember right, any unmounted partition looked like a removable drive, and if I "clicked" to mount it in the 'computer'window, it became an icon on my desk top.  It was still marked as a removable drive.  Now the only drive that shows up on my desk top is the one I mounded from my "home/[username]/storage" directory.

---

### Post by rajan on 2009-03-23
yeah now that i think about it, anything that is mounted will pop up on the desktop (usb drives, cdroms, etc), although most of them are linked in the /media folder (so i might be right still). what would be interesting is to see if you locate the mount point somewhere other than the /media folder if it actually creates a link to that folder anyway. if there's no problem with your system though, it's all academic.

---

