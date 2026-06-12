---
title: "no swap no suspend?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by holyskeleton on 2009-04-21
I didn't set swap space since I have 4 gigs of ram but does ubuntu require swap space in order to suspend and hibernate properly? I tried both and none of them work, just gives me a black screen and nothing happens and I'd have to force shutdown the computer and restart.

---

### Post by Ericyzfr1 on 2009-04-21
> **holyskeleton said:**
> I didn't set swap space since I have 4 gigs of ram but does ubuntu require swap space in order to suspend and hibernate properly? I tried both and none of them work, just gives me a black screen and nothing happens and I'd have to force shutdown the computer and restart.

Unless you have a HD with limited space, you should allocate at least 2GB of swap. Hibernate is written to swap, it is correct.

---

### Post by holyskeleton on 2009-04-21
isn't suspend stored in memory though? that doesn't work either.

---

### Post by Paqman on 2009-04-21
> **Ericyzfr1 said:**
> Unless you have a HD with limited space, you should allocate at least 2GB of swap. Hibernate is written to swap, it is correct.

To Hibernate swap needs to equal RAM, since RAM is stored in swap when you hibernate. 2GB is a bit excessive if you don't need to hibernate. Even 1GB would go unused almost all the time.

No idea why suspend doesn't work without it though. It may just be that your mobo has a funny ACPI implementation and won't suspend. Try search for that model of mobo on here and Google and see if people have been having trouble with it.

Either way, adding a swap partition to an existing system isn't difficult if you want to try it.

---

### Post by presence1960 on 2009-04-21
> **Paqman said:**
> To Hibernate swap needs to equal RAM, since RAM is stored in swap when you hibernate. 2GB is a bit excessive if you don't need to hibernate. Even 1GB would go unused almost all the time.

No idea why suspend doesn't work without it though. It may just be that your mobo has a funny ACPI implementation and won't suspend. Try search for that model of mobo on here and Google and see if people have been having trouble with it.

Either way, adding a swap partition to an existing system isn't difficult if you want to try it.

I thought it was my mobo when in Hardy , Intrepid & Mint suspend and hibernate wouldn't work. When I went to Jaunty, I kept all my partitions intact including swap, just installed over the / partition and suspend & hibernate work perfectly now. Go figure! I am glad they now work.

---

### Post by holyskeleton on 2009-04-21
> **Paqman said:**
> Either way, adding a swap partition to an existing system isn't difficult if you want to try it.

How do I add swap space on root partition?

---

### Post by Paqman on 2009-04-21
> **holyskeleton said:**
> How do I add swap space on root partition?

Well, that would be a swap file, rather than a swap partition. I can't help you with that, as i've never done it but there's a [Howto available]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0").

To add a swap partition just create a new partition formatted as swap. Take a note of what the partition number is, eg: /dev/sda4. Then:

```

sudo mkswap /dev/<partition number>
sudo swapon /dev/<partition number>

```

Then open your filesystem table with:
```

sudo nano /etc/fstab

```

And add this line at the bottom:

```

/dev/<partition number> none   swap   sw   0   0

```

---

### Post by Penguin Guy on 2009-04-21
> **holyskeleton said:**
> How do I add swap space on root partition?
I am confused about what you mean when you say 'root partition'.

---

### Post by holyskeleton on 2009-04-21
From SwapFaq:
How much swap do I need?
If you have n MB of RAM, you need between n and 2*n MB of swap.
If you have a disk big enough, just put 2*n MB swap.

so if I have 4 gigs of RAM then I'll need 8 gigs of swap?

---

### Post by holyskeleton on 2009-04-21
> **Penguin Guy said:**
> I am confused about what you mean when you say 'root partition'.

my laptop has 240 GB HD space which is 120x2 and I put / on one and /home on the other. isn't / called root or something like that?

---

### Post by Paqman on 2009-04-21
> **holyskeleton said:**
> 
so if I have 4 gigs of RAM then I'll need 8 gigs of swap?

Nope. Rules like the one above don't really work for modern systems with tons of RAM. My rule of thumb for swap:

[list]
[*]swap = RAM if hibernation is required
[*]Otherwise swap = 1GB
[/list]

---

### Post by Paqman on 2009-04-21
> **holyskeleton said:**
> my laptop has 240 GB HD space which is 120x2 and I put / on one and /home on the other. isn't / called root or something like that?

Indeed it is.

Normally people put their swap space in it's own partition. It's possible to put swap in a file located on your root partition, but as I mention above, i've not done it.

---

### Post by holyskeleton on 2009-04-22
ok i added the swap file from the how to and it shows a gig of swap file:

owner@owner-laptop:~$ cat /proc/meminfo
MemTotal:      4054484 kB
MemFree:       3293712 kB
Buffers:         19664 kB
Cached:         259512 kB
SwapCached:          0 kB
Active:         461000 kB
Inactive:       176456 kB
SwapTotal:     1048568 kB
SwapFree:      1048568 kB
Dirty:             192 kB
Writeback:           0 kB
AnonPages:      358388 kB
Mapped:          79056 kB
Slab:            46620 kB
SReclaimable:    21900 kB
SUnreclaim:      24720 kB
PageTables:      13776 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   3075808 kB
Committed_AS:   599444 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    313280 kB
VmallocChunk: 34359424507 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     54080 kB
DirectMap2M:   4139008 kB
owner@owner-laptop:~$

but it's still not resuming from suspend. It's still doing that black screen with running hard drives thing. also i've noticed some other users are experiencing the same problem so i don't think it's a swap problem anymore.

---

### Post by presence1960 on 2009-04-22
> **holyskeleton said:**
> ok i added the swap file from the how to and it shows a gig of swap file:

owner@owner-laptop:~$ cat /proc/meminfo
MemTotal:      4054484 kB
MemFree:       3293712 kB
Buffers:         19664 kB
Cached:         259512 kB
SwapCached:          0 kB
Active:         461000 kB
Inactive:       176456 kB
SwapTotal:     1048568 kB
SwapFree:      1048568 kB
Dirty:             192 kB
Writeback:           0 kB
AnonPages:      358388 kB
Mapped:          79056 kB
Slab:            46620 kB
SReclaimable:    21900 kB
SUnreclaim:      24720 kB
PageTables:      13776 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   3075808 kB
Committed_AS:   599444 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    313280 kB
VmallocChunk: 34359424507 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     54080 kB
DirectMap2M:   4139008 kB
owner@owner-laptop:~$

but it's still not resuming from suspend. It's still doing that black screen with running hard drives thing. also i've noticed some other users are experiencing the same problem so i don't think it's a swap problem anymore.

I have used Hardy 8.04, Intrepid 8.10 and mint 5 and suspend and hibernation never worked. I tried all kinds of how to's I found on the forum but nothing worked. I did a clean install of Jaunty RC and voila - suspend and hibernate work outta the box!

---

### Post by Found on 2009-04-22
If i want to resize my swap? Is it possible to use Partition magic, or Ubuntu software for that? Because when i installed ubuntu i made it 1gb, but that's not enough :(

---

### Post by holyskeleton on 2009-04-22
> **Found said:**
> If i want to resize my swap? Is it possible to use Partition magic, or Ubuntu software for that? Because when i installed ubuntu i made it 1gb, but that's not enough :(

you can probably try the [how to]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0") to add more swap files.

---

### Post by Penguin Guy on 2009-04-22
> **holyskeleton said:**
> my laptop has 240 GB HD space which is 120x2 and I put / on one and /home on the other. isn't / called root or something like that?
Ahhh, you are correct, / = root. '/' and '/home' are examples of partitions. All Linux partitions use the same swap space.

Partiton1 <-----> SWAP <-----> Partition2

So it doesn't matter where it is, as long as you have 4GB-8GB swap anywhere on your computer then it will be fine.

EDIT: Also; there is no need to add more swap, just resize the current swap using GParted.

---

### Post by holyskeleton on 2009-04-22
> **presence1960 said:**
> I did a clean install of Jaunty RC and voila - suspend and hibernate work outta the box!

hmm maybe i should do a clean install of Jaunty after it comes out instead of upgrading to it?

---

