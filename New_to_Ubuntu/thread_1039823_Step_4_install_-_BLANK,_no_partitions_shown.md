---
title: "Step 4 install - BLANK, no partitions shown"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by stolenfat on 2009-01-14
Im installing ubuntu- it's my first linux install fyi- and step four is blank!  It doesn't recognize any partitions, or show any hard disks!

The linux partition tool reads my drive and my partitions... so i dont know why the ubuntu install doesn't see them.

Can any one offer any help for me? Im clueless as to what to do.

if it makes a difference im booting up with unetbootin using an ISO cause i couldnt burn the live disc properly

thanks!

---

### Post by handydan918 on 2009-01-14
The amazing Kreskin doesn't hang here anymore, so give us some info. 
Maybe post the output of ```
sudo fdisk -l
``` for a start..

---

### Post by stolenfat on 2009-01-15
alright, i'll see what more information i can provide... but honestly, i dont know what else to add.  I know my way pretty well around windows, but this is my first attempt at linux, i'll see what happens when i try that running that command line.

---

### Post by stolenfat on 2009-01-15
alright, i ran that code, it didnt provide me with anything more than command prompts.  

Is there any other information that would be usefull? Honestly, it seems to me like a fluke, do you think it might be something i could fix in the bios?
I just dont understand why my disc partitions are noticed by the linux partition manager, but come up comepletely blank in the ubuntu installer application.

I've changed the file partition type from linux swap, ext3, nfts- and still nothing, it doesnt show anything.

---

### Post by stolenfat on 2009-01-15
my bad, i thought that 'l' was a 1.

heres the out put:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0a2c9a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         972     7801856   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         972       27665   214410408    7  HPFS/NTFS
/dev/sda3           27666       30401    21976920   83  Linux


does that help>?

---

### Post by stolenfat on 2009-01-15
i found this page through google:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/201286](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/201286)

theres a picture there which depicts the exact screen i run into while installing

---

### Post by stolenfat on 2009-01-15
after more research i find it might be a problem with my SATA drive... does ubuntu support/recognize SATA drives? are there other versions of linux or ubuntu that might?
Anything i can do?

the laptop im installing on is a vgn-nr498e SONY

i also get this error message:

no root file system is defined.

Please correct this from the partitioning menu.

but my menu is blank! bahh!

---

### Post by Vantrax on 2009-01-15
If possible remove and create partition 1 (sda1) again.

Linux should be three partitions. One should be setup as /, one as swap, and one as /home. 

The swap is like the windows page file, the /home is like your user profile, and the / is your 'c' drive.

When you actually load up you will see the home partition as a folder inside root (/)

---

### Post by Vantrax on 2009-01-15
> **stolenfat said:**
> after more research i find it might be a problem with my SATA drive... does ubuntu support/recognize SATA drives? are there other versions of linux or ubuntu that might?
Anything i can do?

Linux all use the same kernel, so its not a problem with the Linux kernel, your drive has an error in the way partition 1 is done.

When you go to install, do the disks via manual and create partitions as mentioned previously. Swap should be 1.5x to 2x your ram. Root is going to be how ever much you need for applications. 10-15g should be plenty (and you can always resize later), home should be as large as possible as its where your data is stored.

---

### Post by stolenfat on 2009-01-15
I'll try recreating my partitions using the linux partition tool, the vista one seems very limiting.  Anyways, i was hoping to install as a dual boot and not have to erase the first partition with vista on it (which would be the one with the problem)  Would you know how to remedy that problem with out erasing everything?

> When you go to install, do the disks via manual and create partitions as mentioned previously.

Thats the thing, the ubuntu install doesnt offer me any options at step 4. I don't have a choice for manual install.

I will attempt to create 3 partitions titled in that manner, i will format / and /home as ext3 and the last one as linuxswap

i'll be back with my results, thanks alot for the help so far!

---

### Post by stolenfat on 2009-01-15
alright, i made a partion 7 gigs format linuxswap titled swap
i made a 2nd partition titled /home 5 gigs formated as ext3
3rd partition titled / 15+ gigs formated as ext3

i ran the install program and still no partitions or disks were listed in step four of the install.   


would changing them to 'extended partitions' instead of primary partitions make a difference?


any clue why i can see any partitions durring the install? is it a bug? fluke?

---

### Post by Vantrax on 2009-01-16
No idea but I would not think having extended would make a big difference. 

I haven't seen that error before, possibly try the alternate CD? Ive installed on dozens of hardware types with no problems partitioning...

---

### Post by k3lt01 on 2009-01-16
Get [Gparted]("http://gparted.sourceforge.net/")

> **stolenfat said:**
> alright, i made a partion 7 gigs format linuxswap titled swap
i made a 2nd partition titled /home 5 gigs formated as ext3
3rd partition titled / 15+ gigs formated as ext3Thats just overkill to the extreme.
Try this instead, 10 gb /, 2gb SWAP (no more than that will be needed, even on my laptop which doesn't have much RAM I only use 2gb SWAP), 15gb /home.

> **stolenfat said:**
> i ran the install program and still no partitions or disks were listed in step four of the install.Try it after using GParted.

> **stolenfat said:**
> would changing them to 'extended partitions' instead of primary partitions make a difference?I don't know nor do I think thats a problem.

> **stolenfat said:**
> any clue why i can see any partitions durring the install? is it a bug? fluke?Can see? because the partition editor looks for them and shows you what you have available.

---

### Post by stolenfat on 2009-01-16
my bad, typo- i mean CANT see, it gives me no options, nothing- only offers a blank window

i am using gparted- i understand that yea 7 gigs of swap is over kill, but should that really make a difference?  whats important is that its there, i think it's formatted correctly, but the install is giving me nothing but blank.

I did try a different cd, i dl'd an amd 64 bit version and still ran into the same problem.

Step four of the install, does some sort of search (a progress bar rans something really fast) but then goes blank... this is after running Gparted.

I saw another thread in which some one encountered a similar problem, some one offered a suggestion of typing 'pci=nomsi' durring the bootup by pushing f6- but i havent been able to access any terminal while doing so.  The same guy also offered typing in 'all_generic_ide'... which i dont know what to do with- does that ring any bell with anyone?

We'll i think i might download a live cd for an earlier version and give that a shot, but running a lesser version just seems silly to me when i shouldnt have too.

---

### Post by ChaiTan on 2009-01-16
I remember having the same problem with Intrepid. It happens if you are using unetbootin or booting from iso on hdd by some other method. I was able to install using the installer as I had two HDD's, the one that didnt have the iso was detected while the other wasnt.

---

### Post by bailbath on 2009-01-16
What version of Ubuntu are you using?
I recently tried one of the Alpha downloads for the next release of Ubuntu and had the same problem.
You could try the alternate install instead of the live cd install.
You could download the last version of Ubuntu as it is well proven and is long term support.
When it gets to install you are going to have to use the manual option to re partition so you may have to get some more tips here or do some googling on Linux partitions. 
Ian

---

### Post by redseventyseven on 2009-01-16
From the original post:
> 
if it makes a difference im booting up with unetbootin using an ISO cause i couldnt burn the live disc properly

How come you're not able to burn the live disc properly? It sounds as though if you could be able to get hold of a properly burned CD then you wouldn't be running into these problems!

What sort of problems are you running into? As a last resort you can always order a CD from a company such as ship-it for a couple of dollars.

---

### Post by k3lt01 on 2009-01-16
EDIT: I just saw a possible fix on the [other thread]("http://ubuntuforums.org/showthread.php?t=1040837") mentioned below.

> **stolenfat said:**
> i am using gparted- i understand that yea 7 gigs of swap is 
over kill, but should that really make a difference?
I dunno, possibly I suppose. When Gutsy come out I had terrible trouble with SWAP size and placement. If I didn't have it at a certain spot and size nothing else would work.

> **stolenfat said:**
> I did try a different cd, i dl'd an amd 64 bit version and still ran into the same problem.What architecture is your system?

> **stolenfat said:**
> Step four of the install, does some sort of search (a progress bar rans something really fast) but then goes blank... this is after running Gparted.Gparted on the Ubuntu LiveCD or Gparted from the site I gave you a link to? If it was the one on the Ubuntu Live CD get the one from the site and use it first.

> **stolenfat said:**
> I saw another thread in which some one encountered a similar problem, some one offered a suggestion of typing 'pci=nomsi' durring the bootup by pushing f6- but i havent been able to access any terminal while doing so.  The same guy also offered typing in 'all_generic_ide'... which i dont know what to do with- does that ring any bell with anyone?There are at least 2 threads on this exact topic going right now.

> **stolenfat said:**
> We'll i think i might download a live cd for an earlier version and give that a shot, but running a lesser version just seems silly to me when i shouldnt have too.Hardy isn't a lesser version, it is more robust and has much longer support than Intrepid. Yes Intrepid is bleeding edge in some aspects but that doesn't make it better for everyone.

---

### Post by boof1988 on 2009-01-16
> **stolenfat said:**
> Im installing ubuntu- it's my first linux install fyi- and step four is blank!  It doesn't recognize any partitions, or show any hard disks!

The linux partition tool reads my drive and my partitions... so i dont know why the ubuntu install doesn't see them.

Can any one offer any help for me? Im clueless as to what to do.

if it makes a difference im booting up with unetbootin using an ISO cause i couldnt burn the live disc properly

thanks!

I had the same problem:
[INDENT]1. Use Unetbootin to put Ubuntu 8.10 LiveCD iso on HDD1
2. Partitions on HDD1 not visible for partitioning step of installation[/INDENT]

The solution I used:
[INDENT]1. Use Unetbootin to put Ubuntu 8.04.1 LiveCD iso on HDD1
2. Partitions on HDD1 are visible during partitioning step of installer[/INDENT]

The installation of Ubuntu 8.04.1 worked just fine (it seems).

I think read an existing thread about this but there weren't any answers that solved the problem.

> **ChaiTan said:**
> I remember having the same problem with Intrepid. It happens if you are using unetbootin or booting from iso on hdd by some other method. I was able to install using the installer as I had two HDD's, the one that didnt have the iso was detected while the other wasnt.

This sounds like a good solution when two HDDs are available.  I might try it if/when I want to install Ubuntu 8.10 instead of 8.04.1.

Thanks...

---

### Post by stolenfat on 2009-01-16
wow, thanks for the many replies and the help offered!

> Gparted on the Ubuntu LiveCD or Gparted from the site I gave you a link to? 

I tried to dl gparted from the site given to me but i couldnt open the program because i didnt have access, i suspect it's a problem from running off an emulated live cd via unetbootin

I also suspect that my troubles are pretty much unetbootin based, i wouldnt even use it if my burning software wasnt error'n every time i tried to burn the iso.  

> How come you're not able to burn the live disc properly? It sounds as though if you could be able to get hold of a properly burned CD then you wouldn't be running into these problems!


I tried several burning programs- they all err'd so i thought unetbootin was the best choice for myself.  Im very confused why i cant burn the iso, i've tried two different downloaded isos, at least 3 programs, no success- then i tried to burn another iso unrelated to ubuntu and was able to successfully burn just to test if it was my system.

As of now, i'm all almost done dl'n 8.04 via torrents and will unetbootin mount the iso and try the install again and see if it lists the partitions or not.


much thanks again for the help

---

### Post by stolenfat on 2009-01-16
well i was finally able to install with hardy heron (8.04) using unetbootin with no troubles at step 4.  There was one error durring the install regarding 'apex' or additional applications or something but i cant quite remember

seems all is well, i've orded a cd from the ubuntu site which may show up in the next month or not, and i will try to do a clean ibex install then and see if i get the same partition troubles

thanks for all the help offered

---

