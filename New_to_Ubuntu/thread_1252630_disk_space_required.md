---
title: "disk space required"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by fitgene on 2009-08-29
i was using vista in my laptop, now switched to ubuntu 9.04. i have done it dual mode with vista in 90 gb disk area and the second partition of 10 gb contains ubuntu. i doubt whether this space is enough for ubuntu to run smoothly considering future upgrades or if to increase the space is there a way without corrupting vista

---

### Post by mapes12 on 2009-08-29
I'm no expert with Vista but I have read on other post that there is a partition tool in Vista that should be used. Normally, I would use Gparted from a Live CD but others have commented that Vista doesn't like GParted.

---

### Post by oboedad55 on 2009-08-29
> **mapes12 said:**
> I'm no expert with Vista but I have read on other post that there is a partition tool in Vista that should be used. Normally, I would use Gparted from a Live CD but others have commented that Vista doesn't like GParted.

More or less what he said. It's best to use Vista's partitioning tool to shrink the Windows partition, after defragging of course. Then you can use Gparted to partition the free space for Ubuntu. I would go with 20 gigs if you have the space. Naturally, backup anything you can't stand to lose, just to be safe.

--Jon

---

### Post by Paqman on 2009-08-29
> **fitgene said:**
> i doubt whether this space is enough for ubuntu to run smoothly considering future upgrades or if to increase the space is there a way without corrupting vista

It's enough for the basic system and all the Ubuntu software you'll ever install, but you're likely to need a bit more space for your personal stuff in your /home folder. This goes double if you start using things like Wine that like to install massive fatso Windows apps into your /home.

---

