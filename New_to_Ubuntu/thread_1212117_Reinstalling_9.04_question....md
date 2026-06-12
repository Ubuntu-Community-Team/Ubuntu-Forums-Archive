---
title: "Reinstalling 9.04 question..."
date: 2009-07-13
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-13
I have been trying to work with my less than perfect 9.04 install and am now to the point that i am going to do a reinstall from the live dvd...

my skill level is not quite novice...

with the reading i have been doing i am to the point where i want to do the re install hopefully the right way this time...

i have 4 mem and a 320 hdd...

my objective is to try my best to avoid windows so at this point i want to only install 9.04...




**i would like input on the following questions if possible...**

1. am i understanding what i am reading by thinking i will need a root, home, and swap partition ???

2. will root and home need to be set up as ext 3 partitions ???

3. is the swap partition necessary ???

4. i would like the hibernation option when the install is finished...

5. am i forgetting/missing anything ???

6. can i get suggestions as to the size of these partitions ???



thanks in advance...

---

### Post by halitech on 2009-07-13
assuming you mean 4gig of memory and you don't use suspend or hibernate, you don't techincally need to have a swap space but I still make one with 3gigs of ram.

answers:
1. see above

2 ext3 or ext4, your choice

3. see above

4. then you will need a swap partition at least as large as your ram

5. not that I can think of

6. / around 10 gig (mine is 27gig and I'm using 3.7gig) swap 1.5times the amount of ram should be safe /home whatever is left

---

### Post by airtonix on 2009-07-13
1. no, but it is a good idea...since further re-installs will only require you to re-format the root partition and you can leave all your /home files alone.

2. yes

3. yes

4. hibernation involves dumping the contents of your ram to hardrive, so you need to make sure that your swap drive is large enough to contain the entirity of the ram.

5. maybe backup your current home files etc

6. /swap : 4.5gb /root : 15gb /home : rest of the drive ( remember /var/apt/cache is where all your deb packages initially are stored when using synaptics or apt-get, so the size of your root partition needs to have this taken into consideration )

---

### Post by Mornedhel on 2009-07-13
> **NOTAGEEK said:**
> 1. am i understanding what i am reading by thinking i will need a root, home, and swap partition ???

You can skip the /home partition if you don't intend to do fancy stuff like sharing your /home between distributions (dangerous). The merits of having a separate /home partitions exist, but are debatable.

> **NOTAGEEK said:**
> 2. will root and home need to be set up as ext 3 partitions ???

ext3, ext4... pretty much anything except vfat and ntfs. ext3 is the current standard, ext4 is more bleeding edge.

> **NOTAGEEK said:**
> 3. is the swap partition necessary ???

Yes, if you want to be able to hibernate, or if you have little memory (4 mem is a dimensionless quantity, unless "mem" is a new unit of measure -- assuming you have 4 GB, you need swap for hibernation only).

> **NOTAGEEK said:**
> 4. i would like the hibernation option when the install is finished...

See above. Hibernation and suspend don't always work perfectly due to hardware issues.

> **NOTAGEEK said:**
> 5. am i forgetting/missing anything ???

Not that I can think of.

> **NOTAGEEK said:**
> 6. can i get suggestions as to the size of these partitions ???

2x(RAM amount) for swap used to be recommended ; nowadays 1.5xRAM should be enough. Around 10 GB for / and the system should be more than comfortable. The rest to /home.

---

### Post by Elfy on 2009-07-13
1 - you don't need a /home partition, it can make it easier if you are likely ot need to reinstall. I did to start with now I find it better to have seperate partitions for data.

2 - not necessarily - I use ext4 now, there have been reports of problems with that but I have not had any. Ext3 is the default.

3 & 4 - swap partition needs to be at least the same as RAM to get hibernate

5 - possibly, but it seems to be all you need to know at the moment ;)

6 - swap 4Gb
    /    10Gb
    /home remainder of disk

Have fun :)

---

### Post by ajgreeny on 2009-07-13
I agree with what everybody above has said in general, but would suggest that you forget about ext4 at the moment.  There have been reports of problems with it as forestpixie says.  A few users have lost all the data in files in directories that had been written to during the session when freezes or crashes occurred, not what you want to happen. The files were still there in theory, but were all 0 bytes, ie empty.  The few times I have had freezes with ubuntu, there have never been any signs of anything wrong when restarting, no file loss or corruption,and not even a forced fsck has taken place as a result.

Stick with ext3 for now and see what happens with karmic in October.

---

### Post by NOTAGEEK on 2009-07-13
I appreciate all the input and b4 i start the re install i have just 1 more question...



is the only reason to have swap to get the hibernate feature ???

if thats the only reason rather than complicate things i think ill pass on the swap partition just to keep things simple...

input ???

thanks...

---

### Post by halitech on 2009-07-13
some people have said they have run their systems with no swap at all with over 2 gigs of ram but I've noticed on my own machine that occasionally things will go to swap ever with the 2gigs that I have so I always set up a swap partition but thats me and if you arent going to use hibernate then I guess its up to you.

---

### Post by jerome1232 on 2009-07-13
You do need to have a swap partition (well it's possible to make a swapfile similiar to how Windows does it but that's another subject), it's the equivalent of a windows page file, data in ram that is not being accessed will often be placed in swap to make room in ram for more file cache or application data.

I'd like to echo forestpixie's #1 point I prefer to make a separate partition just for data and leave /home on the root partition. Actually now I use a whole separate external disk for my data since I'm on a laptop with limited internal hard disk space.

---

### Post by DaGrimReefah on 2009-07-13
Swap isn't just for hibernation; I'd suggest at least half of your ram (2 gigs) just to be safe.

---

### Post by NOTAGEEK on 2009-07-13
ok so i am on the right page this is the way i think i will set the partitions...

swap=6gigs
/=20gigs
/home=rest of drive

with 4 gigs of mem and a 320 hdd does this sound reasonable ???

with a swap partition i assume it will also be set up as a primary partition ???

it should be set up at beginning just like the / and /home partitions ???

also ste as an ext3 partition ???

mount will be /swap ???

when partitions are set up does it matter what order they are set up in as in 1st part swap 2nd part / and 3rd part /home for example ???

thanks again for the help and time...

---

### Post by Elfy on 2009-07-13
Swap is it's own filetype but it needs no mount point.

I would only have the saem as RAM for swap 6GB is overkill.

You can set all 3 as primary partitions if you want to.

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> ok so i am on the right page this is the way i think i will set the partitions...

swap=6gigs
/=20gigs
/home=rest of drive

with 4 gigs of mem and a 320 hdd does this sound reasonable ???

with a swap partition i assume it will also be set up as a primary partition ???

it should be set up at beginning just like the / and /home partitions ???

also ste as an ext3 partition ???

mount will be /swap ???

when partitions are set up does it matter what order they are set up in as in 1st part swap 2nd part / and 3rd part /home for example ???

thanks again for the help and time...

opinions are like holes, everybody's got a few...

what the heck...I'll chase some electrons around the interwebs as well...

***you do not want a 290GB /home partition***

************************************************************

Your machine on my tech bench:

Parted Magic LiveCD goes in

boot

gparted

first primary partition 20GB(might be for windoze someday...otherwise other *nix distros will play around here)

second primary partition will be swap at 1xMAXRAM so if your system max is 4GB then the swap will be 4GB(here we are planning ahead on the assumption that this drive won't be "adjusted" for the life of the system even if more ram is added)

third primary partiton 20GB(main *nix distro will live here)

remaining unallocated space will all be an extended partition and within that partition you can play around with logical partitions and use them however you desire

apply and enjoy!

I want to note here that proper thoughtful partitioning, attempting to think ahead and plan for contingencies...will work best

as always, your mileage may vary

.

---

### Post by NOTAGEEK on 2009-07-13
THREad solved... i am 99% sure...:guitar:

---

### Post by xx58 on 2009-07-13
I have 8.10 in my computer only. Now I want make clean installation with Ubuntu 9.04 and use file system Ext4. I do everything and when I want to go forward then have message:'' Please correct this from the partitioning menu." No root file system is defined. I need help!
I am new at Ubuntu, because I need detailed instruction, how do installed Ext4 at moment when I will put CD in and start installation. First coming language and that not problem. Then coming Partition and I go where is advance AND at that point I have problem and cannot understand nothing....  I don't want to install ext3..... Can anybody help. who did it already?

---

### Post by Bartender on 2009-07-13
xx58 -
I installed 9.04 twice, to two different systems, in the last week.  Used ext4 both times.  No problems.

If you have easy access to broadband you might want to download the latest stable version of gparted, wipe the drive clean, then format the entire drive as ext4, then start over again with your installation.

I've seen that "no root file" error message before.  I was always able to clear it up by wiping the drive clean and leaving it unformatted, and/or setting a compatible file structure.

---

