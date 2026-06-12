---
title: "The best way to Install Linux"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-17
I'm just wondering how people partition their hard drives when installing Linux. 

I myself am using a 250GB Acer laptop and have partitioned my hard drive as such, 75GB for "/ "(root), 5GB for "SWAP" and the remaining 160GB for "/home".

What have people found to be the most efficient ways to partition? Is there a recommended standard?

---

### Post by krishnandu.sarkar on 2010-10-17
LOL...you will never need 5GB of SWAP, 1GB is more than enough.

I don't think there is any standard regarding allocation of space. Just do it as per your need, but allocating more than 1GB to SWAP is just of no use.

---

### Post by Megaptera on 2010-10-17
As already said, it's a personal thing. Useful guide with screenshots in case it's of any help to you or others:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

### Post by Legeril on 2010-10-17
In regards to SWAP, I heard somewhere that 1.5x your memory is a good number to use. As my first install I thought best to over shoot than under shoot ;)

---

### Post by amjjawad on 2010-10-17
> **Legeril said:**
> I'm just wondering how people partition their hard drives when installing Linux. 

I myself am using a 250GB Acer laptop and have partitioned my hard drive as such, 75GB for "/ "(root), 5GB for "SWAP" and the remaining 160GB for "/home".

What have people found to be the most efficient ways to partition? Is there a recommended standard?

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

It's all up to you and to your needs.
I would attach a screen shot that shows my partitions but it's not good idea because I have perhaps 20 partitions and that might confuse you ;)

The most recommended and general scheme is:
1- Root (/) - ext4
2- Swap (SWAP)
3- Home (/home) - ext4

About SWAP, the more, the better unless you have for example more than 4GB of RAM. The main idea about SWAP partition is that partition will work as Virtual Memory, just like in Windows but the difference is, in Windows, you don't need to CREATE a partition for Virtual Memory while you need that in Ubuntu.
You're helping your RAM by providing some extra space for it to operate more efficiently. People might not find that so much interested especially nowadays when almost 80% have more than 2GB of RAM. I do have 2GB of RAM but my SWAP partition is 4GB. I have 500GB HDD so I don't mind to allocate 4GB for SWAP.
After all, it's all up to you and the way you're using your Laptop/PC.

---

### Post by Hippytaff on 2010-10-17
> **Legeril said:**
> In regards to SWAP, I heard somewhere that 1.5x your memory is a good number to use. As my first install I thought best to over shoot than under shoot ;)

I read the same and overcooked the swap partition, but its not the end of the world
. I did the standar /, swap, /root and /home. Purposefully went for a seperate home for future upgrades (Got rid of windows too :-)

---

### Post by bprins on 2010-10-17
But does the factor 2 stays "valid"?

Like, if you have 6GB memory, would it still be "better" to have 12GB of swap? Or does it get a bit over the top then?

---

### Post by Hippytaff on 2010-10-17
> **bprins said:**
> But does the factor 2 stays "valid"?

Like, if you have 6GB memory, would it still be "better" to have 12GB of swap? Or does it get a bit over the top then?

The advice is to double the ram for swap partition!? I don't know much about it so I went with the advice :-s

Not sure that sentance makes sense.

---

### Post by nlsthzn on 2010-10-17
The irony is the more RAM you have, the less swap you need (as it is less likely you will run out of free RAM requiring swapping to happen...

BUT this is very much a recurring topic I am sure and will find its way there very shortly with all the other exact same threads like this :D

---

### Post by krishnandu.sarkar on 2010-10-17
Upto 1GB RAM, "Double the Swap" theory goes perfect, but say if you have 4GB of RAM then 512MB Swap is just fine, As I said before 1GB SWAP is more than enough in more or less every condition

---

### Post by Elfy on 2010-10-17
The x1.5 /x2 RAM thing is in my opinion out of date. 

> LOL...you will never need 5GB of SWAP, 1GB is more than enough.Would not be so funny if you had 3Gb of RAM and then hibernated with only 1Gb swap.

I have swap=RAM at the moment.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by amjjawad on 2010-10-17
> **bprins said:**
> But does the factor 2 stays "valid"?

Like, if you have 6GB memory, would it still be "better" to have 12GB of swap? Or does it get a bit over the top then?

If you're running or working on lots of applications that require more RAM then it could be good idea but if you're a light user and use your PC/Laptop for browsing, etc then perhaps you don't need to double that (12GB).

As I mentioned in my previous post, it depends on your usage.
The only one who knows about the main usage of your machine is you :)

Once, I asked Ubuntu to install itself on an entire disk and I did not used Manual Installation. I found out when the installation is done that SWAP is less than 1GB even though I have 2GB of RAM. So, it wasn't double. When I install Manually, I prefer 4GB.
There's no harm in my opinion to allocate more space for SWAP but it could be a bit of a problem when you allocate say 500MB of SWAP while you have 1GB of RAM.
Again, I think 1.5x or 2.0x is more academic/general than particle.

Again, it's all depends on your hardware specifications + your daily usage.

---

### Post by amjjawad on 2010-10-17
> **krishnandu.sarkar said:**
> if you have 4GB of RAM then 512MB Swap is just fine

I tend to disagree with that.
As mentioned already, when you choose "Hibernate" and you have 512MB of SWAP, then it would look really ugly.

---

### Post by Legeril on 2010-10-17
I get the SWAP thing then, it's essentially just some extra space for your RAM to allocate resources when it gets overloaded. A very nice idea really.

Now if you assume 2 partitions for "/" and "/home" how easy is it to reinstall Linux on the root partition? Are there any points you would need to consider, or would a flat re-install while leaving /home alone leave all your files in-tact and assessable?

---

### Post by bprins on 2010-10-17
Google-d a bit on the subject. And indeed, 6GB ram doesn't require 12GB of swap. But it remains a vague subject to me. 

As far as I understand it now, you can never reserve "too much" for the swap partition. Rather have a few GBs saved for swap, since disks are over sized anyway (like, 1TB disks are more or less becoming the standard for new PCs). Rather throw away a bit of disk size, then having the risk (even when it's a small risk) to crash my laptop/PC, right?

---

### Post by amjjawad on 2010-10-17
> **forestpiskie said:**
> The x1.5 /x2 RAM thing is in my opinion out of date. 


I do agree with that.
In my opinion, they should say: it depends on your daily usage + your hardware specifications.

For example: if someone has 8GB of RAM, I don't think x2 or even x1.5 is good idea. It won't harm, yes but it's unnecessary step.

---

### Post by krishnandu.sarkar on 2010-10-17
> **amjjawad said:**
> I tend to disagree with that.
As mentioned already, when you choose "Hibernate" and you have 512MB of SWAP, then it would look really ugly.

Ya that's not sufficient if anyone opts for Hibernation. I specified that space guessing without Hibernation.

---

### Post by Elfy on 2010-10-17
> **Legeril said:**
> Now if you assume 2 partitions for "/" and "/home" how easy is it to reinstall Linux on the root partition? Are there any points you would need to consider, or would a flat re-install while leaving /home alone leave all your files in-tact and assessable?

If you reinstall with a seperate /home choose Manual/Advanced partitioning - set the mount points and make sure to NOT format the /home partition.

If you reinstall without a seperate /home choose Manual/Advanced partitioning - set the mount points and make sure NOT to format the / partition and the existing /home will remain as it is.

---

### Post by bprins on 2010-10-17
> **Legeril said:**
> I get the SWAP thing then, it's essentially just some extra space for your RAM to allocate resources when it gets overloaded. A very nice idea really.

Now if you assume 2 partitions for "/" and "/home" how easy is it to reinstall Linux on the root partition? Are there any points you would need to consider, or would a flat re-install while leaving /home alone leave all your files in-tact and assessable?

That's what I have here.

Yes, you can reinstall linux leaving your /home partition unchanged.

---

### Post by Elfy on 2010-10-17
> **krishnandu.sarkar said:**
> Ya that's not sufficient if anyone opts for Hibernation. I specified that space guessing without Hibernation.

Then make sure your sweeping statements sweep it all up next time ;)

---

### Post by Hippytaff on 2010-10-17
> **Legeril said:**
> I get the SWAP thing then, it's essentially just some extra space for your RAM to allocate resources when it gets overloaded. A very nice idea really.

Now if you assume 2 partitions for "/" and "/home" how easy is it to reinstall Linux on the root partition? Are there any points you would need to consider, or would a flat re-install while leaving /home alone leave all your files in-tact and assessable?
  Thats the theory

---

### Post by Sylslay on 2010-10-17
I often have dual boot on hdd.

Becouse hdd have 2 pleats and sometimes 2 heads, usually do partitions lake that:

[(full HDD size)-1GB (for swap)]2

Than my hdd is bit faster (optimizated for geometry) -meaby?

So its pration are

(ext4 halfsize minus 512MB) and 1GB Swap and (ext4 halfsize minus 512MB)

But newer run benchmark to confirm that partitoning is better then others say 24% plus 2GB swap plus 74% when hdd=100GB

---

### Post by HermanAB on 2010-10-17
I don't think anyone mentioned it:
You need your /swap to be at least 2xRAM if you want to use Suspend, otherwise suspend won't work.

For a personal machine I normally make:
/ = 20GB
/swap = 2xRAM
/home = rest

Unless it is a server, in which case there are many more things to worry about.

---

### Post by Joshwaa on 2010-10-17
Well I have one partition for my Win7 backup, another one labeled "System Reserved" then I have a 30gb Ubuntu partition which has the bootloader installed on that partition and a EasyBCD loader as my main loader so if I need to I can just delete the partition. I'd get a Swap space partition but I can't as I already have 4 partitions.. hmm.. if anyone knows if system reserved is useless then let me know through PM or whatever :)

---

### Post by Elfy on 2010-10-17
> **HermanAB said:**
> I don't think anyone mentioned it:
You need your /swap to be at least 2xRAM if you want to use Suspend, otherwise suspend won't work.

For a personal machine I normally make:
/ = 20GB
/swap = 2xRAM
/home = rest

Unless it is a server, in which case there are many more things to worry about.

suspend works with swap=ram here (or at least more or less = )

---

### Post by Elfy on 2010-10-17
> **Joshwaa said:**
> Well I have one partition for my Win7 backup, another one labeled "System Reserved" then I have a 30gb Ubuntu partition which has the bootloader installed on that partition and a EasyBCD loader as my main loader so if I need to I can just delete the partition. I'd get a Swap space partition but I can't as I already have 4 partitions.. hmm.. if anyone knows if system reserved is useless then let me know through PM or whatever :)

You can use a swap file instead of a swap partition in some cases - depends really.

---

### Post by Joshwaa on 2010-10-17
> **forestpiskie said:**
> You can use a swap file instead of a swap partition in some cases - depends really.

A swap file? What's that?

---

### Post by amjjawad on 2010-10-17
> **forestpiskie said:**
> If you reinstall with a seperate /home choose Manual/Advanced partitioning - **set the mount points and make sure to _NOT_ format the /home partition.**

If you reinstall without a seperate /home choose Manual/Advanced partitioning - **set the mount points and make sure _NOT_ to format the / partition and the existing /home will remain as it is**.

I liked that so much and honestly I was looking for such advice.
However, is it safe to do that without losing anything? I've never tried it yet but I'm willing to.

---

### Post by Elfy on 2010-10-17
> **Joshwaa said:**
> A swap file? What's that?

[Swap is generally associated with a swap partition, perhaps because the user is prompted to create a swap partition at the time of installation. In fact, any file can be used as a swapping device, be it a partition or a conventional file. Although, to improve the responsiveness, it's recommended to have a good sized amount of RAM available. Swap can be added by adding a swap file. ]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?")

A file instead of a partition.

---

### Post by Joshwaa on 2010-10-17
> **forestpiskie said:**
> [Swap is generally associated with a swap partition, perhaps because the user is prompted to create a swap partition at the time of installation. In fact, any file can be used as a swapping device, be it a partition or a conventional file. Although, to improve the responsiveness, it's recommended to have a good sized amount of RAM available. Swap can be added by adding a swap file. ]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?")

A file instead of a partition.

I found a guide on the internet, so it'd be such thing as

```
sudo dd if=/dev/zero of=/mnt/4096Mb.swap bs=1M count=4096
```

To start it off?

---

### Post by Elfy on 2010-10-17
> **amjjawad said:**
> I liked that so much and honestly I was looking for such advice.
However, is it safe to do that without losing anything? I've never tried it yet but I'm willing to.

I was touch unwilling as well - but backed up home ( which if course I always do anyway ... ) and tried it out - all was there.

It did help my peace of mind to know that all my data is actually on other drives and just symlinked to the ubuntu home folders.

---

### Post by Elfy on 2010-10-17
> **Joshwaa said:**
> I found a guide on the internet, so it'd be such thing as

```
sudo dd if=/dev/zero of=/mnt/4096Mb.swap bs=1M count=4096
```

To start it off?

You'd have to ask someone else I'm afraid - being a mod here is not a symbol of your technical knowledge :)  EDIT - - yea that _looks_ about right for a 4096Mb swap file

I'm just a really laid back guy who uses linux :p (usually ... )

---

### Post by Joshwaa on 2010-10-17
> **forestpiskie said:**
> You'd have to ask someone else I'm afraid - being a mod here is not a symbol of your technical knowledge :) 

I'm just a really laid back guy who uses linux :p (usually ... )

Haha! Yeah, I made a swap file, I followed a guide on the Ubuntu Documentation and it says there is now swap space..
```
SwapTotal:       4194300 kB
SwapFree:        4194300 kB

```

wahey.
I gave it that much space, even though I'm only on a 30gb Partition, I have 4gb of ram. :P

---

### Post by amjjawad on 2010-10-17
> **Joshwaa said:**
> Well I have one partition for my Win7 backup, another one labeled "System Reserved" then I have a 30gb Ubuntu partition which has the bootloader installed on that partition and a EasyBCD loader as my main loader so if I need to I can just delete the partition. I'd get a Swap space partition but I can't as I already have 4 partitions.. hmm.. if anyone knows if system reserved is useless then let me know through PM or whatever :)

I assume you have 4 Primary Partitions that's why you can't get more partitions.
Ubuntu needs _**minimum**_ 2 partitions (root and swap).

You can create an extended partition (remove one of the primary partitions that you don't need) instead of one of the primary partitions and once you have extended partition, you can create as many logical partitions as you want. I have 10 or more logical partitions inside my extended partition. This is what I need at the moment.

As for the reserved partitions, it's for recovery purposes and that partition comes with laptops nowadays. It's there by default. I don't think it's large in size so I don't think it's good idea to get rid of it.

---

### Post by Joshwaa on 2010-10-17
> **amjjawad said:**
> I assume you have 4 Primary Partitions that's why you can't get more partitions.
Ubuntu needs _**minimum**_ 2 partitions (root and swap).

You can create an extended partition (remove one of the primary partitions that you don't need) instead of one of the primary partitions and once you have extended partition, you can create as many logical partitions as you want. I have 10 or more logical partitions inside my extended partition. This is what I need at the moment.

As for the reserved partitions, it's for recovery purposes and that partition comes with laptops nowadays. It's there by default. I don't think it's large in size so I don't think it's good idea to get rid of it.


Thing is, I **_need_** the partitions I have. Ones for Windows 7, ones for the Backup and ones for the System Reserved, and I don't fancy removing any of them. My ubuntu partition is 30gb and I have a 4gb swap, it seems sufficient enough.

---

### Post by amjjawad on 2010-10-17
> **forestpiskie said:**
> I was touch unwilling as well - but backed up home ( which if course I always do anyway ... ) and tried it out - all was there.

It did help my peace of mind to know that all my data is actually on other drives and just symlinked to the ubuntu home folders.

Yes sure, backup first then do whatever you want :)

Thanks!

---

### Post by amjjawad on 2010-10-17
> **Joshwaa said:**
> Thing is, I **_need_** the partitions I have. Ones for Windows 7, ones for the Backup and ones for the System Reserved, and I don't fancy removing any of them. My ubuntu partition is 30gb and I have a 4gb swap, it seems sufficient enough.

In that case yes, you can keep it. I misunderstood your post and thought you don't have a swap partition.
But in general, it's always good to have an extended partition.

For backup, I use external HDDs.

---

### Post by Joshwaa on 2010-10-17
> **amjjawad said:**
> In that case yes, you can keep it. I misunderstood your post and thought you don't have a swap partition.
But in general, it's always good to have an extended partition.

For backup, I use external HDDs.
Yeah, well you see I'm a 15 year old kid strapped for cash at the minute as I need to earn about £350 to buy out my mobile phone contract:

**Start opinion/rant**
(Guys, never go for Virgin Mobile - they're scammers, also, never get the Nokia X6, it's terrible)
**End opinion/rant**

so I can't really afford any external HDs, I've been tempted to extend my Ubuntu partition but this would mean reformatting it.. which isn't too helpful since I've had to reinstall Ubuntu once already in the past few days due to GTK+ failure.. So yeah, I'll just stick to what I have, 30gb Ubuntu partition with a 4gb swap file since I have 4gb ram.

**Edit:** I don't have a swap partition, I have a swap **_file_**.

---

### Post by amjjawad on 2010-10-17
> **Joshwaa said:**
> so I can't really afford any external HDs, I've been tempted to extend my Ubuntu partition but this would mean reformatting it.. which isn't too helpful since I've had to reinstall Ubuntu once already in the past few days due to GTK+ failure.. So yeah, I'll just stick to what I have, 30gb Ubuntu partition with a 4gb swap file since I have 4gb ram.

If you noticed my signature, I have 9 OS's installed so I can't really keep the backup partition in my internal HDD, that's why I use external ones but that's only me :)
In your case, I meant it's advisable to use external but of course you can't buy one now ... you might in the future which is very good idea :)


> **Edit:** I don't have a swap partition, I have a swap **_file_**.Yes, now it's very clear :D

---

### Post by adipramono on 2010-10-17
I have my 763 MB of SWAP and 2.7 GB of RAM. Sometimes I think I don't even need any SWAP for my laptop because the memory from RAM itself is already more than enough for my everyday task.

---

### Post by amjjawad on 2010-10-17
> **adipramono said:**
> I have my 763 MB of SWAP and 2.7 GB of RAM. Sometimes I think I don't even need any SWAP for my laptop because the memory from RAM itself is already more than enough for my everyday task.

You might not need a swap partition but your Ubuntu does :)

If you use [Hibernate]("http://en.wikipedia.org/wiki/Hibernation_%28computing%29"), I think you'll need more than 763MB of swap.

P.S.
Read the whole thread if you didn't yet ;)

---

