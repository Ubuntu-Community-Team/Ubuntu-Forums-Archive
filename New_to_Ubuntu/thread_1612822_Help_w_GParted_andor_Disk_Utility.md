---
title: "Help w/ GParted and/or Disk Utility"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Tholley on 2010-11-03
It has been a while since I have tried using either and for some reason I'm perplexed on what to do. It looks like I have made a mess of my partitions (a while back) and now want to clean it up some.
 
Here is a screen-shot of what I'm up against...
 
[ATTACH]174473[/ATTACH]
 
I want to add the 229 GB free space to the Win7 partition, but since it is part of the sda3 extended partition, I'm not sure if I can just re-size the Win7 partition to fill up the free space or not. I'm not at home to try just yet, but wanted to get some feedback, before I either try and fail, or accidentally erase a partition or data.
 
Basically I just want minimal partitions, 1 for XP, 1 For Win7, 1 for Ubuntu, and of course the swap file and the HP Recovery at the end.
 
Any advice would be appreciated!

---

### Post by Mark Phelps on 2010-11-03
You can't just move space from one partition to another, you have to do a shrink and then a grow -- one after the other.

You'll run into difficulty shrink the Extended partition because Ubuntu will have it mounted while you're running.

So, go to the distrowatch.com website, download and burn a GParted LiveCD, boot from that.

When that comes up, shrink your Extended partition TO THE RIGHT to take up the unallocated space.

Reboot -- this time, into Win7.

FIRST thing you do when back in Win7 is use the Backup feature to create and burn  a Win7 Repair CD. This is a MUST HAVE for anyone running a mixed Linux/Windows dual-boot system.

Once you have that done, open the Disk Management utility and grow the Win7 partition to take up the new free space -- and YES, despite what OTHERS will tell you around here, you CAN resize the Win7 OS partition from inside Win7.

---

### Post by Tholley on 2010-11-03
Thanks for the reply.

> So, go to the distrowatch.com website, download and burn a GParted  LiveCD, boot from that.

I'm in Ubuntu Live CD right now (same?), and it will not let me do anything to the extended partition (no options showing), I can extend the Ubuntu partition (to the left) to take up the space, but that is it. 


I have Win7 install and repair CD's already so that is no big deal.

---

### Post by Tholley on 2010-11-03
I re-booted into Win7 to take a look at computer Management, and it see's the free space but says it is part of an extended partition and if I delete it, then that partition will become inaccessible. 

So I will burn a Gparted Live Cd and try again what you said. 

Let you know...

---

### Post by wilee-nilee on 2010-11-03
> **Tholley said:**
> I re-booted into Win7 to take a look at computer Management, and it see's the free space but says it is part of an extended partition and if I delete it, then that partition will become inaccessible. 

So I will burn a Gparted Live Cd and try again what you said. 

Let you know...

Yeah the gparted cd is best really but you can use the version on a live cd. Also be sure to turn the Ubuntu swap off when resizing at any time. It sounds like your aware of using the W7 partitioner to resize W7 that is best really.

---

### Post by Tholley on 2010-11-04
The GParted CD worked great. I was able to do with it, what I wasn't able to do in Live CD.

Thanks!

> Also be sure to turn the Ubuntu swap off when resizing at any time.

I saw that while in the CD, but left it alone, what is that all about?

---

### Post by Mark Phelps on 2010-11-04
> **Tholley said:**
> I'm in Ubuntu Live CD right now (same?), and it will not let me do anything to the extended partition 

THAT'S why I told you -- specifically -- to download the GParted LiveCD!

However ... the Ubuntu LiveCD can work if you mess around with unmounting partitions and turning off swap -- but with the GParted LiveCD, nothing gets mounted, so you don't have to mess with that.

---

### Post by Tholley on 2010-11-04
Thanks Mark...
 
Now I know the difference between the 2 live cds.
 
Worked like a charm!

---

