---
title: "Swap partitian"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Diametric on 2009-12-14
I've been browsing a few threads here and was wondering if someone could explain the swap partition thang in Linux.  I understand it's used to free up memory...how so?  Is it used only for both dual boot and just solo Linux installs?  
 
Thank you,
-Diametric

---

### Post by JC Cheloven on 2009-12-14
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
;-)

---

### Post by wojox on 2009-12-14
Swap space is the area on a hard disk which temporarily holds memory pages that are inactive. Swap space is used when physical memory, or RAM, is full. If the system happens to need more memory resources or space and the physical memory is currently full, inactive pages are then moved to the swap space. Note that the access time for swap is slower therefore do not consider it to be a complete replacement for the physical memory. Swap space can be a dedicated swap partition (recommended), a swap file, or a combination of swap partitions and swap files.

[SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by audiomick on 2009-12-14
searching swap in the ubuntu documentation yields this:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by jbrown96 on 2009-12-14
Computers, historically, have had less ram than they tend to need. Operating systems (all of them, but they differ in how they do it) create swap "areas". These are used the same way as ram, but are much slower, since it's stored on the hard drive. OSes don't like to use swap because it's so slow, so it ends up being a last resort if the system runs out of ram. There are two designs for swap: a file and a paritition. 

Windows uses a swap file. There are benefits and downsides. The best reason to use a swap file is that you don't have to statically allocate it. If the system needs a lot of swap for some reason, then the file can grow in size. The downside is that it has overhead since it's stored on the file system. File systems store lots of extra info called "metadata" this includes the last time the file was accessed, who owns it, etc. You don't really need this info with swap, but everything on the file system has to have it, so it's a little slower.

Linux uses a parition. This has benefits and downsides. Ram is volatile, meaning that once the computer is turned off, all the data is lost. There's no use trying to preserve this data. A swap partition is faster than a file. However, since it is a partition, the size is fixed, so you are always losing some disk space for swap that is hardly every used. 

I think swap is a huge waste of space. I have used linux on systems with various amounts of ram, and I have never needed swap. It just doesn't get used. I never create a swap partition. If you have >=1GB of ram, then you probably don't need it either, unless you plan to hibernate the computer (suspend doesn't need swap). If you want hibernate, then swap needs to be a little bigger (maybe 1.25x) the size of your ram, since all your ram gets saved to swap during hibernation. 

Hope that helps.

---

### Post by Diametric on 2009-12-14
Great reply, jbrown.  Well, I only have 512mb of ram on the laptop running Ubuntu, however, I don't run a lot of ram intensive processes, so I prolly won't create one.  Plus, forfeting 1-2gb of HD when I only have a 30gb of free space doesn't seem prudent.  As to the speed, would the lack of speed utilized in a Linux partition swap be further reduced if allocated on an external HD?  Again, thanks for your reply.

---

### Post by jbrown96 on 2009-12-14
Generally external storage is slower, but it depends on your specific hardware.

Swap can be thought of as "emergency" ram. Basically, it would only ever be used to stop the computer from crashing from an "out of memory" error*. The memory allocator in linux is smart, so this practically never happens. 

If I were you, I wouldn't create a swap partition, even with 512MB of ram. If you do have problems, then it's always possible to create a swap file in linux, although it won't be as smart as Windows swap (won't grow and shrink as needed), but at least you can easily remove it/add additional swaps. 

I wouldn't ever recommend dedicating 2-4x your ram as swap, but you may find that 300MB or so might be worthwhile. Again, just test it out. Open up a bunch of programs and see if you have problems. I seriously doubt you ever would, but performance may suffer.

There are a couple categories of data that is stored in ram. There is stuff that is in actual use (i.e. the programs you are currently running and files you have open). This data can't be removed or else the programs won't work. The other type is cache, which is data that was either recently used or (if you use something like preload) is anticipated to be used in the future. If you open a program (say Firefox), then close it and open it again, you will notice that it opens faster and doesn't use the hard drive as much. This is because Linux is like "hey Firefox has closed, but nothing currently needs the memory that it was using, so I'll keep it there, maybe Diametric wants to use it again." This works great if you use it again because it's already in memory. Let's say you open some other programs (that aren't already cached) and you start running low on memory, then linux is like, "goodbye firefox. I'll have to load you from the hard drive next time because I'm low on memory and I need it for apps that are currently running." This is really good behavior, but you have to recognize the difference between the two. If you use the "system monitor" it is smart enough to only report the ram that is actually being used, but if you use command line tools like "free" it reports what's actually being used + cache, so it seems like you are really low on ram. That's not the case because Linux will delete the cache if necessary, so it's not really "in use."

Glad to help.

*Not exactly true. Linux will use swap before it's completely out of ram, but greatly prefers real ram to swap. There are instructions on how to set the swap preference in the swap FAQs that other users posted.

---

### Post by ramjet_1953 on 2009-12-14
If you want to use suspend and hibernate functions, then you will need a swapfile, regardless of how much RAM you have.

Regards,
Roger :)

---

### Post by The_Pirate_King on 2009-12-14
> **ramjet_1953 said:**
> If you want to use suspend and hibernate functions, then you will need a swapfile, regardless of how much RAM you have.

Regards,
Roger :)
Not exactly; swap is only for the Hibernate function. 
Suspend actually "maintains" your physical memory, which causes it to use slightly more power than hibernate, which writes RAM to disc and turns the computer off completely. 

But it usually takes longer to start up from hibernation; almost as much a full boot-up. 


So if you are worried about power [if you've got a laptop on battery power] I recommend hibernate, but if you're plugged in, suspend is a better option because it does not require swap and you can resume your session much more quickly. 

The windows equivalents of Ubuntu's "Hibernate" and "Suspend" are "Hibernate" and "Sleep" respectively...

---

### Post by jbrown96 on 2009-12-15
> **The_Pirate_King said:**
> Not exactly; swap is only for the Hibernate function. 
Suspend actually "maintains" your physical memory, which causes it to use slightly more power than hibernate, which writes RAM to disc and turns the computer off completely. 

But it usually takes longer to start up from hibernation; almost as much a full boot-up. 


So if you are worried about power [if you've got a laptop on battery power] I recommend hibernate, but if you're plugged in, suspend is a better option because it does not require swap and you can resume your session much more quickly. 

The windows equivalents of Ubuntu's "Hibernate" and "Suspend" are "Hibernate" and "Sleep" respectively...

The amount of power depends on your hardware platform and how well it implements ACPI. I have a Thinkpad that can stay in suspend for weeks without going dead; my girlfriend's HP can only last about 5 hours in suspend before it dies. 

I've never seen the point of hibernate because it isn't any faster than shutdown and reboot.

---

### Post by JC Cheloven on 2009-12-15
> **jbrown96 said:**
> I've never seen the point of hibernate because it isn't any faster than shutdown and reboot.

In present days, jaunty or karmic with ext4 boot in a breeze, true. Hibernation has not much sense. But remember, it wasn't the same quite a long ago.

---

