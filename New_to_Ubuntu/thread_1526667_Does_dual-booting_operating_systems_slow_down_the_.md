---
title: "Does dual-booting operating systems slow down the computer?"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Bublex on 2010-07-08
Thanks :)

---

### Post by arochester on 2010-07-08
No. In dual booting only one OS runs at a time.It's not as though it runs two OS's...

---

### Post by cascade9 on 2010-07-08
It sort of can.......mainly due to the way that HDDs dont have a constant transfer speed. 

The 1st sector on a HDD is the fastest, and the last is the slowest. So if you are dual-booting, and have 1 OS at the beginning and 1 OS in the middle/toward the end of the drive (which is typical) then the OS closer to the end will be slightly slower than if it was a single OS. 

It doesnt make a that much of a difference though.

---

### Post by arubislander on 2010-07-08
And of course it kills boot-up speeds :)

---

### Post by Paqman on 2010-07-08
> **cascade9 said:**
> 
It doesnt make a that much of a difference though.

On modern magnetic drives it makes almost no difference. 
On solid state drives it makes exactly no difference.

---

### Post by Grenage on 2010-07-08
> **Bublex said:**
> Does dual-booting operating systems slow down the computer?

No.

---

### Post by AAccount on 2010-07-08
Theoretically it shouldn't. However, I have had Windows XP's boot time significantly increase when resizing its partition. I ended up using GPartEd to preformat the drive and then install Windows and Linux. I still have no idea why XP does this.

---

### Post by Paqman on 2010-07-09
> **AAccount said:**
> Theoretically it shouldn't. However, I have had Windows XP's boot time significantly increase when resizing its partition. I ended up using GPartEd to preformat the drive and then install Windows and Linux. I still have no idea why XP does this.

The first time you boot Windows after resizing it's partition it will run through a check of the filesystem. It'll then reboot and boot like normal.

---

### Post by audiomick on 2010-07-09
> **AAccount said:**
> Theoretically it shouldn't. However, I have had Windows XP's boot time significantly increase when resizing its partition. I ended up using GPartEd to preformat the drive and then install Windows and Linux. I still have no idea why XP does this.
Don't know if it is relevant to this, but XP needs a lot of elbow room. If its partition is too small, it will not be happy.

---

### Post by Paqman on 2010-07-09
> **audiomick said:**
> Don't know if it is relevant to this, but XP needs a lot of elbow room. If its partition is too small, it will not be happy.

Any filesystem is going to be unhappy once it gets above about 80% full, so "elbow room" is always a good idea.

---

### Post by audiomick on 2010-07-09
> **Paqman said:**
> Any filesystem is going to be unhappy once it gets above about 80% full, so "elbow room" is always a good idea.
For example: an acquaintance recently asked a friend of mine to help him with his mac. The machine was taking nearly 20 minutes to boot. It turned out he only had about 500MB of free space on his 120GB drive.

---

### Post by cascade9 on 2010-07-09
> **Paqman said:**
> On modern magnetic drives it makes almost no difference. 
On solid state drives it makes exactly no difference.

'Almost' would depend on just how much you do notice inceases/drops in perfromance. What one person will notice, another wont. 

True on with SSDs it makes no difference, but they are still uncommon.

---

### Post by Paqman on 2010-07-09
> **cascade9 said:**
> 'Almost' would depend on just how much you do notice inceases/drops in perfromance. What one person will notice, another wont.

No human will notice the difference. You *might* get some statistically significant results from benchmarking, but overall it's a non-issue.

> 
True on with SSDs it makes no difference, but they are still uncommon.

Not in my house they ain't! ;)

---

### Post by tarps87 on 2010-07-09
> **audiomick said:**
> Don't know if it is relevant to this, but XP needs a lot of elbow room. If its partition is too small, it will not be happy.

I think that main cause of this is it uses a paging file instead of a partition and this can actually shrink in size when the partition gets full, but default most if not all distros use a swap partition not a file

---

### Post by cascade9 on 2010-07-09
> **Paqman said:**
> No human will notice the difference. You *might* get some statistically significant results from benchmarking, but overall it's a non-issue.

Not in my house they ain't! ;)

I disagree. When I changed from an old SATA HDD (Seagate 7200 80GB SATA, aprox 60-70MB/sec max IIRC) to a newer SATA HDD (WD 5400 1TB Green Power, 90-100MB/sec max) I noticed it was faster. Mainly in bootup times. 

People sure do notice the difference with SSDs, and they tend to run about twice to two and half times as fast as a (modern) 7200. So why wouldnt people notice if they have half the access speed (which is typical of 'end of the drive' speeds)?

---

### Post by da burger on 2010-07-09
I'm pretty sure he was refering to the speed difference from installing a second OS on the HD, not on switching HDs or changing to an SSD.

---

### Post by Bublex on 2010-07-10
> **da burger said:**
> I'm pretty sure he was refering to the speed difference from installing a second OS on the HD, not on switching HDs or changing to an SSD.

Exactly,

Edit: My friend just installed ubuntu on his machine, he's currently dual booting xp and ubuntu, however ubuntu boots first, he was wondering if there's a way to make windows xp boots as primary os?

thanks!

---

### Post by cascade9 on 2010-07-10
> **da burger said:**
> I'm pretty sure he was refering to the speed difference from installing a second OS on the HD, not on switching HDs or changing to an SSD.

True, but changing the HDD had pretty much the same effect as if I had of been dual-booting from the last one third of the drive. 70MB/sec is the speed my 1TB drive has one third of the way though (and it drops even lower toward the end).  

How much of a speed impact you will get depends on how fast the drive is overall, how much speed it 'loses' toward the end of the drive, and how far along you have the second OS installed. 

SSDs were brought up merely because the speed they get is constand throughout, and doesnt vary like a mechanical HDD.

---

### Post by Bublex on 2010-07-11
Bump

---

### Post by KdotJ on 2010-07-11
> **audiomick said:**
> For example: an acquaintance recently asked a friend of mine to help him with his mac. The machine was taking nearly 20 minutes to boot. It turned out he only had about 500MB of free space on his 120GB drive.



As they say, to find a specific item in a shopping bag, it's easier when the bag has more empty space in it as opposed to the bag being jammed packed

---

### Post by ov3rcl0ck on 2010-07-11
> **AAccount said:**
> Theoretically it shouldn't. However, I have had Windows XP's boot time significantly increase when resizing its partition. I ended up using GPartEd to preformat the drive and then install Windows and Linux. I still have no idea why XP does this.
When gparted resizes a drive, if theres any fragments in the area that is being removed it will basically defragment them or move them closer in on the harddrive. So basically it might have defragged your harddrive a bit.

> **arubislander said:**
> And of course it kills boot-up speeds :)

No it doesn't.. you probably did something wrong..

---

### Post by arubislander on 2010-07-25
> **ov3rcl0ck said:**
> No it doesn't.. you probably did something wrong..

Sure it does, if you leave the default settings, it'll wait a few seconds before booting into the default OS. As you have two OS's (since you're dual booting) you will want a few seconds to choose which OS to boot. So it kills the boot speed. Or at least makes it that much slower...

---

### Post by Bkidiooo on 2010-07-25
> **Paqman said:**
> The first time you boot Windows after resizing it's partition it will run through a check of the filesystem. It'll then reboot and boot like normal.

Thats true my Win7 partition did a system check but i skipped it ;)

---

