---
title: "Can p2p be a danger for the hard drive?"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by joaogpeixoto on 2010-11-16
Hi. I'm using Ubuntu 10.04 and p2p software ("amule" and "ktorrent") on an HP Probook 6540b laptop. 

I got a little bit worried when I heard rumors that intensive use of p2p software (like 12hrs a day) might damage the hard drive, as some parts of the HD are accessed much more often than others, thus creating bad blocks/sectors.

Yes this true in any way? If so, can anything be done to prevent it?

---

### Post by Hoopz on 2010-11-16
I don't know for sure.  but I highly doubt it.   It doesn't make sense that a torrent program would be programmed that way

---

### Post by soldier1st on 2010-11-16
p2p itself will not damage the hard drive but any apps you download from it depending on what it is could damage your hard drive or even destroy it. with p2p you always need to be careful with it.

---

### Post by CharlesA on 2010-11-16
Don't worry about it. A hard drive is made to be accessed frequently.

---

### Post by 3rdalbum on 2010-11-16
I have a laptop hard drive in my server, that runs 24/7. It's not accessed much, though. No problems so far.

You'd probably want to use an external 3.5 inch hard disk anyway, as they are much tougher and have a bigger capacity-per-dollar. Big capacity means a lot when torrenting.

---

### Post by joaogpeixoto on 2010-11-17
> **CharlesA said:**
> Don't worry about it. A hard drive is made to be accessed frequently.

It sure is made to be accessed frequently, but that's not really my point.

I may not have expressed myself clearly, so let me put it this way:
If you constantly access, say 12+ hrs/day, just a tiny part of the disk (one or two shared/download folders) (I suppose that's what happens with p2p in Ubuntu, please correct me if I'm wrong), Isn't that tiny part going to give you trouble a lot sooner (because of the extra stress), thus reducing the Hard Drive's life time?

---

### Post by CharlesA on 2010-11-17
Magnetic storage doesn't work like that.

Data isn't stored on one single area of the drive, but it's stored where there is space.

---

### Post by walt.smith1960 on 2010-11-18
> **CharlesA said:**
> Magnetic storage doesn't work like that.

Data isn't stored on one single area of the drive, but it's stored where there is space.

I wonder about SSDs and flash drives though, which do have a (high #)finite read/write cycles life.

---

### Post by CharlesA on 2010-11-18
> **walt.smith1960 said:**
> I wonder about SSDs and flash drives though, which do have a (high #)finite read/write cycles life.
SSDs are a whole different animal. I would only run the OS on an SSD and have my data stored elsewhere, but that's just me.

---

### Post by theozzlives on 2010-11-18
> **CharlesA said:**
> Magnetic storage doesn't work like that.

Data isn't stored on one single area of the drive, but it's stored where there is space.

+1 on that. It just looks like you're writing to one folder. On the hard drive is an index that tells where the data is stored. It's then displayed in a user friendly manner (folders and such). DOS use to call it the File Allocation Tables which I think is an appropriate name.

---

### Post by Buxxx on 2010-11-18
I had a 3yrs old laptop and there was a time when did not switch it off for a month. I'm not joking, the p2p was running 24/7 for more than a month and I still have that laptop and no problem arised by now.

---

### Post by psusi on 2010-11-18
> **3rdalbum said:**
> 
You'd probably want to use an external 3.5 inch hard disk anyway, as they are much tougher and have a bigger capacity-per-dollar. Big capacity means a lot when torrenting.

Not true.  External drives are just internal drives with an external enclosure around them.  You pay a premium for that enclosure, so if you don't need to be able to remove the drive and have it be portable, you are better off just buying the bare drive and installing it in your case.  Also external USB enclosures means you can't do things like SMART diagnostics, and access will be slower.

> **joaogpeixoto said:**
> It sure is made to be accessed frequently, but that's not really my point.

I may not have expressed myself clearly, so let me put it this way:
If you constantly access, say 12+ hrs/day, just a tiny part of the disk (one or two shared/download folders) (I suppose that's what happens with p2p in Ubuntu, please correct me if I'm wrong), Isn't that tiny part going to give you trouble a lot sooner (because of the extra stress), thus reducing the Hard Drive's life time?

In theory, yes, if you constantly access the same part of the disk you put more wear and tear on it, and it will eventually wear out, but hard disks can take a LOT of access, and torrenting does not repeatedly access the same part of the disk.  It does tend to cause a lot of fragmentation on some filesystems though ( not ext4 ).

> **CharlesA said:**
> Magnetic storage doesn't work like that.

Data isn't stored on one single area of the drive, but it's stored where there is space.

It is stored where the filesystem decides to store it.  If an application keeps overwriting the same part of a file, the same part of the disk will be written to.

> **walt.smith1960 said:**
> I wonder about SSDs and flash drives though, which do have a (high #)finite read/write cycles life.

SSDs deal with this by actually migrating logical sectors around to different physical flash blocks to level the wear out over the whole disk, even if you keep writing to the same logical block.

---

### Post by A_M_S on 2010-11-18
> **joaogpeixoto said:**
> It sure is made to be accessed frequently, but that's not really my point.

I may not have expressed myself clearly, so let me put it this way:
If you constantly access, say 12+ hrs/day, just a tiny part of the disk (one or two shared/download folders) (I suppose that's what happens with p2p in Ubuntu, please correct me if I'm wrong), Isn't that tiny part going to give you trouble a lot sooner (because of the extra stress), thus reducing the Hard Drive's life time?

Yes i think that could happen, but i wouldn't worry much about that. A HD disc is built to withstand constant use.

A HD is a mechanical device so it should be handled carefully when being used.

---

### Post by CharlesA on 2010-11-18
> **psusi said:**
> 
It is stored where the filesystem decides to store it.  If an application keeps overwriting the same part of a file, the same part of the disk will be written to.

Thanks for the clarification. I was referring more to new files, rather then existing files, but you have a good point. :)

---

### Post by ppv on 2010-11-18
For the main point of the thread the p2p app is not going to do anymore harm than any other application that would use the hard drive in a similar manner.

---

