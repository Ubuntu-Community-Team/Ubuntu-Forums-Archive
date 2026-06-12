---
title: "Put &quot;Home&quot; on a diet? Need to purge files"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by pottzie on 2010-02-21
I started another thread yesterday abut problems I'm having with the capacity of my hard drive. I'm new and naive when it comes to computers, and the "problem" I'm having is compounded by, of all things, the fact that Ubuntu may be working TOO well!
 I downloaded another iso, to try out on another computer. While I'll spare you the grief of that (Debian's "set up your computer remotely" nightmare), my Ubuntu set-up went into a quasi-meltdown half way through the download. I only have a 10 gig hard drive, and half of it is used for another O.S., so 5 gigs is all I have. The "problem," if you will, is that until now Ubuntu has chugged away like that was plenty, and had I not tried to download the equivalent of the library of Congress, I'd have never known just how cramped the hard drive is. 
 My question is: is there a way to get the packge manager to weed out my system? Computer janitor found a few things, but the Disk Usage analyzer still says 100% of total file system capacity. Is there a painless way of purging the excess, including the k3b download that aborted when it "hit the wall" because of my small system?

---

### Post by 2hot6ft2 on 2010-02-21
Disk Usage analyzer tells you how the files in your file system are distributed NOT the amount used on your partition/drive. To find out how much space is actually being used run this in a terminal
```
df -h
```
The second line will say something like this
> /dev/sda8 40G 9.9G 28G 27% /
40G is the total space on the partition
9.9G is the amount of data on the partition
28G is the free space
and
27% is the amount of space used by data on the partition

There is a link to cleaning up the file system to make more space in my sig below.

---

### Post by halitech on 2010-02-21
If you only have 5gig to work with, you may want to do a minimal install from the Alt install cd and then add just the packages you need/want

---

### Post by 2hot6ft2 on 2010-02-21
> **palluvinny said:**
> thanks. just checked mine too. around 47% occupied. Is it free space or occupied space?
That would be 47% used by data. Leaving 53% free space.

---

### Post by bodhi.zazen on 2010-02-21
> **pottzie said:**
> I started another thread yesterday abut problems I'm having with the capacity of my hard drive. I'm new and naive when it comes to computers, and the "problem" I'm having is compounded by, of all things, the fact that Ubuntu may be working TOO well!
 I downloaded another iso, to try out on another computer. While I'll spare you the grief of that (Debian's "set up your computer remotely" nightmare), my Ubuntu set-up went into a quasi-meltdown half way through the download. I only have a 10 gig hard drive, and half of it is used for another O.S., so 5 gigs is all I have. The "problem," if you will, is that until now Ubuntu has chugged away like that was plenty, and had I not tried to download the equivalent of the library of Congress, I'd have never known just how cramped the hard drive is. 
 My question is: is there a way to get the packge manager to weed out my system? Computer janitor found a few things, but the Disk Usage analyzer still says 100% of total file system capacity. Is there a painless way of purging the excess, including the k3b download that aborted when it "hit the wall" because of my small system?

It is easier to start with a minimal install and add only what you need. You can try Crunchbang , lubuntu , or if you like Zenix.

If you install Zenix, and cancel the download and installation of the language packs, it takes much less HD space.

[http://zenix-os.net/](http://zenix-os.net/)

---

### Post by spiky001 on 2010-02-21
have you tried removing programs you dont use games word etc only a thought

---

### Post by snowpine on 2010-02-22
8gb is the [recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements") for a full install of Ubuntu.

Storage is cheap these days; Newegg has 80gb drives for $34, 1TB drives for $79, and 8gb flash drives for $19.

If for whatever reason you are stuck with 5gb and no possibility of upgrading, I'd recommend a "lightweight" Ubuntu (Xubuntu, Lubuntu, CrunchBang, minimal install, etc.) but even then you will not have much room to install applications or create documents.

---

### Post by undecim on 2010-02-22
I agree with everyone else. A minimal install would suit you well if you don't care to upgrade from 5GB, but make sure you are prepared to deal with nothing more than a text interface until your system is set up.

If you want to do this without formatting, it is possible. If you are going to reinstall anyways, then the only thing you would be risking by trying this is your time. If it goes smoothly, it should save you a lot of time downloading and upgrading, but if it doesn't, then it just cost you some time.

If you want to try doing that, let me know by posting here and I will help you out.

---

### Post by bodhi.zazen on 2010-02-22
Zenix uses 1.5 Gb of HD space (you need to skip installation of the language packs).

Plenty of space for light weight apps, if needed.

---

