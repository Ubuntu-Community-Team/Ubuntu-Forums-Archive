---
title: "Making a SD card a virtual drive."
date: 2009-05-29
forum: New to Ubuntu
---

### Post by apfroggy0408 on 2009-05-29
I've been searching for quite a while and cannot find anything on turning an sd card into a virtual hard drive. I've installed ubuntu onto my EEE PC that only has 4gb's of internal memory but I've got a class 6 8gb sdhc card that I would like to turn into a virtual hard drive. Please point me in the right direction.

---

### Post by Paqman on 2009-05-29
As long as the card reader on your EEE is working ok you just just stick the card into it. It'll show up as a removable drive on the desktop.

---

### Post by apfroggy0408 on 2009-05-29
> **Paqman said:**
> As long as the card reader on your EEE is working ok you just just stick the card into it. It'll show up as a removable drive on the desktop.

All that good stuff works fine but like on windows you cannot completely install programs onto removable drives and cannot find anything on how linux controls something of the sort. I want my sd card to be read like my internal hard drive.

---

### Post by Paqman on 2009-05-29
> **apfroggy0408 said:**
> All that good stuff works fine but like on windows you cannot completely install programs onto removable drives and cannot find anything on how linux controls something of the sort. I want my sd card to be read like my internal hard drive.

Ah right, so you want to actually mount parts of your filesystem onto the card?

That's completely doable. For example: it's very common to mount /home on a seperate drive or partition. The principle for adding any particular part of the filesystem to a new mount point is the same. I'd suggest starting with /home, since there's already plenty of documentation about how to do it, and /home can take up a fair bit of space. Plus it would give you the bonus of being able to format the rest of the filesystem (eg: for an upgrade) without destroying your settings and data in /home.

---

### Post by apfroggy0408 on 2009-05-30
> **Paqman said:**
> Ah right, so you want to actually mount parts of your filesystem onto the card?

That's completely doable. For example: it's very common to mount /home on a seperate drive or partition. The principle for adding any particular part of the filesystem to a new mount point is the same. I'd suggest starting with /home, since there's already plenty of documentation about how to do it, and /home can take up a fair bit of space. Plus it would give you the bonus of being able to format the rest of the filesystem (eg: for an upgrade) without destroying your settings and data in /home.

Thanks, that's all I wanted, to be pointed in the right direction.

---

### Post by Paqman on 2009-05-30
> **apfroggy0408 said:**
> Thanks, that's all I wanted, to be pointed in the right direction.

No problem.

[Psychocats]("http://www.psychocats.net/ubuntu/separatehome") has some good information on how to do this without reinstalling. However, depending on how quick your system is to set up you might just find a reinstall is easier. Up to you.

You can probably skip right over all the partition resizing stuff in that tutorial, since by having two seperate disks you've effectively got partitions already.

Another thing to bear in mind: cheap flash storage like SD cards have a limited lifespan. If you're going to keep your data there, make sure to do regular backups. If you've got a device you can backup up to on a network you could automate this and it'll be zero hassle. Take a look at rsync and anacron for a slick way to do that kind of thing.

---

