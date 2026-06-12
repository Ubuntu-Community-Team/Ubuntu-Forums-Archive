---
title: "Ubuntu on fakeraid 0 alongside windows 7"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Somnophore on 2010-04-09
Hi, I'm interested in experimenting with other OS'es, and I wanted to try out Ubuntu, unfortunately, when I tried installing the previous version, it failed because it couldn't detect my raid array, and did some horrible things with it in the mean time. 

So I'd like to know, does the currect version support fakeraid out-of-the-box? Just a simple yes or no will do.. I quickly searched the forum, but I seem to get conflicting posts about the matter.

I don't mind trouble when I get it up and running, that's what experimenting is all about, but I want the installation itself to be as fluid as possible.. I don't mind it requiring my undivided attention, but I don't want to consult external tutorials and use 3rd party applications to get it running on my hardware. For example, I came across [**[this tutorial]**](https://help.ubuntu.com/community/FakeRaidHowto#Live%20CD%20Installation%20%28Ubiquity%20graphical%20installer%29) during my previous attempt, but I didn't really understand it at all..

So again, in short:
Will the current version (or perhaps the next big update) install on a fakeraid array?
I checked the releasenotes, and [**[this]**](http://www.ubuntu.com/getubuntu/releasenotes/910#Dmraid%20active%20by%20default%20on%20Desktop%20CD) seems to suggest it does, but I want to be absolutely sure.

Thanks in advance.

---

### Post by jvc26 on 2010-04-11
As an idea, how about booting up the livecd/live usb stick for ubuntu 9.10/10.04 beta and then see whether you can mount your already existing fakeraid device? If you can access the fakeraid device, then it looks like it can be recognised by ubuntu, which should mean you can install to it. If GRUB2 supports fakeraid, then you could well be in business.

I can't say I've ever used fakeraid for exactly the fact its not a real raid. For linux only I use software raid, (assuming I have the sys resources) and for lin/win environments/where I have a bit more real estate, I use the old Dell PERC raid cards (pick them up for ~£30 on ebay) with more RAM for hardware RAID - a much better option than fakeraid.

Il

---

### Post by J V on 2010-04-11
And if he can't it gets fried again...

I think software raid arrays are support out of the box now, but you can't be too careful, time to ask wikipedia...

---

