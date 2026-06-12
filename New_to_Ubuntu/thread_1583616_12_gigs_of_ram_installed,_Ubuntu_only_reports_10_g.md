---
title: "12 gigs of ram installed, Ubuntu only reports 10 gigs."
date: 2010-09-28
forum: New to Ubuntu
---

### Post by o0kojiro0o on 2010-09-28
Just installed Ubuntu on my primary pc to give it a try on good hardware (only used it on laptops and metbooks previously). Had a huge issue getting my monitors to display properly, and now I have a new issue. I got the 64bit version installed and it seems to be running fine, but I noticed it's only addessing 10 of the 12 gigs of memory I have installed. Windows addresses this memory without any trouble and I've done burn-in, stress testing, and memory testing to confirm it is stable with all 12 gigs addressed. Is there some limitation in memory or some configuration i need to change in order for Ubuntu to see this ram or is there some other issue going on. Any help is appreciated. Thanks!

free -m output:

> 
             total       used       free     shared    buffers     cached
Mem:         10015       1121       8893          0         27        272
-/+ buffers/cache:        821       9193
Swap:         6234          0       6234





---

### Post by mastablasta on 2010-09-28
firstly you really didn't give any information on your system appart from saying you chucked in 12 GB of ram. so how can anyone help you?
**Suggestions on how to get your support questions answered as quickly as possible**:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
secondly have you checked your motherboard specifications? i know they have limits. i have one that can only take max 384MB ram, one that can take 2GB max and one that can take 8 GB max.
 
Linux itslef can handle 256GB ram i believe.
 
out of curiousity what programme you run requires so much RAM?

---

### Post by renkinjutsu on 2010-09-28
> **mastablasta said:**
> firstly you really didn't give any information on your system appart from saying you chucked in 12 GB of ram. so how can anyone help you?
**Suggestions on how to get your support questions answered as quickly as possible**:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
secondly have you checked your motherboard specifications? i know they have limits. i have one that can only take max 384MB ram, one that can take 2GB max and one that can take 8 GB max.
 
Linux itslef can handle 256GB ram i believe.
 
out of curiousity what programme you run requires so much RAM?

He has already confirmed that other operating systems are recognizing the extra ram.

Also, I have no idea why your system isn't recognizing the 2 extra gigabytes of ram.. I'm not really sure what you can do, but it seems like something in /etc/sysctl or perhaps a kernel boot parameter? Someone get an expert in here!

---

### Post by jtarin on 2010-09-28
Run this command and post.```
cat /proc/cpuinfo | grep flags
```

---

### Post by Perfect Storm on 2010-09-28
Do you have onboard videocard with shared memory?

---

### Post by khelben1979 on 2010-09-28
What version of Ubuntu do you have installed? Also, if it's a bug in the Linux kernel, report back the kernel version.

It could also be interesting to know what brand it's on the RAM sticks which is installed. Just because they work good with Windows does not exclude that the Linux kernel won't reject something.

---

### Post by beew on 2010-09-28
Is it 10 G or 10Gi?

---

### Post by jwbrase on 2010-09-28
> **beew said:**
> Is it 10 G or 10Gi?

I already ran the math on that. 12 G would be about 11 Gi. 10 Gi would be about 11 G, so it's probably not that (at least, not exclusively).

Ubuntu would be reporting Gi, so if the memory was marketed in G, it could explain about half of what he's missing.

---

### Post by cascade9 on 2010-09-28
> **jwbrase said:**
> I already ran the math on that. 12 G would be about 11 Gi. 10 Gi would be about 11 G, so it's probably not that (at least, not exclusively).

Ubuntu would be reporting Gi, so if the memory was marketed in G, it could explain about half of what he's missing.

Well, RAM is sold in binary MB/GB (which they renamed GiB *censored due to CoC* and therefore if you have a '2GB' stick of RAM it will be reported as '2GiB').

The 'missing' 2GB is nothing to do with binary/decimal shenanigans.

---

### Post by jwbrase on 2010-09-28
> **cascade9 said:**
> Well, RAM is sold in binary MB/GB (which they renamed GiB *censored due to CoC* and therefore if you have a '2GB' stick of RAM it will be reported as '2GiB').

The 'missing' 2GB is nothing to do with binary/decimal shenanigans.

I've seen it sold in decimal GB. Our desktop was sold with "4 GB" of memory, and Ubuntu reports it as having 3.75 GiB, which comes out to almost exactly 4 decimal GB.

But, as I said, binary/decimal crud can only account for about half of the missing memory.

---

### Post by cascade9 on 2010-09-28
> **jwbrase said:**
> I've seen it sold in decimal GB. Our desktop was sold with "4 GB" of memory, and Ubuntu reports it as having 3.75 GiB, which comes out to almost exactly 4 decimal GB.

But, as I said, binary/decimal crud can only account for about half of the missing memory.

I've never, ever seen memory sold in decimal GB. I dont think its even possible. 

Your 3.75GiB issue could be from shared memory, or from the 3.something limit of 32bit (assuming that you dont have a PAE kernel or 64bit version installed) or something else I havent even thought of.

---

### Post by migs73 on 2010-09-28
> **cascade9 said:**
> Well, RAM is sold in binary MB/GB (which they renamed GiB *censored due to CoC* and therefore if you have a '2GB' stick of RAM it will be reported as '2GiB').

The 'missing' 2GB is nothing to do with binary/decimal shenanigans.

GB is the SI prefix for Gigabyte 10 to the power 9 (decimal) and GiB is the IEC Binary prefix for 2 to the power 30. If the RAM is sold as GB (which most are, and HDD's) then it is 12GB or approx 11.17GiB. To do otherwise would be a breach of sales description laws.

---

### Post by cascade9 on 2010-09-28
> **migs73 said:**
> GB is the SI prefix for Gigabyte 10 to the power 9 (decimal) and GiB is the IEC Binary prefix for 2 to the power 30. If the RAM is sold as GB (which most are, and HDD's) then it is 12GB or approx 11.17GiB. To do otherwise would be a breach of sales description laws.

RAM is sold as 'real' GB (1,073,741,824bytes = 1GB) and HDDs, flash drives, etc sold as 'decimal' GB (1,000,000,000 bytes = 1GB). 

JEDEC (who control memory standards) defines a GB as 1024x1024x1024 bytes (1073741824 bytes). If you really want to check that, you can go here,  register an account, and d/l the white paper- 

[http://www.jedec.org/standards-documents/results/JESD100B01](http://www.jedec.org/standards-documents/results/JESD100B01) 
 
I really hate this GB/GiB junk. It doesnt make any sense anyway, 'decimal'? LMAO. 8 bits to the byte, if it was really decimal they should have fixed that, making 1GB ('true' decimal) bigger than the current GB (no matter if you mean GiB or GB). 

1,000,000,000 x 8 = 8,000,000,000
1,073,741,824 x 8 = 8,589,934,592

So a true, decimal, GB should actually be 10,000,000,000 bytes, and that means that the 'decimal' GB is about 80% of the size it should be, and even a GiB is a bit over 85% of the size it should be.......

---

### Post by CharlesA on 2010-09-28
That GiB/GB garbage gets annoying at times, but I've only seen it on HDDs and the like. For memory, I've always seem it go off of the "normal" GB value.

@OP: If you boot off a memtest86+ cd, does it show all 12GB as detected?

---

### Post by migs73 on 2010-09-28
> **cascade9 said:**
> RAM is sold as 'real' GB (1,073,741,824bytes = 1GB) and HDDs, flash drives, etc sold as 'decimal' GB (1,000,000,000 bytes = 1GB). 

JEDEC (who control memory standards) defines a GB as 1024x1024x1024 bytes (1073741824 bytes). If you really want to check that, you can go here,  register an account, and d/l the white paper- 

[http://www.jedec.org/standards-documents/results/JESD100B01](http://www.jedec.org/standards-documents/results/JESD100B01) 
 
I really hate this GB/GiB junk. It doesnt make any sense anyway, 'decimal'? LMAO. 8 bits to the byte, if it was really decimal they should have fixed that, making 1GB ('true' decimal) bigger than the current GB (no matter if you mean GiB or GB). 

1,000,000,000 x 8 = 8,000,000,000
1,073,741,824 x 8 = 8,589,934,592

So a true, decimal, GB should actually be 10,000,000,000 bytes, and that means that the 'decimal' GB is about 80% of the size it should be, and even a GiB is a bit over 85% of the size it should be.......

Just when I think I've got my head round it, another spanner in the works :confused:
That document even seems to contradict itself later in the explanation of Megabytes when it shows a table of the IEC MiB and SI MB as it understood by me, but states they (JEDEC) will use MB to mean MiB?
Somebody somewhere has got to get ALL these guys in a room and bang their heads together till they get a true Standard. What is the point in having two different measuring systems for memory (HDD's and RAM) in one piece of equipment (PC's)? Although at one time it made as little difference at did not matter, as we grow closer to the realms of PC's with massive SSD's (100+ GB) what system do they use? They are surely large banks of RAM accessed as HDD's.

BTW here is what my system reports for 4GB/GiB???
```
             total       used       free     shared    buffers     cached
Mem:          3889        616       3272          0         62        277
-/+ buffers/cache:        276       3612
Swap:         5553          0       5553

```
Not really near 4GB either?

---

### Post by CharlesA on 2010-09-28
> **migs73 said:**
> BTW here is what my system reports for 4GB/GiB???
```
             total       used       free     shared    buffers     cached
Mem:          3889        616       3272          0         62        277
-/+ buffers/cache:        276       3612
Swap:         5553          0       5553

```
Not really near 4GB either?

If you've got onboard video that would account for the discrepancy.

Mine is fine:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       3907       2073          0         70       3492
-/+ buffers/cache:        344       5637
Swap:        12401          0      12401
```

I've got 6GB of RAM.

---

### Post by migs73 on 2010-09-28
Why doesn't the onboard Video appear on the Used column and the total show the actual RAM? Is memtest and/or BIOS the only place to see actual total RAM? (I think I just answered my first question, BIOS assigns the Video RAM so therefore OS only sees what is left?). Can the OS not determine how much RAM is being used for the Video? Could the OP's systems BIOS be assigning some of the RAM for other processes?

---

### Post by CharlesA on 2010-09-28
> **migs73 said:**
> Why doesn't the onboard Video appear on the Used column and the total show the actual RAM? Is memtest and/or BIOS the only place to see actual total RAM? (I think I just answered my first question, BIOS assigns the Video RAM so therefore OS only sees what is left?). Can the OS not determine how much RAM is being used for the Video? Could the OP's systems BIOS be assigning some of the RAM for other processes?

The BIOS will usually show the entire memory then minus the stuff being used for video, normally.

The OS only sees what is left.

Having 2GB dedicated to video would be.. crazy. @OP: Does Windows list 12GB of "usable memory" ?

---

### Post by roddie on 2010-09-28
Just curious, what can you use 12 gigs or RAM for?!

---

### Post by CharlesA on 2010-09-28
> **roddie said:**
> Just curious, what can you use 12 gigs or RAM for?!
I can't speak for the OP, but I'm using 6GB for running VMs.

---

### Post by Calash on 2010-09-28
> **roddie said:**
> Just curious, what can you use 12 gigs or RAM for?!

Virtual computers, at least that is what we use one of our systems with 12 gig for.  It runs 5 virtual systems with 2gig of memory for the server and 1gig for each host.

---

### Post by migs73 on 2010-09-28
> **CharlesA said:**
> The BIOS will usually show the entire memory then minus the stuff being used for video, normally.

The OS only sees what is left.

Having 2GB dedicated to video would be.. crazy. @OP: Does Windows list 12GB of "usable memory" ?

I specifically said 'other processes' because I knew 2Gb for video was unlikely, but other RAM can be left unusable by address conflicts with PCI stuff. What I don't know is how much can be left unusable by this problem.
I have also been led to believe (from other forums) that windows reports the RAM as seen by BIOS and not what is usable (they never used to but they got fed up with people wondering where all their RAM had gone, sound familiar??).

---

### Post by CharlesA on 2010-09-28
> **migs73 said:**
> I specifically said 'other processes' because I knew 2Gb for video was unlikely, but other RAM can be left unusable by address conflicts with PCI stuff. What I don't know is how much can be left unusable by this problem.
I have also been led to believe (from other forums) that windows reports the RAM as seen by BIOS and not what is usable (they never used to but they got fed up with people wondering where all their RAM had gone, sound familiar??).

The message that Windows shows is similar to the one [here]("http://www.overclock.net/windows/503769-windows-7-usable-memory.html"). It can appear due to chipset limitations (ION with 4GB of ram will only seem 3.5GB, even on 64 bit.), using onboard video and the like.

Is that what Windows is saying?

All my Win7 machines show the full amount of memory, but I've got a dedicated card in most of them, sans netbook.

---

### Post by migs73 on 2010-09-28
CharlesA,
I believe it was more due to people putting 3.5GB+ in their machine running 32bit software and wondering where it all went (usually reporting about 2.7GB) so they used the BIOS value instead to stop the confusion (what confusion:confused:) even if there was only 2.7GB available to the OS. I think it was Vista (I love Vista, it's why I switched to Ubuntu:))that they did this with, and seeing the link you sent (Win7), that is a much less confusing (what confusion:confused:) way to report RAM, giving both amount installed and the amount available for use.

Now is that in GB or GiB? :confused:

---

### Post by CharlesA on 2010-09-28
It's in GB.

---

### Post by o0kojiro0o on 2010-09-30
Sorry for the late reply, my classes have really robbed me of my time. Anyway, I found out that it was in fact my motherboard. Windows reported the ram as 12Gigs, and after a couple reboots it started reporting 10 as well. After fiddling with my settings a bit I discovered my ram refused to run at it's advertised speed. After some more research, I discovered that high-speed ram advertisements are a bit of a sham, and its preconfigured values don't always work as intended. I'm running at about 2/3s of the speed advertised at the moment and I don't really have much time to fiddle with it to get it working right at the moment. Good news is, Ubuntu sees all the ram now and it's working quite well =)

---

### Post by migs73 on 2010-09-30
> **o0kojiro0o said:**
> Sorry for the late reply, my classes have really robbed my of my time.
Isn't that a pain! ;)
I am glad you got your RAM problem sorted (well kind of).

---

