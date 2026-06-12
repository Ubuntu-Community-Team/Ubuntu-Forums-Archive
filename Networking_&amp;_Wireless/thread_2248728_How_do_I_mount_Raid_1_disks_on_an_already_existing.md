---
title: "How do I mount Raid 1 disks on an already existing Ubuntu server?"
date: 2014-10-16
forum: Networking &amp; Wireless
---

### Post by bengy103 on 2014-10-16
Hi All,
I've just got a (ubuntu) server up and running for the first time ever on my old ex-NAS computer which won't boot off a usb. Disk wise it has a 200GiB (SDA) for the server, on a 20GiB partition, I believe that there is a swap file in there as well, and two 500GiB (SDB+SDC) hard drives. At the time of installation I set up these two as Raid 1 (I think because I haven't seen them - softwarewise - since).

I need to set these up for my storage notions, which I suspect means that I need to mount them. I don't want to trash what I've done so far and I'm sure this has been asked a dozen times before but I've been googling for the last 16 hours and all the Raid references are about setting up the operating system on the Raid disks. That's not what I want and this old motherboard I'm using has been passed by by all but server installations.

I would be so grateful if someone can point me toward the solution. In an ideal world that would be on Youtube, because that's what I used to get my server up and running.

I didn't understand the Ubuntu server explaination of setting up at all.

At installation time I set up the server using Ubuntu 12.04 server and did updates and upgrades yesterday, which might mean I'm on Ubuntu 14.04 but I'm not sure.

Sorry to be so vague but to be honest I don't know enough about server stuff to give a more succinct description of my problem.

For anyone thinking of having a go at setting up a server for the first time I can recommend it. I've even got a Print server going so everyone can print from any computer to any printer. It's brilliant. Media next (hopefully).

regards,

brawd.

---

### Post by weatherman2 on 2014-10-16
What kind of RAID - hardware or software?

It could be you need to re-build the RAID with the mdadm command, then mount the array, but if the array wasn't originally built that way, it may not work.  Instead, you may need to re-mount the array in the original NAS and copy the data over to another location first, then move the drives, make a new RAID array on them, and copy the data back.

---

### Post by bengy103 on 2014-10-16
It's a software raid.

The disk that FreeNas Ver. 0.7.2ish was on died over a couple of days and my old banger couldn't accept the new FreeNas. It won't boot off a usb.
I did manage to copy the important files (family pics) to another hard drive so that free-ed up the two 500s for a server RAID. Then they got RAIDed and reformatted during the server setup so there is nothing on them. I'm happy enough trying your suggested rebuild and mount but I don't know how to do either and I can't find anything on the web concerning drives seperate from the drive holding the server program, probably I don't know enough about servers to phrase a tidy question. The web is full of advice on how to build a RAIDed server with two harddrives.
 I was hoping someone would tell me how to mount them so I could see them as storage from other computers. 

Will they be considered as one disk because they are in a RAID array or as two seperate disks?

---

### Post by weatherman2 on 2014-10-16
If they were part of a RAID array, they will be considered as one disk. But I'm not clear on exactly what you did, with what.  You have two 500GB disks that were part of a RAID array on your FreeNAS box, but you formatted those drives during Ubuntu installation?  If you did that, then your data is gone - don't even bother trying to recover anything.  Or are there two other disks that had the RAID?  Or are you simply trying to build a new RAID in Ubuntu?

Was it a RAID mirror (e.g.. RAID 1) or a stripe (RAID 0 - for speed)?

If it was a RAID 1, you may be able to re-build the array with just one of the disks.  But, I'm not sure you'd build it if it came from a FreeNAS build.  It could be just the mdadm command.  Once you do that, you'll need to mount the filesystem - and if it's a FreeBSD (e.g ZFS) filesystem, you'll need to handle it that way.

You might post this on a FreeNAS forum, too.  But I'm sure someone else has needed to move a FreeNAS RAID array to Linux.  Focus on Linux, not Ubuntu, as your search, because you'd build the array in the same way under any Linux distro.

---

### Post by bengy103 on 2014-10-17
Hi Weatherman,
Thanks for your interest and apologies for my ineptitudel.
Firstly I have recovered the data so I'm not trying to salvage anything more from those two 500 drives, therefore they were spare.

That being the case I decided to set up a ubuntu 12.04 server using the following configuration:-

A 200GiB HDD with the server software on. I partitioned that disk at 20GiB where I let the setup program automatically configure itself onto that 20GiB partition. So there's 180GiB spare on that Disk, not that I know how to get at it yet but it's not a priority. Probably my first mistake.

Two 500GiB HDD were configured as software RAID 1 - which should be the RAID mirror in your query above - during the server setup routine. I didn't know I was supposed to consider the mount point for these at the time. Probably my second mistake.
Now if I can find out how to automatically mount them when I restart my server I'll be well on my way. I say restart because I've found out that I can do all sorts of things, media servers, postman,,,,,,etc., hence that will require a few restarts no doubt.

You've given me a some good guidance, search using mdadm and linux servers as keywords, for which I am extremely grateful. But please don't let me put you off trying to help a guy who has probably bitten off more than he can chew at this moment.

I hope I've cleared up my previous shabby explanation of my situation.

regards,

brawd.

---

### Post by weatherman2 on 2014-10-17
(The fact that they were previously in your FreeNAS box threw me - sorry.)

It sounds like you setup the new array during installation but didn't choose a mount point?  Then you may only need to mount the array in your /etc/fstab file.

Try this in a terminal:

```
sudo mount /dev/md0 /mnt
```

Does that work?  If not, either the array was never built or no filesystem was created.

Is there an existing file /etc/mdadm/mdadm.conf ?  That should contain the definition of the array.

You can also create a filesystem this way:

```
sudo mkfs -t ext4 /dev/md0
```

assuming it has been created and is up via mdadm.

---

### Post by weatherman2 on 2014-10-17
[FYI, this thread should probably be moved e.g. to "Hardware" as it really has nothing to do with Networking & Wireless.]

---

### Post by bengy103 on 2014-10-17
OK

Just before that happens I worked my way through the advice on this link
[http://www.cyberciti.biz/faq/linux-creating-software-raid-one-arrays/](http://www.cyberciti.biz/faq/linux-creating-software-raid-one-arrays/)
and my RAID array looks good. Not that I can see it yet on other machines but it gives me confidence.

Many thanks weatherman2, your a prince.

regards,

brawd.

P. S. How do I move a thread or will someone else do it?

---

### Post by weatherman2 on 2014-10-17
Since you had to mention "see it yet on other machines," now we can call this a thread about networking. So you can leave it here. ;-)  

If you want to share a folder on your local network in Ubuntu 12.04, you can use something called Samba.  To do simple sharing, you can short-cut doing a Samba setup and try right-clicking on any folder you are browsing and choosing "Sharing Options."  (This assumes you have mounted the array somewhere.)  The first time you may be asked to install some packages.  You can use guest sharing if you don't care to password-protect the share and make it easy.

You may also need to set permissions on the filesystem in the share to be writeable by sharing users, otherwise you may get permission errors.

---

### Post by bengy103 on 2014-10-23
OK, well it's been an epic.
I've given up trying to install the server on one drive and install a Raid 1 on another matched pair of devices because I simply don't have the knowledge to adjust all the parameters. There is of course a wealth of information to be had by googling but none so far has worked within any reasonable time limit. No doubt it's out there somewhere. It's also complicated by the release of 14.04 with the slight, but obviously crucial, changes in configurations. I failed to nail this problem.

The upshot is that I used GOGUDA55 on youtube to set up a raid 1 array and (probably) kissed goodbye to 200GiB of storage on a spare IDE drive that I had intended to use to store all the server software. Ah well.

The current position being that Windows (all versions) is cruising my Plex media server and storing files in available folders, while my Ubuntu flately refuses to have anything to do with my home server setup. So I guess I'll be busy all next week.

I'll have to mark this thread as "Solved" though really what it should be is "Abandoned".

My thanks to weatherman2 for giving your time helping me.

regards,

brawd

---

### Post by bengy103 on 2014-10-23
I feel I must make a final observation here.
Windows cruising, as mentioned above.
I have Ubuntu 14.04 server installed on a remote box.
I have Ubuntu 12.04 LTS installed on my day to day computer.
They don't hold hands without being properly introduced.

brawd.

---

