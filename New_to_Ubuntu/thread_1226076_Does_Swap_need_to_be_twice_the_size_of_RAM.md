---
title: "Does Swap need to be twice the size of RAM?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by swarup on 2009-07-29
They say that the swap partition should be twice the size of one's RAM. And that on the other extreme, if the swap is less than the size of the RAM, then the system will not be able to go into hibernate mode. I've got 4 GB RAM. Do I really need a swap partition of size 8 GB? Will 4, 5 or 6 GB do?

---

### Post by Zenze on 2009-07-29
Swap is used when you run out of ram, like the pagefile in windows if you are familiar with that. If you have 4 GB you will probably never use swap unless you are running a crazy amount of programs at once. So no, I don't think you need to make it 8 gigs.

As far a hibernation, I don't know where it writes to.

---

### Post by Idefix82 on 2009-07-29
> **swarup said:**
> They say that the swap partition should be twice the size of one's RAM. And that on the other extreme, if the swap is less than the size of the RAM, then the system will not be able to go into hibernate mode. I've got 4 GB RAM. Do I really need a swap partition of size 8 GB? Will 4, 5 or 6 GB do?

As Zenze said, during your normal work you are unlikely to ever use SWAP at all. When you hibernate, the RAM is written to SWAP so for that you need as much SWAP as you are likely to occupy before hibernating. With 4GB of SWAP you will be on the safe side.

---

### Post by swarup on 2009-07-29
@ Zenze: I see-- so, so far as general performance is concerned, it won't make any difference if I make the swap say 5 or 6 GB instead of 8. And perhaps, since the RAM is quite large, then in order to do hibernation too, the swap won't need to be as large as 8 GB. I wonder whether that "twice the size of RAM" rule is mostly for machines with less RAM.

@ Idefix82: wow, thanks-- great info. So from what you're saying, it sounds like with 4 GB swap I won't be compromising or risking anything as far as functionality goes. Rather, 4GB swap will be ample.

---

### Post by benj1 on 2009-07-29
a 2:1 ratio swap to ram used to be recommended, it isn't realy needed now though.

the only thing you realy need swap for now is suspending to disk, if you don't use that and you have 4gb of ram you could probably do without swap, but ofcourse it depends on your usage, i have 512mb ram and hardly ever go into swap.

---

### Post by bumanie on 2009-07-29
There is no strict rule of how big swap must be the double your physical ram was a 'rule of thumb' notion that came out some way ago when ram was expensive and motherboards could only handle small amounts of ram. 2gb swap should be ample.

---

### Post by philinux on 2009-07-29
That advice comes from the era of having 256meg ram when swap really was useful.

I've got 2 gig ram and use hibernate so I made my swap partition 2 gig.

Under normal running my swap never gets used.

---

### Post by CatKiller on 2009-07-29
> **benj1 said:**
>  the only thing you realy need swap for now is suspending to ram, 

You don't need any swap for Suspend-to-RAM. That mode keeps everything in RAM and sends enough power to the RAM so that the contents stay there. The clue's in the name :)

You need swap for Hibernate (or Suspend-to-disk). The contents of the RAM are written to the swap, and then the computer is shut down. Since the data is persistent (it's on a hard drive, after all) you can turn everything off. When the computer starts it will look for an image in swap and, if it finds one, will copy that image to the RAM and start running again.

---

### Post by swarup on 2009-07-29
I see-- that's all great to know.
I've actually just bought a Mac laptop (MBP), and want to do a triple boot (OSX/Jaunty/Vista) on it. OSX comes with a second partition called EFI, leaving only two for Jaunty and Vista. I tried to create an extended partition using gparted for Ubuntu & swap, but for some reason gparted refused to create an extended partition on a Mac. So I had to go without swap, and just made Jaunty without it. It sounds from what you all say like Jaunty should run just fine. Perhaps I won't be able to suspend though? Is there a difference between suspend and hibernate with respect to the need for swap?

---

### Post by CatKiller on 2009-07-29
> **swarup said:**
> I tried to create an extended partition using gparted for Ubuntu & swap, but for some reason gparted refused to create an extended partition on a Mac.

It's possible that you could use partitioning tools in OS X to create the partitions. I have no idea how Macs do things.

It's possible to create a swap file rather than a swap partition. For the normal uses of swap it performs just as well as a swap partition. I haven't looked into how one would configure the resume to work from a swap file, but it might be possible.

---

### Post by hthury on 2009-07-29
Wow, great info, guys.

Seems like I got many wrong ideas about RAM e Swap.

I thought Swap could also increase performance, but seems only in cases when the RAM is above 100% os capacity.

---

### Post by theozzlives on 2009-07-29
I have 4 GB RAM and just followed the rule and made an 8 GB swap, but I have Ubuntu as my only OS and have the space to spare.

---

### Post by thiebaude on 2009-07-29
When I install Ubuntu I let Ubuntu adjust the swap for me based on how much Ram I have.

---

### Post by benj1 on 2009-07-29
> **CatKiller said:**
> You don't need any swap for Suspend-to-RAM. That mode keeps everything in RAM and sends enough power to the RAM so that the contents stay there. The clue's in the name :)

You need swap for Hibernate (or Suspend-to-disk). The contents of the RAM are written to the swap, and then the computer is shut down. Since the data is persistent (it's on a hard drive, after all) you can turn everything off. When the computer starts it will look for an image in swap and, if it finds one, will copy that image to the RAM and start running again.

quite right, typo, sorry

---

### Post by bear24rw on 2009-07-29
i run no swap with both my laptop (4gb ram) and desktop (6gb ram)

---

### Post by LewRockwell on 2009-07-29
> **philinux said:**
> That advice comes from the era of having 256meg ram when swap really was useful.

I've got 2 gig ram and use hibernate so I made my swap partition 2 gig.

Under normal running my swap never gets used.

this is what I do also

so if you've got 4GB ram then do a 4GB swap(it's not like you can't change it later if you decide differently)

.

---

### Post by swarup on 2009-08-02
Just to make sure I've got this right-- In Jaunty for example, when I go to the upper right corner of the screen, click the power button there and select "suspend", is that a "suspend-to-ram", or a "suspend-to-disc" ?

---

### Post by Dark Aspect on 2009-08-02
With 4GB of Ram you can probably get away with not having a swap file at all since I have 2GB or ram and I have only ever used 4% of my 1GB swap file. Though not using a swap file is unsupported I believe,

```
sudo swapoff -a
```

---

### Post by swarup on 2009-08-02
But I do want to confirm: is the "suspend" feature in Jaunty a "suspend-to-ram", or a "suspend-to-disc"? Again, here I am asking about the suspend, not the hibernate feature.

---

### Post by CatKiller on 2009-08-02
Suspend is Suspend-to-RAM. Hibernate is Suspend-to-Disk.

---

### Post by SunnyRabbiera on 2009-08-02
Well for large RAM such as 4GB you can use less swap, for smaller RAM such as under 1GB of RAM then swap needs to be more.
typically you need less Swap around 2GB of RAM, 2GB of ram does not need a Swap of 4GB you can do 2 or 3, then with 3GB of ram you can go smaller, 3GB of RAM 1GB of Swap.

---

### Post by gn2 on 2009-08-02
> **swarup said:**
> Just to make sure I've got this right-- In Jaunty for example, when I go to the upper right corner of the screen, click the power button there and select "suspend", is that a "suspend-to-ram", or a "suspend-to-disc" ?

If it says Suspend it's to RAM.
The option which writes to the hard drive is called Hibernate.

---

### Post by HotShotDJ on 2009-08-02
Several people have suggested that you may be able to eliminate swap.  That is bad advise.  Below is what I wrote in a similar thread:

The RAM X 2 is what is called a "safe harbor" method of calculating swap space. The purpose of allocating this amount is NOT for the purpose of day-to-day running of your system, but to prevent a catastrophic failure should a badly behaved application run amok on your system.

I can give you an example of this principle in a real-world situation: One of the recent Ubuntu Kernels (not available in the repositories -- I believe it was from the 2.6.30 series) OR one of the xorg-video-intel drivers (also from a PPA, not in the regular Jaunty repositories) contained a regression that caused a huge amount of swapping. If I had not set my swap partition to the admittedly over-sized default of RAM X 2, or worse, chose not to have a swap partition at all, my system would have come to a crashing halt before I was able to detect what was going on, look up the issue, and make the appropriate corrections to my system.

As others have noted, if a system has a sufficient amount of physical RAM, it is possible that the user will never experience any problems by shrinking, or even eliminating, the swap partition. Also, I have seen recommendations that RAM X 2 is only correct for systems with less than 1 Gig RAM (the type of systems we old-timers used for most of our computing life), and that for systems with 1 or more GIG, the appropriate calculation is RAM X 1.5. To me, this seems like a reasonable recommendation. In any case, the cost of mitigating the potential risk is minimal compared to the cost of having a RAM related catastrophic failure. The cost/benefit calculus seems to overwhelmingly support the use of either the RAM X 2 or at the very least, the RAM X 1.5 recommendation.

All systems that I set up have RAM X 2 swap partitions. As previously mentioned, disk space is cheap, so I can think of no reasonable argument to change to another partitioning scheme.

---

### Post by swarup on 2009-08-03
> **HotShotDJ said:**
> All systems that I set up have RAM X 2 swap partitions. As previously mentioned, disk space is cheap, so I can think of no reasonable argument to change to another partitioning scheme.

For me, it isn't an issue of disk space. Rather, it is an issue of limitations to the number of allowed partitions. I have an Apple laptop (MBP), and there one cannot create extended partitions. I am setting up a triple boot OSX-Jaunty-Vista. OSX comes with another tiny partition besides OSX, and it is not yet clear to me whether I can get rid of that. But as it stands, OSX takes up two of the allowed partitions. And that leaves two others for Jaunty and Vista. If I want swap for Jaunty, then there's no partition left for Vista. If I could create an extended partition, I'd be fine--but it can't be done on an Apple disk. So that is why I am considering setting up Jaunty without swap-- so I can accommodate Vista. And since the suspend feature in Jaunty is suspend-to-ram, and since I have 4 GB Ram, that should be plenty for all my day-to-day works, plus be able to accommodate the suspend feature which I very much want. 

That is the reason I am considering installing Jaunty without swap.

---

### Post by n8bounds on 2009-08-03
Ubuntu can use a swap FILE, working around your partitioning problem.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

just two programs needed: dd and swapon (already included) plus one extra line in your /etc/fstab file

Pretty easy

---

### Post by swarup on 2009-08-03
> **n8bounds said:**
> Ubuntu can use a swap FILE, working around your partitioning problem.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

just two programs needed: dd and swapon (already included) plus one extra line in your /etc/fstab file

Pretty easy

Wow-- sounds really great. :)

One question about it: if one does for any reason need swap for the suspend-to-ram function, then will the swap *file* be able to fulfill that need? Or does the swap file, being only a file, have to function from within Ubuntu and therefore only work when Ubuntu is up and running?

---

### Post by HotShotDJ on 2009-08-03
> **swarup said:**
> For me, it isn't an issue of disk space. Rather, it is an issue of limitations to the number of allowed partitions. I have an Apple laptopIC.  That is a problem.  Have you considered installing Jaunty, complete with a swap partition, and then using VirtualBox to run Vista?  Otherwise, perhaps the swap file mentioned by n8bounds will take care of the problem.  For many reasons, including those mentioned in my previous post, you'd be better served having swap and no Vista than no swap and having Vista. ;)

---

### Post by swarup on 2009-08-04
Yes, that would be a possibility. I've actually already installed Ubuntu, and with a sizeable swap partition. I was thinking of possibly re-installing without the swap in order to get the triple boot set up, but if I can convert the swap over to a swap-file without re-installing Ubuntu, that would be great. Or the option of doing a virtual box is also another option.

---

### Post by scrapmetal on 2009-08-04
I have always done swap 2 X ram, no problems so far.
2 different machines for IT people.
First, apple was loaded. used gparted (boot CD) to make room for Ubuntu 8.04 and XP pro. Loaded XP next, Then 8.04.
Second, XP pro (OEM) so loaded it first. Then 8.04. Finally latest 9 Ubuntu.
I keep swap twice ram in case graphic, or CAD programs required by user.
Do not know if this is the absolute correct way to do it but it works for me.
These machines are over 1,500 kilometers away from me so dropping in to help, or fix is out of the question.
Hope this helps.

---

### Post by ridetheteapot on 2009-08-04
TuxOnIce supports hibernate to file, so you can hibernate you machine with no swap partition. (or with no harddisk swap partition ...)

you could also if you really still want a swap file,but want it really fast. (i dunno why but maybe, like was posted earlier you need it for buggy kernels and drivers)
you could basicly
mkfs on /dev/ramXX
mount it mkswap it then start using it. obviously this won't help you hibernate lol.

personally i use a 1 gig swap with 4 gigs of ram.

---

### Post by aysiu on 2009-08-04
Disk space isn't cheap for those of us who have SSDs.

I have 16 GB. There's no way I'm allocating 4 GB (double my RAM) to a useless swap partition.

---

### Post by HotShotDJ on 2009-08-04
> **aysiu said:**
> Disk space isn't cheap for those of us who have SSDs.

I have 16 GB. There's no way I'm allocating 4 GB (double my RAM) to a useless swap partition.Most of the "safe harbor" type of recommendations assume the availability of sufficient HDD space, and certainly would not apply to your situation.  When one has certain hardware limitations, one must make compromises and assume some risks.  The very same cost/benefit calculus that tells us that RAM X 2 is a reasonable recommendation for swap on most systems ALSO leads to the conclusion that it is an unreasonable recommendation on a system with only a 16 GB SSD at a very high cost per GB.

(Newer SSD's are quite a bit larger than that, but still very expensive. On the Pangolin Performance laptop, [System76]("http://www.system76.com") offers an 80 GB SSD upgrade for $250 and a 160 GB SSD upgrade for $495.  For comparison, their 500 GB 7200 RPM SATA II hard drive upgrade is $99)

But I must protest your calling swap "useless."  The laptop that I use has 2G physical RAM and it would have come to a very undignified, crashing halt if I didn't have that "useless swap partition" (see my first post to this thread, [#23]("http://ubuntuforums.org/showpost.php?p=7721877&postcount=23")).  I COULD, however, be persuaded that RAM X 1.5 is the better calculation for systems with 2G RAM or more.

---

### Post by wizard10000 on 2009-08-04
> **HotShotDJ said:**
> ...I can give you an example of this principle in a real-world situation: One of the recent Ubuntu Kernels (not available in the repositories -- I believe it was from the 2.6.30 series) OR one of the xorg-video-intel drivers (also from a PPA, not in the regular Jaunty repositories) contained a regression that caused a huge amount of swapping. If I had not set my swap partition to the admittedly over-sized default of RAM X 2, or worse, chose not to have a swap partition at all, my system would have come to a crashing halt before I was able to detect what was going on, look up the issue, and make the appropriate corrections to my system.

Although I agree in principle the bottom line is you weren't running a production OS or video driver.  Disk space *is* cheap but the example you mention would have been caught way before either the kernel or the video driver made it into production  ;)

IM frequently less than HO the correct amount of swap is determined by your requirements.  The trick is to have enough swap space to do what you need to do - and on this machine (3.5GHz i7 920, 6GB RAM used for video rendering,  web surfing and not much else) swap use has been zero since I built the machine - even when stress-testing the machine with eight threads of folding@ home or rendering video.  I use a 2GB swap partition just in case but since my stuff is processor-intensive as opposed to memory-intensive and I since don't hibernate the system 2GB is plenty for me.

If I was running on the bleeding edge then I agree completely that you need a buffer but truth be told if you'd been out for coffee when your machine decided to act up even 2x ram wouldn't have been enough  :)

Same is true with Windows.  Although MS used to recommend 2x then 1.5x RAM and since Windows doesn't hibernate to swap the right answer depends on what the machine's used for - and Windows comes with plenty of tools to monitor pagefile use.  On a 4GB Windows machine I normally let Windows manage PF use for awhile and monitor it until I get a baseline then set a static pagefile about 50% bigger than max PF use.

So my general rule of thumb for Linux is if you hibernate the system you need a swap partition equal to RAM size unless your applications demand more.  If you don't hibernate then you can track how much swap you use, add a bit for a buffer and set your swap partition that way.

Easiest way to monitor swap use in Linux?  Glad you asked  ;)

I use a cron job that runs 'swapon -s'every 5 minutes and dumps the results to a text file like this -

```
# log swap usage
*/5 * * * * root swapon -s >> /var/log/swap-use.log 2>&1
```

and the output looks like this.  You could do it more often than every five minutes if you wanted. It'd be handy to add system time but this works for me - and once I get a baseline I just comment out the cron job.

```
Filename				Type		Size	Used	Priority
/dev/sda2                               partition	2000084	0	-1
Filename				Type		Size	Used	Priority
/dev/sda2                               partition	2000084	0	-1
```

Hope this helps -

---

### Post by HotShotDJ on 2009-08-04
> **wizard10000 said:**
> Although I agree in principle the bottom line is you weren't running a production OS or video driver.  Disk space *is* cheap but the example you mention would have been caught way before either the kernel or the video driver made it into production  ;)You are sort of correct.  Although I was running a production OS, I was not using the production kernel and I was not using the production video driver... but thats just picking at nits... I get your point. :)  In a perfect world, kernels, drivers, or for that matter, any software that makes it into a production system should function properly.  But bugs -- and sometimes very serious bugs -- inevitably make it through to final release.  That is just the nature of the beast.

Having said that, I really don't disagree with anything you said, and am particularly intrigued by your method of determining your swap-space needs by use of a cron job and log files.  Very ingenious!  Although, other than as an interesting academic exercise, I honestly don't see any real world advantage unless:
[LIST=1]
[*]one is very low on disk space and needs to squeeze every last kilobyte out of what they have (and even then, the better recommendation is to get a larger harddrive).
[*]one is concerned that that the standard recommendation is not sufficient for their needs and would like to more accurately determine a larger swap size for their needs.
[/LIST]
In any case, I was describing a "safe harbor" method of calculating one's swap partition.  In other words, one that will work with most systems for most people under most circumstances.  Unless a person has severe space limitations (such as aysiu's system) or other very specialized needs, there is absolutely no harm in having a large swap partition.  System performance does not suffer from having too much swap space.  But the opposite is certainly NOT true. 

When things are going right and software is not misbehaving (and on a stable, production system, hopefully this is all the time), any swap space you allocate will rarely, if ever, be used other than for hibernation.  The RAM X 2 (or RAM X 1.5) "Safe Harbor" method, however, will provide that safety net that one hopes will never be needed.

---

### Post by wizard10000 on 2009-08-04
> **HotShotDJ said:**
> ...When things are going right and software is not misbehaving (and on a stable, production system, hopefully this is all the time), any swap space you allocate will rarely, if ever, be used other than for hibernation.  The RAM X 2 (or RAM X 1.5) "Safe Harbor" method, however, will provide that safety net that one hopes will never be needed.

Yup.  If one's got the disk space it certainly won't hurt anything and as you mention it can help.

---

### Post by Paddy Landau on 2009-08-04
Looking at the manual for swapon, it seems that you can specify more than one swap file, and furthermore prioritise them. This indicates to me that perhaps you can use a USB flash drive as a swap partition (like Windows Ready Boost). Would that be right?

@swarup: You can't make an extended partition: Have you called Apple Support to find out whether there is a way to create an extended partition? It would seem a strange omission from a company that normally creates quality products.

BTW, I have 1Gb RAM, and my machine does use the swap partition, but only a little -- I don't think I've ever seen it exceed 100Mb.

---

### Post by wizard10000 on 2009-08-04
> **Paddy Landau said:**
> Looking at the manual for swapon, it seems that you can specify more than one swap file, and furthermore prioritise them. This indicates to me that perhaps you can use a USB flash drive as a swap partition (like Windows Ready Boost). Would that be right?

It'd be right but it wouldn't be efficient - a modern hard drive talks a heck of a lot faster than a USB port does.  If you've got the disk space it's still better to have swap on a hard drive.

I normally put swap as close to the outside edge of the disk platter as I can since throughput is faster on the outside edge of a drive.  If I've got more than one drive in the machine I put the swap partition on a different spindle than the OS.

---

### Post by HotShotDJ on 2009-08-04
> **wizard10000 said:**
> I normally put swap as close to the outside edge of the disk platter as I can since throughput is faster on the outside edge of a drive.I just wonder... while throughput is faster on the outside edge (careful -- make sure you're not spanning platters), on average, the head will have to travel further to get to the outside edge when it needs to read/write to the swap-file.  I suspect that placing the swap partition beginning somewhere near the half-way point would give better real-world performance, although I doubt that the difference would be noticeable. (I'm just guessing... I have no evidence upon which to base a genuine opinion.)

But who am I to talk, I used Gentoo Linux for years so that I could squeeze the last millisecond of performance out of my system.  Nowadays, I can't be bothered. ;)

---

### Post by Paddy Landau on 2009-08-04
> **wizard10000 said:**
> ... throughput is faster on the outside edge of a drive.
Now I'm really confused.

I thought that a single spin, whether you were on the inside or out, stored the same amount of data, meaning that throughput would be identical. All that changed (so I believed) would be the space between bits, not the time taken to read or write.

---

### Post by wizard10000 on 2009-08-04
> **HotShotDJ said:**
> I just wonder... while throughput is faster on the outside edge (careful -- make sure you're not spanning platters), on average, the head will have to travel further to get to the outside edge when it needs to read/write to the swap-file.  I suspect that placing the swap partition beginning somewhere near the half-way point would give better real-world performance, although I doubt that the difference would be noticeable. (I'm just guessing... I have no evidence upon which to base a genuine opinion.)

But who am I to talk, I used Gentoo Linux for years so that I could squeeze the last millisecond of performance out of my system.  Nowadays, I can't be bothered. ;)

Yeah, I'm getting too old for this stuff too  ;)

Partitions *always* span platters because they're set on cylinder boundaries.  The only exception is with Vista, since MS decided they could partition drives on 1mb boundaries instead of cylinder boundaries, which is why a buncha utilities choked on resized Vista partitions at first.

I *think* that putting swap on the outside edge of the platter would make up for the difference in seek time but I don't know for sure.

I *do* know that on a Winders machine I used to experiment with that stuff when RAM still cost $40 a megabyte and just for the heck of it I created a custom NTFS partition with 4k clusters (remembering that an ia-32 data page is also 4k), put it on the outside edge of a different spindle than the OS and did get a tiny performance boost over the same swapfile with default 512k clusters.

But then, I can be an idiot sometimes too.  I'm probably the only person on the planet who's ever put a Windows swapfile on a ramdrive.  Made plenty of sense when I thought up the idea  :D

---

