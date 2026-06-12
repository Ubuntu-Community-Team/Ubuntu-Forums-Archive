---
title: "RAID media PC"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by hellomoto on 2009-08-17
Hey guys,

Haven't got a problem as such, just in search of some knowledge!

So in the past 3 days, i built a PC of old parts i found around the house, put it under a wide-screen TV, reconfigured Xorg to enable s-video on my graphics card and got ssh working between ny desktop and this media PC i have created. It has been a great experiment and im very proud of what I have accomplished.

My end goal is to have a big media server in the house. holding all my data and running mythbuntu backend and then aprox 4 media PCs running mythbuntu front end  at various points around the house. I am aware this is a massive undertaking for me and something i look 4ward to doing. 

However this brings me to my question im looking at having aprox 1-2tb of space on the media server. I could just go and get a couple of 1tb hard disks but how hard is it to run a RAID setup on ubuntu? I know nothing of RAID or running servers but I do like the idea of being ablt to easily expand my media server and having most of my data safe if one of the HDs were to fail. 

Anyone got any advice, or know where i can find more information. 

Thankyou!

---

### Post by Shig on 2009-08-17
Hi There

Software RAID in Linux is great, for your setup I would recommend RAID-5 if you can afford 3 drives, 3 1TB drives in RAID-5 will give you 2TB of space, but if one drive dies, you will not lose data, if two drives die, you will. 

RAID-5 is good because once you have forked out for 3 drives, you can add more, so 4 1TB drives in RAID-5 will give you 3TB, you still only lose one drive worth of storage capacity and retain the ability to rebuild a failed disk. With RAID-5 you basically lose one drive in the array to parity data which is used to rebuild the array after a disk fails (although the partity is actually stored on all disks in the array, so any disk can fail).

A good explaination of various RAID levels in general is the [RAID wikipedia article]("http://en.wikipedia.org/wiki/RAID"), read it before you start to get serious about using RAID as it helps a lot to understand the concepts before you start tinkering.

For a good guide on setting up software raid on mythbuntu, [see here.]("http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/")

I run a very similar setup to the one you are describing, and setting up RAID and Mythbackend is the least time consuming of all activities. Just wait until you start tweaking your graphics card to get 1080p over HDMI, start messing with ALSA to get Optical audio... It's all a lot of fun and very rewarding.

Have fun!

---

