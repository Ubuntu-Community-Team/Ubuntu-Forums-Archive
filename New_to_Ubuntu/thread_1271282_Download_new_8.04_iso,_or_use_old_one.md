---
title: "Download new 8.04 iso, or use old one?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by japhyr on 2009-09-20
I have kept 8.04 on my old laptop, while using 9.04 on a newer laptop.  I want to install ubuntu on another old machine, and I want to use 8.04 because I am more familiar with it, especially on older machines.  I know if I install using the 8.04 iso cd I burned a year ago, I will have a bunch of updates to do after installing.  So I have a couple questions:

- If I download a new 8.04 iso, will I have fewer updates to do after the installation?  Are updates incorporated into LTS iso downloads, or do the iso's stay the same?

- If I am going to install 8.04 on a number of machines, is there any way to put the set of updates on a CD and install updates from that CD, to save bandwidth?

-Eric

---

### Post by slakkie on 2009-09-20
If you want to save bandwidth, download a new CD and install from there. You will have less updates to apply. You could use aptoncd as well.

How many machines are you planning to install Ubuntu on? You could also try to setup a local repo, so you are effectivly a private mirror..

---

### Post by Paqman on 2009-09-20
> **japhyr said:**
> 
- If I download a new 8.04 iso, will I have fewer updates to do after the installation?  Are updates incorporated into LTS iso downloads, or do the iso's stay the same?


Depends when you got your original CD. LTS disk images do get updated occasionally.

> 
- If I am going to install 8.04 on a number of machines, is there any way to put the set of updates on a CD and install updates from that CD, to save bandwidth?


There's a few different ways to do this. Probably the most straightforward would be to install onto one machine, patch it right up to date, then make a custom disk image to use on the others. You can do this using [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"). It's fairly simple to use, just create a disk image using the -dist option, then burn it to a CD and use it to do the rest of your installs.

The other option would be to clone your first install using a tool like [Clonezilla]("http://clonezilla.org/"), you can even clone multiple machines over your network simultaneously. Can be a bit of a faff to use, though.

---

### Post by japhyr on 2009-09-20
I think I will download a new iso, because it's been about 15 months since I downloaded the first one.  I'm sure that have been some updates in that time.

I have used remastersys before, and that is an excellent suggestion.   Thank you for the quick reply.

---

### Post by CatKiller on 2009-09-21
> **japhyr said:**
>  I know if I install using the 8.04 iso cd I burned a year ago, I will have a bunch of updates to do after installing.

You'll have a bunch of updates anyway.

The LTS releases get refreshed every now and then to incorporate some of the newer versions of packages. The current release is 8.04.3, which was made available in July. If you use this release (which is the current on the ubuntu.com site) you'll still have all the updates since then to do. I don't really know which will be quicker or use less bandwidth out of using your 8.04 and then doing updates or downloading 8.04.3 and doing updates. Feel free to take it as an opportunity for some scientific testing :)

If you're doing *lots* of machines, it's probably worth using the later image and having a local repository for the updates. If you're only doing a couple, it might not be worth traversing the learning curve.

---

### Post by mcduck on 2009-09-21
> **CatKiller said:**
> You'll have a bunch of updates anyway.

The LTS releases get refreshed every now and then to incorporate some of the newer versions of packages. The current release is 8.04.3, which was made available in July. If you use this release (which is the current on the ubuntu.com site) you'll still have all the updates since then to do. I don't really know which will be quicker or use less bandwidth out of using your 8.04 and then doing updates or downloading 8.04.3 and doing updates. Feel free to take it as an opportunity for some scientific testing :)

If you're doing *lots* of machines, it's probably worth using the later image and having a local repository for the updates. If you're only doing a couple, it might not be worth traversing the learning curve.

I'd say that there's never more updates than the size of the disk image itself, so installing with the old disk you have + downloading the updates would require less downloading than getting the new disk image + updates for that.

(and it should be also noted that *onl*y LTS releases get updated disk images, for normal releases the disks are always the same as they were at the time of the release)

---

### Post by louieb on 2009-09-21
If saving bandwidth is you main concern, spend a couple of bucks and order it from some someplace like linuxcd.org. Going to be a few updates since 8.04.3 was released but nothing like the ones you'll have installing from 8.04.

Occasionally I'll get CD from one of the online stores. Just like the looks. 

Get tired head sometimes looking at my chicken scratch magic marker writing on some CD. :P

---

