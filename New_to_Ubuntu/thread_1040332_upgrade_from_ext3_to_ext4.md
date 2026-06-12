---
title: "upgrade from ext3 to ext4"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by BDNiner on 2009-01-15
I wanted to know if it is possible to do an in place upgrade from ext3 to ext4 without losing any data? I know it is kinda a stretch and I would obviously backup my data before attempting it, but it would be a nice feature to upgrade without repartitioning.

---

### Post by Titan8990 on 2009-01-15
> I wanted to know if it is possible to do an in place upgrade from ext3 to ext4 without losing any data?


Using Ext4, on a freshly installed system, carries the risk of losing your data....

Ext4 is still being developed and is not yet a format that I would trust data on that I wouldn't want to lose.

Only Ubuntu 9.04 alpha has the support for EXT4

---

### Post by talsemgeest on 2009-01-15
> **BDNiner said:**
> I wanted to know if it is possible to do an in place upgrade from ext3 to ext4 without losing any data? I know it is kinda a stretch and I would obviously backup my data before attempting it, but it would be a nice feature to upgrade without repartitioning.
The only way to upgrade to EXT4 without losing data is to stick your data somewhere else first ;)

Since it completely rearranges the way the data is arranged on your disk, there is no way to leave the data intact.

Also, take heed of Titan8990's message.

---

### Post by BDNiner on 2009-01-15
Well Ext4 is stable and has been included with the kernel as of version 2.6.28. It is just in the testing stage as far as ubuntu is concerned. I do create regular backups i just don't want to deal with moving all my mp3s, pictures and videos to my windows computer while performing the upgrade to ext4.

---

### Post by stchman on 2009-01-15
> **BDNiner said:**
> I wanted to know if it is possible to do an in place upgrade from ext3 to ext4 without losing any data? I know it is kinda a stretch and I would obviously backup my data before attempting it, but it would be a nice feature to upgrade without repartitioning.

I would not do it.  I don't see any advantage of changing to EXT4.  EXT4 may be a little faster but until there is a need and great advantages then it i would not be recommended.

---

### Post by wrichtmyer on 2009-01-24
> **stchman said:**
> I would not do it.  I don't see any advantage of changing to EXT4.  EXT4 may be a little faster but until there is a need and great advantages then it i would not be recommended.

On test actually. EXT4 is 3 times faster than Ubuntu. With it's revolutionary packet system of transferring and using data, it's much more efficient and faster than the poor Ext3. I believe Ext4 is one of the main implements of making Ubuntu's boot up, (as well as the regular performance) MUCH faster.

---

### Post by kellemes on 2009-01-24
> **stchman said:**
> I would not do it.  I don't see any advantage of changing to EXT4.  EXT4 may be a little faster but until there is a need and great advantages then it i would not be recommended.

It is MUCH faster indeed.

---

### Post by Cypher on 2009-01-24
For an average user of Ubuntu upgrading from EXT3 to EXT4 will yield no real benefit and is probably not really worth the hassle..

---

### Post by fubbleskag on 2009-01-24
it would seem that an in-place upgrade is in fact possible, and seemingly safe; although, review the comments following this article regarding the fact that existing files will not make use of the ext4's new extent system until/unless you use the online defrag tool.

[http://buranen.info/?p=345=1](http://buranen.info/?p=345=1)

---

### Post by Paqman on 2009-01-24
> **wrichtmyer said:**
> EXT4 is 3 times faster than Ubuntu.

Realistically, you're not likely to see a huge improvement unless you use a SSD. The bottleneck in data transfer isn't the filesystem, it's the read/write speed of the hard drive.

---

### Post by medic on 2009-01-24
you mean to say that we wont be much difference in the speed on a regular PC?

---

### Post by mgranet on 2009-01-24
I have two SATA drives, one for my x64 O.S., and one for my data. I'm a rather advanced user, so I have no problems with being adventurous(sp?), but I still like a decently stable system. When 9.04 comes out, I was planning on converting my O.S. drive to ext4, and leaving my data drive ext3; with a possible conversion to ext4 @ 9.10. On hearing things such as 'increased possibility of data loss', and 'only really works with SSD's', it would be great if I could get input on what I might do.

---

### Post by Paqman on 2009-01-24
> **medic said:**
> you mean to say that we wont be much difference in the speed on a regular PC?

The only benchmarks i've seen show only slight improvements on a machine with an SSD. I'd be surprised if you saw any noticeable improvement on a magnetic HDD.

Having said that, i'll probably use ext4 for the root partition on my HDDwhen I upgrade to Jaunty. It's stable, so why not use it?

---

### Post by Cypher on 2009-01-24
> **medic said:**
> you mean to say that we wont be much difference in the speed on a regular PC?

That is correct, on a day to day basis you will not notice a lot of difference..

---

### Post by ethoxyethaan on 2009-01-24
Reasons to switch to EXT4:

- you want to make more than 32 000 sub directories, up to 64 000
- you want to use 256 bytes filenames instead of 255.
- you want to store more than 2 TB in 1 file up to 16 TB
- you want a partition greater than 16 TB up to 1EB.

ouch...

---

### Post by Frak on 2009-01-24
I actually have to say, there would probably be no improvement using EXT4. The bottleneck on regular HDDs prevents EXT4 from showing much improvement. You would need to have an SSD to do anything much noticeable.

---

### Post by mgranet on 2009-01-24
I have 1.5 more questions. It may not increase system speed, but does it noticeably affect boot speed, even with a SATA drive? If so, would it just be advantageous to just put my core O.S. partition as ext4?

---

### Post by Frak on 2009-01-24
> **mgranet said:**
> I have 1.5 more questions. It may not increase system speed, but does it noticeably affect boot speed, even with a SATA drive? If so, would it just be advantageous to just put my core O.S. partition as ext4?
I didn't notice a difference on my Sata-300 drive, but I did notice it on my SCSIs.

---

### Post by Paqman on 2009-01-24
> **mgranet said:**
> I have 1.5 more questions. It may not increase system speed, but does it noticeably affect boot speed, even with a SATA drive? If so, would it just be advantageous to just put my core O.S. partition as ext4?

It's unlikely to speed up your boot, but if you were going to migrate anything to ext4 the core OS is the least risky, and the most likely to benefit from any speed increase.

Even if the filesystem went completely bananas, reinstalling the OS is pretty painless. It's your data you want to be paranoid about.

---

### Post by Vaedrah on 2009-01-26
Interesting thread. Perhaps the best test for ext4 over ext3 is to actual compare both side by side in the real world.

Perhaps using a virtual machine would be an easy way to accomplish this(VirtualBox, VmWare etc). If a version of Ubuntu 9.04 alpha is available, the virtual drive created could use ext4. Equally Ubuntu 8.04 and/or Ubuntu 8.10 could be placed on another virtual drive.

This approach will keep all data intact on the host - the guest however can be completely sacrificial.

If I find a download of Ubuntu 9.04 alpha I might try this myself. Otherwise I am certainly interested to see any results other people may obtain! :)

---

### Post by Muffinabus on 2009-01-26
> **Vaedrah said:**
> Interesting thread. Perhaps the best test for ext4 over ext3 is to actual compare both side by side in the real world.

Perhaps using a virtual machine would be an easy way to accomplish this(VirtualBox, VmWare etc). If a version of Ubuntu 9.04 alpha is available, the virtual drive created could use ext4. Equally Ubuntu 8.04 and/or Ubuntu 8.10 could be placed on another virtual drive.

This approach will keep all data intact on the host - the guest however can be completely sacrificial.

If I find a download of Ubuntu 9.04 alpha I might try this myself. Otherwise I am certainly interested to see any results other people may obtain! :)

Phoronix did a series of benchmarks:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=4)

Also, the Jaunty alpha can be found here:

[http://cdimage.ubuntu.com/daily-live/20090126/](http://cdimage.ubuntu.com/daily-live/20090126/)

---

### Post by TheLions on 2009-01-26
> **Frak said:**
> I actually have to say, there would probably be no improvement using EXT4. The bottleneck on regular HDDs prevents EXT4 from showing much improvement. You would need to have an SSD to do anything much noticeable.

[IMG]http://www.phoronix.com/data/img/results/ubuntu_ext4/4.png[/IMG]

ext4 compared to other filesystems (on SSD disk):
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=4)

too bad that NTFS isn't there!:p

---

### Post by Vaedrah on 2009-01-27
Great information Muffinabus and TheLions. I am downloading Ubuntu 9.04 alpha 3 but it's currently on a slow connection and may take a day or two.

Personally I think that any advances in technology probably have some motivation in real world needs so this ext4 thing is worth pursuing (at least to my appreciations). 

Here is an offball comment - people used to operate "valve" or "vacuum tube" radios to listen to AM. When the "transistor" came around, it was promoted as "instant turn on radio" - i.e. why wait for old vacuum tube filaments to "warm up". Interestingly, modern computers take ages to "power up". This turn on period is waste time so I fully appreciate any efforts to obviate this wastage. Equally, any system that better uses the hardware that is here and now is worth an investigation.

Hard drives are mechanical systems and a major weak link in terms of reliability. The sooner they are ditched the better I guess :)

I'll report:) back on my findings - if at all interesting; no harm done otherwise with VM experiments.

---

### Post by jerome1232 on 2009-01-27
Does testing a file system in a virtual machine actually show anything, I mean your writing to an ext4 file system. The disk is actually an image file which is on an ext3 file system. Do you see my line of thinking here.

---

### Post by Vaedrah on 2009-01-27
I agree jerome1232 - there are no absolutes in "truth" - however we can try alternatives out with direct experience.

The VM approach is inexact but so to is animal testing on drugs; please consider

1. If an animal test shows extreme toxicity then why engage a human trial?
2. If an animal test shows potential efficacy then "perhaps" future trials are imaginable?

The VM is just a "tool" - it allows some information albeit imperfect but maybe not throw away as a tool because it shines with some lower ter. 

In any arena of thought the subject matter still has some center-poise
of potential applicability - equally there are no sure bets on "the best" or "the worst"; I guess I prefer direct tests and I like to read the adventures people have have.

---

### Post by talsemgeest on 2009-01-27
> **jerome1232 said:**
> Does testing a file system in a virtual machine actually show anything, I mean your writing to an ext4 file system. The disk is actually an image file which is on an ext3 file system. Do you see my line of thinking here.
I have been told that the speed increase in ext4 is more evident in a vm than on a physical hard drive, (just don't ask me why, I don't know :))

---

### Post by jerome1232 on 2009-01-27
> **talsemgeest said:**
> I have been told that the speed increase in ext4 is more evident in a vm than on a physical hard drive, (just don't ask me why, I don't know :))

That's insane! lol, I was mostly thinking out loud about it, seeing if what I said made sense, not criticizing anything. I'm very excited to see ext4 come out.

---

### Post by dmizer on 2009-01-27
> **talsemgeest said:**
> I have been told that the speed increase in ext4 is more evident in a vm than on a physical hard drive, (just don't ask me why, I don't know :))

It is more evident when the host OS has ext4. This is because ext4 is more capable of handling the large file size required by virtual machines. So if your vmx is on an ext4 drive, you will see significant performance improvement in your virtual machine (guest).

---

### Post by talsemgeest on 2009-01-27
> **dmizer said:**
> It is more evident when the host OS has ext4. This is because ext4 is more capable of handling the large file size required by virtual machines. So if your vmx is on an ext4 drive, you will see significant performance improvement in your virtual machine (guest).
I'm just going off what bodhizazen has said on irc, so I can't confirm what the speed differences were. Try asking him yourself. :)

---

### Post by Frak on 2009-01-27
> **dmizer said:**
> It is more evident when the host OS has ext4. This is because ext4 is more capable of handling the large file size required by virtual machines. So if your vmx is on an ext4 drive, you will see significant performance improvement in your virtual machine (guest).
ooooooo

Didn't think of that. I must now go play with Jaunty. :)

---

### Post by dmizer on 2009-01-27
> **Frak said:**
> ooooooo

Didn't think of that. I must now go play with Jaunty. :)

Yeah, I wanted to implement it on my production Hardy server, but it requires a newer kernel. For now, I wait. :( Should be able to make it work on Ibex fairly easily though.

---

### Post by BDNiner on 2009-01-27
All this has made me really contemplate building a test computer. I find there is only so much i can test in a VM. Especially since creating a VM that use ext4 on a computer that runs ext3 would not provide a realistic testing environment.

But seeing as it is a choice that a lot of people are going to have to make in the coming year i was wondering if i could 'upgrade' to ext4 without reinstalling my whole system?

very interesting links in your sig dmizer, they deserve a thankyou!

---

### Post by talsemgeest on 2009-01-27
I believe you can convert an ext3 filesystem to ext4, but you will not have all of the benefits of a clean install. If you are benchmarking the filesystems, the only way to get a fair test is to start on a clean partition.

---

### Post by Jynxx on 2009-01-27
So will ext4 be standard in Jaunty?

---

### Post by dmizer on 2009-01-27
It's already available in Jaunty: [http://www.nabble.com/My-experiences-with-ext4-on-Jaunty-p21235823.html](http://www.nabble.com/My-experiences-with-ext4-on-Jaunty-p21235823.html)

Disclaimer:
Jaunty is still in development. Use Jaunty for TESTING ONLY. This is not ready for a production environment yet.

---

