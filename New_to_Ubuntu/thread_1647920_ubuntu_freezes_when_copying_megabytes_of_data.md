---
title: "ubuntu freezes when copying megabytes of data"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by EntropyReduction on 2010-12-18
Apologies for reposting here (I originally posted this a few days ago  "Hardware & Laptops": on reading subtitle of that forum, probably wrong).  I'm a ubuntu newbie.

Just installed 10.10 on an acer aspire 5101AWLMi with a replacement Seagate 320gb Momentus 7200.4 HD.

Install went flawlessly. I added a few partitions, one meant primarily for data to be shared, eventually, with a win VirtualBox install, and across LAN to a couple of win machines.

Installing all sorts of software via ubuntu software centre, no problems, or none that a bit of googling couldn't solve.

To get started, began copying data from a memory stick to this partition; went ok for a while, then Ubuntu froze solid; no input recognised, no way out (that I know of) except forcing a power off and rebooting. This happened repeatedly. Proportion of time the partition was hosed, had to reformat it.

I tried an NTFS format, then FAT, then EXT4; all the same result.

No predictable amount of data transferred before a freeze; sometimes a few hundred MB, sometimes much less.

I was beginning to think &quot;hardware problem&quot;; but a response to a query on a sort-of-similar problem suggested dropping back to a previous kernel version (I had updated from 2.6.35-22 to 2.6.35-23 immediately after install). So I booted from 2.6.35-22 (after a bit of messing about with


sudo update-initramfs -u -k 2.6.35-22-generic

(What's that about? Nevermind, it worked).

Presto. Problem gone.

So: is that a bug? Did I do something wrong? If not, should a report a bug on kernel 2.6.35-23?

Now wildly impressed with silent magic that somehow means I can browse my ext4 partition from a win machine on LAN.

Many thanks for any help.



Alan C

---

### Post by Wtower on 2010-12-18
Have you tried to do a memtest for a start?

---

### Post by EntropyReduction on 2010-12-20
> **Wtower said:**
> Have you tried to do a memtest for a start?

I just did (sorry for delay).  Memtest launched from boot menu eports no problems.

---

### Post by EntropyReduction on 2011-01-04
Sorry to repeat myself, but should I report this as a bug?  Laptop has operated flawlessly running  2.6.35-22; I don't know any better but a lockup when copying data that happens reliably in a later version of kernel but not in an earlier one smells a bit buggy.

I now have substantial amounts of data on my partitions and don't really want to risk trashing them in  2.6.35-23; OTOH sooner or later I probably will need to update to the next kernel version.  

Thanks for any feedback.

Alan

---

### Post by Wtower on 2011-01-04
Hi Alan,

Is this only going on when copying data? Hasn't a freeze occured at any other circumstance? There are many reports on Ubuntu random freezes and many times it is about the graphics adapter. Nevertheless I really doubt that this be a kernel bug, I would think that there would be more reports as such. Still, of course you could report a bug anyway.

It is my understanding based on personal experience (I have not researched this thoroughly and have not confirmed it), Linux uses as much ram as possible for caching, which I believe Windows don't do in such scale. When performing large copies, it possibly caches large data on memory. That's when ram faults occur that they don't in windows.

That's the reason why I asked you to perform a memtest. I had similar issues in the past, and two resemble your description. One was about low memory faults at the 2nd slot that I solved with increasing the ram voltage from bios. The other was a crappy motherboard (asus p5p77 or something) that still has got terrible issues with memory compatibility.

I hope somebody else could help on this.

Regards

---

### Post by EntropyReduction on 2011-01-04
> **Wtower said:**
> 
Is this only going on when copying data? 


Yup

> **Wtower said:**
> 
Hasn't a freeze occured at any other circumstance? 


No, only happens when copying largish amounts of data in  2.6.35-23 

> **Wtower said:**
> 

There are many reports on Ubuntu random freezes and many times it is about the graphics adapter. Nevertheless I really  doubt that this be a kernel bug, I would think that there would be more reports as such. 



Yeah, only way I can imagine it could be kernelish was if there was something unique about hardware I'm using th somehow irritated 2.6.35-23 more than 2.6.35-22.

> **Wtower said:**
> 
 
Still, of course you could report a bug anyway.



Seems a bit silly unless I have something more concrete to report.

I'm wondering if / hoping there's some sort of setting that could throttle back..memory cacheing in file ops?   Just blundering around in the dark...

> **Wtower said:**
> 
 
It is my understanding based on personal experience (I have not researched this thoroughly and have not confirmed it), Linux uses as much ram as possible for caching, which I believe Windows don't do in such scale. When performing large copies, it possibly caches large data on memory. That's when ram faults occur that they don't in windows.

That's the reason why I asked you to perform a memtest. I had similar issues in the past, and two resemble your description. One was about low memory faults at the 2nd slot that I solved with increasing the ram voltage from bios. The other was a crappy motherboard (asus p5p77 or something) that still has got terrible issues with memory compatibility.



I'll see if I can find other ways to test memory aside from the boot-time memory test,
or go back to that and see if I can do more exhaustive tests.


> **Wtower said:**
> 
 
I hope somebody else could help on this.



Thanks in any case for your feedback.

---

### Post by kurru on 2011-01-15
Hello All,

I have a notebook ASUS A9RP which shows the very same issue. All the kernels above 2.6.35-22 replicate the failure mode. Freezing during HDD activity (eg. copy files).

2.6.35-22 is just fine.

---

### Post by bikodog on 2011-01-15
are you using nautilus to do the copying, or the command line?

I had issues in the past using nautilus to copy large files. I was using the GUI being fresh from the windows world :(


The solution led me to using the command line. now I use the command line for everything! It's much more flexible and efficient.

---

### Post by kurru on 2011-01-15
Thanks for your reply.

The way I copy has no affect to the result. Both Nautilus and command line copying freeze the computer (Ubuntu 10.10).

---

### Post by cipherboy_loc on 2011-01-15
What did you use to do the copy from the command line? Have you tried rsync? I have used it to copy >=75GB to a local NAS, when cp failed.


Cipherboy

---

### Post by Wtower on 2011-01-15
Sure, rsync is good, but I don't think using the standard cp command would hung up the machine. Something is wrong here, and I would think some hardware issue more likely.

---

### Post by kurru on 2011-01-15
I use cp command to copy. I think file handling is a very base process of an OS and should not work incorrectly.

It would not be a surprise for me if this fail occured due to some hardware/kernel conflict. My notebook (A9RP) is not a new type. However depressing.

---

### Post by Wtower on 2011-01-18
I am really curious about this issue. The only way I found to replicate it was by lowering the voltage of RAM in bios (8gig here with pae), enough so that memtest gave me 1 or 2 errors in the upper memory after about an hour test. Then I booted and logged in without apparent problems. The system came to a sudden halt only once at random, but to no surprise I believe since the memory usage on idle is really low. But I didn't manage to complete a copy of a really big bunch of video files from any disk to any disk, as soon as the RAM cache went up to 100% the pc got stuck dead.

But with the correct bios settings on this machine or on other machines the copy was completed as expected. Surely there may be plenty other reasons for which this freeze occurs, but when it comes to file copy I truly believe there is something wrong with RAM and I would recommend extensive memtest.

Now if someone wonders why this never or nearly never happens with windows, I would urge him to try to full up ram in other ways and see. File copying in windows does not bring the cache up afaik.

---

### Post by kurru on 2011-01-19
Thanks for your help.

I am just wondering why just appeared with the kernel versions above 2.6.35-22?
So, that is not Windows but Linux I use/used without any problem. New kernels are sensitive of RAM failures and a bit older kernels are not?
Hopefully this now is just a bad dream :-)

I will try 2.6.36 once stable version is available.

---

### Post by Wtower on 2011-01-19
I am not sure if it is about the kernel version or the configuration during compilation for each distribution/version. If indeed this does not happen with older kernels, then probably they do not utilise ram cache the same way, but that's just a guess. Can't look into that much detail for the moment (my free time is limited).

---

### Post by Wtower on 2011-01-19
---

---

### Post by Splat_NJ on 2011-01-19
I've not had any copying or moving problems, large or small data amounts, on any of my Ubuntu machines. I've had Ubuntu running on all three machines for about 2 months now, with my desktop being the longest. I doubt it's a memory issue. Running Memtest, as I believe he did, would uncover that. I wonder if the OP's filesystem got fubarred. The only time I had a problem with disks was when I was messing with my partitions. After successive create/deletes of partitions my disk became locked. I couldn't create or delete any partitions and had to reinstall Ubuntu, creating the partitions during install.

---

### Post by 3rdalbum on 2011-01-19
> **Splat_NJ said:**
> I doubt it's a memory issue. Running Memtest, as I believe he did, would uncover that.

Not necessarily. My computer had a bad RAM stick, same symptoms as the OP, Memtest passed. The computer consistantly froze during the Phoronix Test Suite's memory benchmarking test. Now that the bad RAM is gone, the computer works fine.

Also, more recently I saw problems with Ubuntu crashing; even the live CD freezing up during boot or not installing. Memtest passed, but removing one of the RAM sticks fixed the problem.

---

### Post by Splat_NJ on 2011-01-20
> **3rdalbum said:**
> Not necessarily. My computer had a bad RAM stick, same symptoms as the OP, Memtest passed. The computer consistantly froze during the Phoronix Test Suite's memory benchmarking test. Now that the bad RAM is gone, the computer works fine.


If you go only one or two passes with Memtest, that's not usually enough. FWIW, Prime95 is another good one. I've never used Phoronix TS.

---

### Post by Wtower on 2011-01-20
@Splat_NJ

Fyi, earlier I managed to get the pc stuck during a copy op having lowered the voltage of ram, without memtest complaining about it up to pass 14. Here is a quote from their web page [http://shsc.info/Memtest86](http://shsc.info/Memtest86)

> 
**If memtest86+ shows no errors does that mean my memory is not defective?**

Of course no answers are definitive, no matter how good memtest86+ will  eventually become there is always the possibility that a particular type  of error will go unnoticed. As long as you are having no problems with  the system it will be pretty safe to say that the modules are good. If  you are having problems with the system however you will just have to  check by trial and error, IE; swapping the modules for new ones and/or  testing with modules of a different brand/type.


---

### Post by Splat_NJ on 2011-01-20
> **Wtower said:**
> Fyi, earlier I managed to get the pc stuck during a copy op having lowered the voltage of ram, without memtest complaining about it up to pass 14. Here is a quote from their web page [http://shsc.info/Memtest86](http://shsc.info/Memtest86)
  
I believe you. FWIW, I've seen Memtest crash, reboot back up (if disk is still in drive) and obviously then showing no errors.

---

### Post by Wtower on 2011-01-21
Just had a little chat with a hardware maniac friend of mine. Just to clear things out, of course RAM voltage is only one out of countless factors for memory faults that can come immediately to my mind. Now, if someone experiences things like that, a good slow temporary solution is to try to lower ram frequency to eg 667mhz.

---

### Post by EntropyReduction on 2011-01-25
> **kurru said:**
> Hello All,

I have a notebook ASUS A9RP which shows the very same issue. All the kernels above 2.6.35-22 replicate the failure mode. Freezing during HDD activity (eg. copy files).

2.6.35-22 is just fine.

Okay, thanks, I'll consider dropping back to 2.6.35-22 .  I'd have to tinker with VirtualBox, whose drives seem to depend on eact kernel version.  Also trying to get a handle on exactly where the problem is.  I've ruled out X-freeze (can't ssh into machines once frozen).  Temperature monitors tell me I'm not overheating.   I've run into comment that suggests acpi may be the culprit, so trying to boot without it (so far without success).

---

### Post by EntropyReduction on 2011-01-25
> **bikodog said:**
> are you using nautilus to do the copying, or the command line?

I had issues in the past using nautilus to copy large files. I was using the GUI being fresh from the windows world :(


The solution led me to using the command line. now I use the command line for everything! It's much more flexible and efficient.

Problems are

(a)  Although biggish copys with nautilus are a pretty good way to (sometimes) get a freeze, I get infrequent lockups in other circumstances; occasionaly during a big install (most recently of some eclipse modules); once just when screensaver was running and nothing else; once when I launched firefox.

(b) Things I'd imagine might cause a freeze, don't. I can watch DVDs til I'm blue n the face (??), and use a slightly jerky google earth, no problem.

Also, the kernel-dependency thing has me flummoxed.

But yes, I must be a Good Boy and do more stuff with command lne.  Drag and drop dies hard.

---

### Post by EntropyReduction on 2011-01-25
> **Splat_NJ said:**
> If you go only one or two passes with Memtest, that's not usually enough. FWIW, Prime95 is another good one. I've never used Phoronix TS.

I ran memtest overnight  No problems found.  I'll try Prime95, or Phoronix Test Suite if I can figure out how to use it.

Thanks for suggestions.  This laptop has rather small amount of memory anyway (free tells me 873k), so probably worth upgrading anyway, bad memory or not.

---

### Post by EntropyReduction on 2011-01-26
> **Wtower said:**
> Just had a little chat with a hardware maniac friend of mine. Just to clear things out, of course RAM voltage is only one out of countless factors for memory faults that can come immediately to my mind. Now, if someone experiences things like that, a good slow temporary solution is to try to lower ram frequency to eg 667mhz.

Another thing that might have made a differnce: I replaced a faulty 5400 rpm hard disk with a Seagate 320gb Momentus 7200.4 ; any chance laptop might not be able to deal with a faster hard disk and somehow that's causing problems?

Even if it does, doesn't explain why less trouble on earlier versions of kernel...

---

### Post by Wtower on 2011-01-26
> **EntropyReduction said:**
> Another thing that might have made a differnce: I replaced a faulty 5400 rpm hard disk with a Seagate 320gb Momentus 7200.4 ; any chance laptop might not be able to deal with a faster hard disk and somehow that's causing problems?

Even if it does, doesn't explain why less trouble on earlier versions of kernel...

There is a possibility. I remember having disk problems with an asus motherboard for which series they kept releasing bios updates about several chipset issues that were affecting, well, pretty much anything that seemed irrelevant at the time.

About the kernel versions, as I said earlier, an explanation could be (don't really know I say) that older Ubuntu releases had different kernel compilation configuration with different memory caching, thus been more sensitive to a memory fault.

---

### Post by Splat_NJ on 2011-01-26
A failing drive, as well as a PSU, can definitely be a cause for your problems. What I don't understand is lowering your voltages (speed) to your memory. If you trust that, then that's your business. I would rather get it straightened out then to take a chance that all computations are correct.

---

### Post by Wtower on 2011-01-26
> **Splat_NJ said:**
> A failing drive, as well as a PSU, can definitely be a cause for your problems. What I don't understand is lowering your voltages (speed) to your memory. If you trust that, then that's your business. I would rather get it straightened out then to take a chance that all computations are correct.

Just to clear things out. I do NOT recommend to play around with ram voltage and definitely I have not suggested that ram voltage is a solution, if you read carefully. I simply described how I had set up my testing environment so that to make my ram behave badly, since finding faulty ram sticks is apparently not a matter of choice. On the other hand, ram frequency has got nothing to do with voltages, I simply suggest that lower ram frequencies tend to be more robust as a rule of thumb.

---

### Post by EntropyReduction on 2011-01-27
> **Splat_NJ said:**
> A failing drive, as well as a PSU, can definitely be a cause for your problems. What I don't understand is lowering your voltages (speed) to your memory. If you trust that, then that's your business. I would rather get it straightened out then to take a chance that all computations are correct.

I haven't a clue how to tinker with laptop voltages; option not in BIOS.  Think I'll leave that alone.

Sorry if I didn't  make myself clear re drive.  The current drive is a 7200 rpm, brand new, and seems to be okay.  I replaced a 5400 rpm one that died (never used with ubuntu, it was a Vista machine back then).  I wondered if the disk controller might have got itself in a state trying to keep up with the faster drive.

That said, I dropped back to kernel 2.6.35-22 after suggestions that was more reliable, and it seems to be; so far no problems at all.

OTOH some updates came in in the last few days with arcane names like "kernel firmware", so for all I know there's been some fix and even 2.6.35-24 will be okay now.  I'll go back up there and see.  Be a shame to be permanently stuck on 2.6.35-22.

---

### Post by kurru on 2011-01-27
I now performed a little test of the RAM's.

There are 2 slots and x2 512M memory moduls from different vendors in my laptop.

Test: Copied 1.5 Gigabyte twice.

Tried each RAM module one by one in both slots with kernel 2.6.35-24. - PASSED

Tried both RAM modules together both way using the slots with kernel 2.6.35-24. - FAILED

So, this is most probably a hardware issue of handling these two RAM's and the newer kernels are sensitive against it.

---

### Post by EntropyReduction on 2011-02-17
I've reported this as a regression bug in all post 2.6.35-22  kernels.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/719446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/719446)

---

### Post by kurru on 2011-02-18
Nice, thanks!

---

### Post by EntropyReduction on 2011-02-25
It was suggested in thread resulting from my bug report that I try the latest kernel build, reached from

[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

which led to 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")

I tried it: seemed improved, in that I had to try quite hard to get a freeze during a Nautilus copy, and haven;t yet managed to get a freeze while copying in a terminal with cp -r

If anyone wants to have a go, be interesting to hear results.  You'll want to back off the bleeding-edge kernel for normal work; be sure you know how to set grub to boot from an earlier kernel by default.

Also usual caveats: a bleeding-edge kernel could do 'orrible things.

---

### Post by kurru on 2011-03-01
Hello Mate,

I also use edge kernel repository: [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) maverick, which may have a few delay to the one that you installed.

My latest update was: 2.6.35-27. I tested this version but no success. I also tried different RAM/SWAP with swappiness. However swappiness=0 seemed to solve the issue Ubuntu freezed after approx. 2G of copying. So, this had not any effect neither.

It is a bit wierd that 2.6.38 is the real edge kernel version and only a 2.6.35 is available from Ubuntu repository!

I might do a try... - come back with the results soon.

Regards,

---

### Post by kurru on 2011-03-01
I also have good results with edge kernel you suggested. No freeze so far.

---

### Post by pjasnos on 2011-03-07
Hi Kurru,

Is your processor single-core by any chance?

---

### Post by kurru on 2011-03-12
Hi Pjasnos,

Yes, it is an Intel(R) Celeron(R) M CPU 420 @ 1.60GHz, and single core.
My computer is a notebook ASUS A9RP.

Regards,

---

### Post by EntropyReduction on 2011-04-04
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/719446]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/719446") still going.

Problem almost certainly appears only with single-core processors.

Natty kernel appears to not have the bug.  

Stay tuned  to [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/719446]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/719446")

---

### Post by kurru on 2011-04-24
Thanks for your efforts.

---

### Post by kurru on 2011-05-07
I installed Natty, with kernel version 2.6.38-8. It still has the problem. Seems, the stable kernel versions always do the freezing issue. Maybe this is a feature? :-)

Will update to the 2.6.39-999.

---

