---
title: "slow performance"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by twood2978 on 2009-09-15
I just installed ubuntu onto a dell optiplex GX50 w celeron 1GHZ CPU and 512 of ram, I also have a 80 gig HDD. I did a fresh clean install of Release 8.04 (hardy)

My problem is, everything seems fine, but it seriously lags in performance. everything opens but it is slow, system monitor shows that the CPU is running a 99 to 100%.

Now I know I am not linux savy, Im switching over from windows.  but shouldnt it work well with the hardware I have.

Any help or idea will be great.

---

### Post by Yannick Le Saint kyncani on 2009-09-15
> **twood2978 said:**
> system monitor shows that the CPU is running a 99 to 100%.

It should also tell you which process is eating your cpu.

---

### Post by Geoff918 on 2009-09-15
You seem new to Ubuntu, you haven't installed any new software, correct? No antivirus or the like? AV will drive performance into the ground (and mostly isn't needed on a Linux machine).

Let us know what process is taking the most CPU time from your system monitor.

---

### Post by twood2978 on 2009-09-15
well the only thing in the processes section of the monitor that shows the highest % is gnome system monitor at 9%. however if I run top from the termnal (found that command in the forum) it lists Xorg at 45% to as high a 70% then sys-mon at 9ish% then terminal at .7%

---

### Post by twood2978 on 2009-09-15
and no software whatsoever. the only thing i have done is install a wireless nic, and run the updates.

---

### Post by ~The~Killer~ on 2009-09-15
> **twood2978 said:**
> and no software whatsoever. the only thing i have done is install a wireless nic, and run the updates.
Welcome to my world. I have the same problem I opened 2 topics. 1st one 2 guys had a fight because dunno what and the other few replies without any help :lolflag: 
All you have to do is imagine yourself in 1990's and u'll be fine :P

---

### Post by twood2978 on 2009-09-15
what are you talkin about the 90's I still rock a mullet.

---

### Post by cariboo on 2009-09-15
@~The~Killer~

I had a look at one of your threads, I agree you weren't getting any help. If you have that happen in a thread again, use the report button, we should be able to get the thread back on track again.

---

### Post by abouzar on 2009-09-15
I had the same problem with hardy. I installed Jaunty (ubuntu 9.04) and everything is just working fine. The only point is that if your system seems to be slow, go to:

System--> Preferences--> Appearance--> Visual Effects

and then choose*** None***. This will highly improve the performance of your system. The visual effects will not work properly with your system as it is quite old.

You can even give it a try to minimize these Visual Effects in Hardy to check the performance.

> **twood2978 said:**
> I just installed ubuntu onto a dell optiplex GX50 w celeron 1GHZ CPU and 512 of ram, I also have a 80 gig HDD. I did a fresh clean install of Release 8.04 (hardy)

My problem is, everything seems fine, but it seriously lags in performance. everything opens but it is slow, system monitor shows that the CPU is running a 99 to 100%.

Now I know I am not linux savy, Im switching over from windows.  but shouldnt it work well with the hardware I have.

Any help or idea will be great.

---

### Post by Geoff918 on 2009-09-15
Okay, well Xorg is the window manager. So, it looks like something with your video card--or more to the point, likely your video driver/settings.

If you've enabled any "screen candy" you may wish to disable that. If you don't know what I'm talking about, I'll assume you haven't.

Secondly, what you may want to do is find out what your video card is. The two easiest ways are:

1) Check the Dell website for your computer model and find out

2) use Applications -> Accessories -> Terminal and enter the following
[INDENT]lspci and hunt for your video card
[/INDENT]
From with that data in tow, we can move on some more. :)

---

### Post by k33bz on 2009-09-15
> **twood2978 said:**
> I just installed ubuntu onto a dell optiplex GX50 w celeron 1GHZ CPU and 512 of ram, I also have a 80 gig HDD. I did a fresh clean install of Release 8.04 (hardy)

My problem is, everything seems fine, but it seriously lags in performance. everything opens but it is slow, system monitor shows that the CPU is running a 99 to 100%.

Now I know I am not linux savy, Im switching over from windows.  but shouldnt it work well with the hardware I have.

Any help or idea will be great.

Not everything well work as well out of the box the way it does with windows. There is alot of different aspects when it comes to this. Alot of it doing with reverse engineering. 

Out of curiosity what is graphics card?

---

### Post by dwasifar on 2009-09-15
> **twood2978 said:**
> well the only thing in the processes section of the monitor that shows the highest % is gnome system monitor at 9%. however if I run top from the termnal (found that command in the forum) it lists Xorg at 45% to as high a 70% then sys-mon at 9ish% then terminal at .7%
Just FYI: the reason you are not seeing the same results in System Monitor as in top (good idea to run that, by the way) is that by default, System Monitor shows you only processes you own.  Pull down View and choose All Processes, and you will see results more in line with top.

---

### Post by twood2978 on 2009-09-16
I have disabled the settings for visual effects. man did that help out alot! dropped CPU usage down to 35%! It also helped with screen ghosts(bits of previous windows still on the desktop after something is closed.) So i decided to test it out, firefox is still aliitle jerkly at times but usable. still not able to watch streaming video yet, however it will play a dvd very well.

---

### Post by tcchris on 2009-09-16
You may want to try xubuntu , ubuntu uses gnome desktop . Xubuntu uses xfce which is a little less functional but much faster on slower computers

---

### Post by twood2978 on 2009-09-16
From what i can tell it is a intel 810 onboard graphix card. what i hope to do is install a PCI card with s-video out so that it can be connected to the tv, the main purpose of this PC will be to watch steraming video and play dvd's for now.

---

