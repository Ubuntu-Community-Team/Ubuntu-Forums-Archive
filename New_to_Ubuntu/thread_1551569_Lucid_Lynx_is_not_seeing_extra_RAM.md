---
title: "Lucid Lynx is not seeing extra RAM"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by boron on 2010-08-12
I recently fitted two extra IGB ram Simms in my desktop but System/Administrator/System monitor does not seem to be seeing this.  I thought Linux 64 bit (which is the version I'm using), automatically detected and made us of much more RAM than Windows 7 can use.
Is there anyway I can make use of the extra RAM I have fitted using some utility or command?
If anything, my system seems to run more slowly since fitting the extra RAM:(

---

### Post by QIII on 2010-08-12
Virtually all 64 bit OSes can address 16 exabytes of RAM, depending on what your motherboard is capable of.  That's a huge number.  You'd buy that by the truckload from BestBuy.

So:

What is the maximum your motherboard allows?

Does your motherboard require "symmetrical" amounts of RAM across all the sockets?

How much memory did you have before and how much do you have now?

How much do you have in each socket?

Did you bump one of the other modules loose while installing the new memory?

How much memory is being detected?

Are you sure you are using a 64 bit distro?

---

### Post by ajgreeny on 2010-08-12
What does ```
free -m
``` show, and what do you think it should show?  Does POST and/or your BIOS show the memory as installed?

---

### Post by QIII on 2010-08-12
Also --

I see from another post that at one time you had a Wubi install.

Is that still how you are set up?  I don't know if that would have any effect.

---

### Post by boron on 2010-08-13
> **QIII said:**
> Virtually all 64 bit OSes can address 16 exabytes of RAM, depending on what your motherboard is capable of.  That's a huge number.  You'd buy that by the truckload from BestBuy.

So:

What is the maximum your motherboard allows? Answer 4x sockets with 2GB in each, total 8gb Max, I have 1GB in each

Does your motherboard require "symmetrical" amounts of RAM across all the sockets? the user manual says: For dual-channel memory configuration (2), you may:
•	 install identical DIMMs in all four sockets OR
•	 install an identical DIMM pair in DIMM_A1 and DIMM_B1 (yellow
	
sockets) and another identical DIMM pair in DIMM_A2 and
	
DIMM_B2 (black sockets) I have identical Dimms in A1 & B1 and identical [but different from A1& B1] in A2 and B2


How much memory did you have before and how much do you have now?  Igb in A1 and B1 so 2Gb total. I added a matching pair into A2 & B2. It's possible that the Ram I added is a different speed than the original - invoice says it is PC2-5300 Unbuff. Not sure of speed of original RAM, could be faster, possibly?

How much do you have in each socket? 1GB in each. (i.e A1, B1, A2 & B2

Did you bump one of the other modules loose while installing the new memory?  I don't think so. They are all a very tight fitand hooked in with clamps.

How much memory is being detected?999.6 Mib (IGB in old money?)

Are you sure you are using a 64 bit distro?according to sysinfo, GCC version is 4.4.3 (x86_64-linux-gnu)  I believe that confirms it as 64 bit?  I'm a newbie as far as the technicalities are concerned.  Thanks.

---

### Post by boron on 2010-08-13
> **QIII said:**
> Also --

I see from another post that at one time you had a Wubi install.

Is that still how you are set up?  I don't know if that would have any effect.

Yes: I originally tried Ubuntu with Wubi, but ran out of disk space, so did a fresh install on a separate hard disk which I am now using, having discarded Windows.  So I don't think that is the issue, in this case, but a worthwhile pointer, so thanks.:)

---

### Post by Rubi1200 on 2010-08-13
Applications > Accessories > Terminal

copy and paste this:

```
cat /proc/meminfo
```

Will hopefully give you a better view of what is what.

---

### Post by boron on 2010-08-13
> **ajgreeny said:**
> What does ```
free -m
``` show, and what do you think it should show?  Does POST and/or your BIOS show the memory as installed?

Hi, thanks for reply, I get:
Mem   total   used   free   shared   buffers   cached   
            999     989    10          0       7      216
I think it should show total of 4000 when Virtual box is not running (as some memory - 50% recommended, has to be assigned to it).
Don't know how to discover if memory is installed in my AMI BIOS  will now check the flash screen on boot up to see if it is displayed.  Hmm, very fast, but I saw it said "single channel DRAM clocking 667Mhz" from memory. So I think you've hit on the problem. How to get it into "dual channel mode"?  Thanks again

---

### Post by boron on 2010-08-13
> **Rubi1200 said:**
> Applications > Accessories > Terminal

copy and paste this:

```
cat /proc/meminfo
```

Will hopefully give you a better view of what is what.
Thanks for all the help ful clues. . .
result of cat:-
john@john-desktop:~$ cat /proc/meminfo
MemTotal:        1023600 kB
MemFree:           10100 kB
Buffers:           18900 kB
Cached:           249228 kB
SwapCached:          652 kB
Active:           436880 kB
Inactive:         415500 kB
Active(anon):     294252 kB
Inactive(anon):   294504 kB
Active(file):     142628 kB
Inactive(file):   120996 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       5960072 kB
SwapFree:        5938764 kB
Dirty:                36 kB
Writeback:             0 kB
AnonPages:        583772 kB
Mapped:           146148 kB
Shmem:              4508 kB
Slab:              42292 kB
SReclaimable:      19248 kB
SUnreclaim:        23044 kB
KernelStack:        4032 kB
PageTables:        31992 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6471872 kB
Committed_AS:    1769840 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      326224 kB
VmallocChunk:   34359403348 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      186112 kB
DirectMap2M:      862208 kB

But I think the problem is that the POST shows machine is in single channel mode, so I need to discover how to get it into dual channel mode, I guess.

---

### Post by Paqman on 2010-08-13
> **boron said:**
> 
But I think the problem is that the POST shows machine is in single channel mode, so I need to discover how to get it into dual channel mode, I guess.

Make sure that you've got identical sticks in the matched slots. Most boards have the slots for the channels colour-coded so that you get it right.

---

### Post by ajgreeny on 2010-08-13
Only one GB approximately is showing in both **free -m** and the **cat /proc/meminfo** so something is definitely wrong in your system hardware somewhere or other.

---

### Post by eriktheblu on 2010-08-13
OS won't matter if your machine does not recognize it. On your next boot, go into your BIOS and see if you can find how much memory is detected. See if any of the memory ports are disabled. If you find any deficiencies there, it might be an installation issue, or a BIOS malfunction (may be addressed by updating BIOS).

---

### Post by boron on 2010-08-13
> **Paqman said:**
> Make sure that you've got identical sticks in the matched slots. Most boards have the slots for the channels colour-coded so that you get it right.
Thanks,paqman,
My eyesight is not very good, and the print on the SIMMs is very small, so I just trusted I'd been supplied with the correct items, which looked the same physical size and fitted the 240 pin slots.
I read at [http://www.terminally-incoherent.com/blog/2006/10/04/how-much-memory-do-i-have/](http://www.terminally-incoherent.com/blog/2006/10/04/how-much-memory-do-i-have/)
 that if I typed 

lshw -C memory

in the terminal window, that it would report " exactly what kind of dimms are in your system". . . great! [if true. . .]
Here's what I got:
desktop:~$ lshw -C memory
WARNING: you should run this program as super-user.
  *-memory:0              
       description: System memory
       physical id: 3
       size: 999MiB
  *-memory:1 UNCLAIMED
       description: RAM memory
       product: MCP61 Memory Controller
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:00:00.0
       version: a1
       width: 32 bits
       clock: 66MHz (15.2ns)
       capabilities: bus_master cap_list
       configuration: latency=0
  *-memory:2 UNCLAIMED
       description: RAM memory
       product: MCP61 Memory Controller
       vendor: nVidia Corporation
       physical id: 1.2
       bus info: pci@0000:00:01.2
       version: a2
       width: 32 bits
       clock: 66MHz (15.2ns)
       configuration: latency=0
But I'm none the wiser.
 Does it throw any light on the matter to anyone, out there? Thanks.  We'll get there, somehow, with help from the Ubuntu community.

---

### Post by Paqman on 2010-08-14
> **boron said:**
> Thanks,paqman,
My eyesight is not very good, and the print on the SIMMs is very small, so I just trusted I'd been supplied with the correct items, which looked the same physical size and fitted the 240 pin slots.


You might want to get someone with better eyesight to check the model numbers on the sticks and Google it to make sure they're the same spec. There's a lot more to it than just the size. RAM comes in all sorts of flavours.

---

### Post by JBAlaska on 2010-08-14
Post your MainBoard model and the specs on your memory chips please.

---

