---
title: "Ubuntu single boot question."
date: 2009-01-20
forum: New to Ubuntu
---

### Post by jotremba on 2009-01-20
I was wondering if my computer would run faster if I were to remove windows and reinstall from a liveCD, this would give me the oppertunity to reformat my hard disk to something other that NFTS and dedicate my hard disk partitions. Also if anyone has any additional suggestions on the installation it would be pretty helpful as well.

---

### Post by eder.apt-get on 2009-01-20
It doesn´t matter if you have Win or not. Ubuntu will run smoothly in any case. 
You don´t need even to remove Win, unless you want to. For this, you can have a dual-boot system.
Give us more details of what you really want or need.

---

### Post by mcduck on 2009-01-20
Are you currently running Ubuntu installed inside Windows (with Wubi)?

In that case making a proper install would result in a small speed increase in everything that requires reading or writing to hard disk.

If you are using a normal dual-boot it makes no difference if you have Windows on another partition or not.

---

### Post by jotremba on 2009-01-20
So does the computer have different formats for the windows partition and the linux partitions or are they both the same???

---

### Post by drs305 on 2009-01-20
I don't think you will see a significant increase in speed. Using a native linux file format for your data might provide a bit of a boost but the OS was running on ext3 regardless. 

Scrapping NTFS will allow you to take full advantage of permissions but that will have a benefit only if you have multiple users on the machine.

If you are going to reformat everything then think about how you want to partition the drive. Some recommend a separate /home, which can be helpful if you want to retain your settings when you upgrade to a newer version (e.g. Hardy to Intrepid). Personally, I don't do that but do like to have a separate partition for all my data.

If you have been using linux for a while you probably have a good idea of how you want to partition it. If not, this site discusses partitioning considerations:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by earthpigg on 2009-01-20
assuming you ran defrag prior to partitioning, the existence of a windows partition will not slow your system down.

---

### Post by jotremba on 2009-01-20
Basically my computer is not running as smoothly as I would like with Ubuntu - I am going to reinstall it and I can pull everything I need off of windows pretty painlessly. If I am going to reinstall Ubuntu I would like to do it in the best possible way so I was thinking that a fresh format and LiveCD would work pretty good.

---

### Post by mcduck on 2009-01-20
> **jotremba said:**
> So does the computer have different formats for the windows partition and the linux partitions or are they both the same???

Linux uses it's own file systems and Windows uses it's own.

But if you installed Ubuntu using wubi, then the Linux filesystem is *inside* a windows filesystem, meaning that everything you read or write goes through two file systems (which slows disk access a bit).

The important question here is if you installed using Wubi or did a normal install to a separate partition.

---

### Post by jotremba on 2009-01-20
Its a normal install to a seperate partition. It is a huge memory hog and ubuntu has locked up on me twice now since I installed it. I have a 1.2ghz processor and 512mg's ram but it should be a little smoother than it is. I mean it runs XP pretty smoothly.

---

### Post by mcduck on 2009-01-20
What do you mean with "huge memory hog"? It's *supposed* to use all your RAM. Unused RAM will not give you any benefits, while caching recently used data to RAM will significantly increase performance.

Run "free -m" and read from the "+/- buffers/cache"-line to check how much of the  RAM is actually used.

If there's still some problem with RAM usage you should check what program is using it.

It's hard to say anything about lockups or performance without knowing what you were doing at the time, what (exact) hardware you are using and with what drivers etc.. The question is pretty much the same as "My windows crashed. Why?" ;)

---

### Post by jotremba on 2009-01-20
well thats a pretty good point man, well put. I really like ubuntu a whole lot better than any other OS I have used and I really want to get it to work well.

It broke while I was installing windows xp through virtualbox which I now realize is not something that my computer can not really do. And another time while installing limewire which also could be attributed something I may have screwed up during installation.

---

### Post by jotremba on 2009-01-20
*UPDATE*

I did a complete install when I got home from work and it is running really smooth and fast... I have been customizing my OS ever since.  Linux rules..

---

