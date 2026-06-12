---
title: "Why ubuntu hangs all the time!"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-26
I'm so angry, my ubuntu 9.10 still hangs even when reinstall it, ubtuntu 10.4 does that as well, when i'm browsing or working with gimp or other apps, it stops me from continue working and the colors turn black and white for a moment.
what cause this problems?

regards

---

### Post by khelben1979 on 2010-06-26
It could be problems with your computer hardware. Dust in the case causes instability no matter what operating system and software you are using. Have you checked it out?

Some information about the computer hardware would be good to know to be able to analyze how that looks like as well.

---

### Post by libssd on 2010-06-26
> **MBG1987 said:**
> I'm so angry, my ubuntu 9.10 still hangs even when reinstall it, ubtuntu 10.4 does that as well, when i'm browsing or working with gimp or other apps, it stops me from continue working and the colors turn black and white for a moment.
what cause this problems?

regards
What is your hardware configuration? Even on a measly netbook, I have never experienced delay issues with 9.04, 9.10, or 10.04.

---

### Post by eltonw on 2010-06-26
> **MBG1987 said:**
> I'm so angry, my ubuntu 9.10 still hangs even when reinstall it, ubtuntu 10.4 does that as well, when i'm browsing or working with gimp or other apps, it stops me from continue working and the colors turn black and white for a moment.
what cause this problems?

regards

Before you blame the OS, and the fact that this happens with various applications leads one to believe that this may be a problem with your video card. 

[COLOR="Red"]It pays to give a description of your hardware setup when posting problems.
[/COLOR]
It could be something as simple as a loosely seated video card, or short-circuiting caused by dust or cigarette smoke. Other possibilities may be shorting caused by loose wires or overheating.

---

### Post by MBG1987 on 2010-06-26
> Some information about the computer hardware would be good to know to be able to analyze how that looks like as well.

1GB of RAM
2.2GHz Dual core CPU
160 GB hard disk 
256GB Intel Corporation 82G33/G31 Express Integrated Graphics Controller
thanks

---

### Post by oldsoundguy on 2010-06-26
just dropping this in .. I had boot problems on one machine.  Found if I disconnected the FLOPPY DRIVE, the issue went away.  NOT that way on other Ubuntu boxes .. just one of them.  NOT A CLUE as to why, but saw a mention of it somewhere on the forum so gave it a shot.

---

### Post by khelben1979 on 2010-06-26
> **MBG1987 said:**
> 1GB of RAM
2.2GHz Dual core CPU
160 GB hard disk 
256GB Intel Corporation 82G33/G31 Express Integrated Graphics Controller
thanks

By looking at these specifications I can see that's more than enough to be able to handle a Ubuntu system without any problems such as you describe, so you or some one else (depending on your skills) should take a look at your computer hardware to see how it looks like inside.

---

### Post by mörgæs on 2010-06-26
You could try having **top** running while working on the machine. This will tell if a particular application is overloading the CPU.

---

### Post by MBG1987 on 2010-06-26
> By looking at these specifications I can see that's more than enough to be able to handle a Ubuntu system without any problems such as you describe, so you or some one else (depending on your skills) should take a look at your computer hardware to see how it looks like inside.
yes, I thing it's hard ware issue, i'll look into it tomorrow since i've a bit knowledge about hardware 
thank u again

> You could try having **top** running while working on the machine. This will tell if a particular application is overloading the CPU.

I've checked it, nothing over loading the cpu, off curse firefox taking the biggest cpu space lol

---

### Post by nhasian on 2010-06-26
> **MBG1987 said:**
> I've checked it, nothing over loading the cpu, off curse firefox taking the biggest cpu space lol

> **MBG1987 said:**
> when i'm browsing or working with gimp or other apps, it stops me from continue working and the colors turn black and white for a moment.

when an app is grayed out temporarily it is waiting for the CPU.  I know you said you checked top but what does top say when your app turns gray?

---

### Post by syamkumar on 2010-06-27
I am also having this problem (system hangs and needs hardware reboot)
my laptop is ThinkPad Z60t.. and i tried many distros based on ubuntu 10.04 here also same problem exists... and one more thing that i have to say is "The mouse pointer disappears when my laptop lid is closed and reopened in ubuntu 10.04 and it is working fine with ubuntu 9.10.....".

---

### Post by mörgæs on 2010-06-27
Then by all means, stick to 9.10. It is supported almost a year from now. 

There are many reports of this kind of problem in the fora, and often there is nothing one can do about it.

---

### Post by 3rdalbum on 2010-06-27
Check your memory. Run Memtest86 overnight. If it still doesn't report any problems and your computer hasn't crashed by morning, then run the memory benchmarks on Phoronix Test Suite to see if the system crashes then.

If you get any errors during Memtest86 or your computer crashes during the memory benchmarks, then try replacing your RAM.

Otherwise, faulty RAM will lead you on a wild goose chase; you'll be examining log files and scratching your head as to why a different program has caused the crash each time. Took me months to figure out.

---

