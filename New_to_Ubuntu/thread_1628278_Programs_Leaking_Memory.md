---
title: "Programs Leaking Memory"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Ana.Gene on 2010-11-22
Hello,

I've noticed that my programs seem to leak memory and that if they are logged on too long they start to eat away at the SWAP even thought all of the RAM is not used (in fact I may only be using 4 GIGs of 32 Gigs and for some reason it will steal some swap).

I notice this problem in two circumstances:
1) When running R (I have recently started doing garbage collection to help with this)

2) When I leave any program open over night (R, eclipse, Chrome).

I am running Ubuntu Lucid Lynx Server Edition and my machine has 64 bit architecture. I haven encountered this problem before but I am not sure why. I just restart the machine to fix swap issues, otherwise it becomes very slow.

Thanks for any help!

---

### Post by zadehas on 2010-11-22
I can confirm this issue on a Dell Optiplex 380 running Kubuntu 10.04. I get swapping although the RAM is far from being exhausted. As a workaround I do this on startup (as root):

```
$ swapoff -a
```

Which disables the swap altogether. You can make this permanent by disabling the swap partition, but I don't want to go that far, I'm still hoping for a more elegant fix, I don't really like this kind of hacking.

So if anybody else has a better idea...

---

### Post by The Real Dave on 2010-11-22
Perhaps [changing your swappiness will help]("https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?")? 

@Ana.Gene, you're running a server with 32Gbs of RAM, or just a madly powerful home PC? :O

---

### Post by oldos2er on 2010-11-22
You can adjust swappiness in /etc/sysctl.conf, with values from 0 - 100 (the default is 60). Add the line

vm.swappiness=10

to the end of the file, replace '10' with whatever value you wish.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by zadehas on 2010-11-22
I'll try changing the swappiness and post back here about how that worked out for me.

Thanks for the references.

---

### Post by oldsoundguy on 2010-11-22
browsers seem to be the biggest offenders.  FF had a big issue a couple months back that they seem to have corrected.  Also, Facebook is a really BIG offender repeatedly .. seems every time they do a tweak, things get muddy until they repair the leak!

I found a kill all apps and re install really works for me .. takes just a few seconds, but solves the frustrations.

---

### Post by zadehas on 2010-11-23
> **zadehas said:**
> I'll try changing the swappiness and post back here about how that worked out for me.

Thanks for the references.

I changed swappines to 10 from the default 60.

I can definitely confirm that the swapping is down and the system is more responsive. Also it looks to be better than just turning the swap off.

I wonder if the swappiness shouldn't be set to a lower value by default...

---

### Post by Ana.Gene on 2010-11-24
The thing is that I need the SWAP space. I write/run a lot of intensive programs on my machine and while I try to avoid going into SWAP space, the truth is that sometimes it goes there. 

I mean right now I restart it regularly to kinda fix the the problem, but I don't want to limit the capabilities of my program to use swap.

Are there more elegant solutions? OR better yet an explanation for this behviour?

Thank you

---

