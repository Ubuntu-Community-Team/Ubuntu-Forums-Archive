---
title: "Triple boot?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by robro on 2011-02-15
Hello ubuntu forums,
well, i have been looking at some other linux distros and i was wondering if it is possible for a triple boot?

I already have windows 7 and ubuntu maverick meerkat, and will it interfere with them?
What other problems could it cause?

Thanks for your help :) (I hope im not asking for too much help :))

---

### Post by hansolo4949 on 2011-02-15
Yes, a triple/quadruple/quintuple plus boot can be attained, but you have to watch your partitions. You can only have 4 partitions on a single hdd at any time, unless you create an extended partition and place partitions in it (I do not know the max partitions you can put in one extended partition). So you should be just fine. I actually know one person who has about 5+ oses booting on one computer. Good luck!

---

### Post by robro on 2011-02-15
Thanks for the fast response :)
alothough i dont have a lot of information on partions :lol:
is there some website that can teach me about it :)

---

### Post by wormyblackburny on 2011-02-15
That is the wonderful thing about Grub, it doesn't care how many or what kind of OS's you have, it will run them if you install them and their boot flags are active. On a side note, why triple boot? Use VMware or Virtualbox for the 3rd OS. I have Ubuntu10.4x64/Win7 dual boot. Both have VMware installed. I create the VM's in windows and then import the VM's in Ubuntu by going into the windows partition and finding the VM file. That lets me run the same VM regardless of which OS I am using as the proprietary and all changes I make to the virtual machine are seamless across Win7/Ubuntu.... :)

---

### Post by Megaptera on 2011-02-15
As an aside "How to install and boot 145 operating systems in a PC"
[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

The 145 systems are:-

3 Dos
5 Windows
137 Linux

---

### Post by robro on 2011-02-15
> **wormyblackburny said:**
> That is the wonderful thing about Grub, it doesn't care how many or what kind of OS's you have, it will run them if you install them and their boot flags are active. On a side note, why triple boot? Use VMware or Virtualbox for the 3rd OS. I have Ubuntu10.4x64/Win7 dual boot. Both have VMware installed. I create the VM's in windows and then import the VM's in Ubuntu by going into the windows partition and finding the VM file. That lets me run the same VM regardless of which OS I am using as the proprietary and all changes I make to the virtual machine are seamless across Win7/Ubuntu.... :)

That does seem like a thing to take into consideration, i might do that and see if everything works,
thanks for the idea :)

---

### Post by hansolo4949 on 2011-02-15
@robro, here is a (rather lengthy) tutorial on [partitions]("http://www.bleepingcomputer.com/tutorials/tutorial115.html").

@wormyblackburny: I would not recommend doing that if he wants to experience another Ubuntu flavor more than just casually, since, especially depending on what hardware you have, Oses in Vm's are usually pretty slow, or at least a lot slower than it would be on the actual hardware.

@megaptera, thank you for providing that tutorial, I will actually check that out. Sounds intriguing! I just hope I have a spare several terabyte hdd around....:D

---

### Post by wormyblackburny on 2011-02-15
> **hansolo4949 said:**
> 
@wormyblackburny: I would not recommend doing that if he wants to experience another Ubuntu flavor more than just casually, since, especially depending on what hardware you have, Oses in Vm's are usually pretty slow, or at least a lot slower than it would be on the actual hardware.


That is the only downside to VM's: the overhead of system resources that the proprietary OS uses. If you have a dual or quad core processor and 4+ gigs of RAM, it usually isn't an issue tho.

---

### Post by hansolo4949 on 2011-02-15
Yes, I know, I am actually a big fan of Vm's myself (but as much nowadays, because if I want to run an OS, I usually will just run it from livecd or install it:)). So, this is the million dollar question: do you want to use thwe third os regularly, or just as a curiosity, and use it once in a while? if the answer is 1, then tri-boot it. If the answer is 2, just run it in a vm. Hope that clears things up!

---

### Post by robro on 2011-02-15
> **wormyblackburny said:**
> That is the only downside to VM's: the overhead that the proprietary OS uses. If you have a dual or quad core processor and 4+ gigs of RAM, it usually isn't an issue tho.

hmm... i have 1 gig ram and no dual core :| TRIPLE BOOT IT IS :lolflag:

anyways thanks for the help and i will install the new os sometime this month (due to limitations of gigs per month i have to go to a free wifi place :lol:) hopefully it will go well and not screw up my hard drive :)

---

### Post by hansolo4949 on 2011-02-15
Glad we could help! have fun, and Enjoy Ubuntu! You know, if your Internet plan is limited, then you should order a free Ubuntu cd from[ here]("http://www.ubuntu.com/desktop/get-ubuntu/cds").

---

### Post by robro on 2011-02-15
:lol: I already have ubuntu but im going to install fedora next :) but do you if they have a cd to order, just wondering :)

---

### Post by hansolo4949 on 2011-02-15
Ah, whoops, kinda forgot about that :D. let's see fedora....time for a google search! Well, it looks like you will have to download it, since my rapid google search turned nothing up. Perhaps there is a 3rd party company that will send them for a fee if you want to go that way.

---

### Post by robro on 2011-02-15
I'm a freebie :lolflag:
Thanks for help though :)

---

### Post by Megaptera on 2011-02-16
> **hansolo4949 said:**
> @megaptera, thank you for providing that tutorial, I will actually check that out. Sounds intriguing! I just hope I have a spare several terabyte hdd around....:D

You're welcome :D

---

