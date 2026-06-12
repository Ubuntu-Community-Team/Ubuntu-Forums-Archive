---
title: "Please help! Constant crashing..."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by JumpJump123 on 2009-12-01
Hi, I need help. I have Xubuntu installed (from Ubuntu) on an old PC - 256MB RAM, 2.4Mhz processor. Initially it worked fine, faster than I could have imagined. But increasingly it started crashing, sometimes when a lot of processes were running, but more and more often for no apparent reason at all. It just freezes and I'm forced to reboot.

It's becoming more and more frequent. I've done a Memory Test and didn't get any errors.

This absolutely NEVER happened under Windows(XP), not once.

Any ideas?

---

### Post by JumpJump123 on 2009-12-01
Also - the same thing happens when I run in Gnome.

---

### Post by teward on 2009-12-01
First thought:  Use the "edit" button rather than posting continual updates to your thread unless responding to someone.

Now to the actual question.  Is it at all possible your processor can't handle the load of lots of processes at once?  Because processes eat up CPU resources, and not just RAM.  You said it was a 2.4GHz processor.  What kind of processor?  Intel Pentium?  Intel Celeron?  AMD?  Intel?  More info, please.

---

### Post by JumpJump123 on 2009-12-01
Pentium 4.

I can't see that the problem is the processor when Windows never crashed once, even under serious strain. Plus, it crashes when very little is happening, too.

I'm leaning towards overheating, but it's a guess at best.

---

### Post by JumpJump123 on 2009-12-01
Anyone?

It's crashed about 5 times since.

---

### Post by Julita on 2009-12-02
In order to understand what freezes your system, it could be useful to type in the terminal 
```
top
``` (whenever it is possible, of course) I had the same problem due to the mysterious update-apt-xapi process that froze my entire system. The solution was to disable it entirely:
```
sudo chmod 644 /etc/cron.weekly/apt-xapian-index
```

---

### Post by beblasl on 2009-12-04
For some reason, Ubuntu causes the processor to heat up! I've had the same problem with my old eMachines W2646. 2.6 Ghz Celeron. I had to take a side panel off the tower and put a desk fan to blow air over the cpu. It's worked fine, so far & I didn't have this problem in XP either. I hope that helped!

---

### Post by JumpJump123 on 2009-12-04
Thanks a lot I'll give that a go, it's getting very frustrating.

---

### Post by Terl on 2009-12-04
> **JumpJump123 said:**
> Thanks a lot I'll give that a go, it's getting very frustrating.

Can you give more specs on your pc?  What gfraphics card do you have and, more important, is it a separate card or is it an on-board card that shares ram?  If it is the latter it cuts into your 256MB.  If it is separate, your card could be overheating causing the crash.

Can you give an idea of what you have open/running when this happens?

---

### Post by Sir Jasper on 2009-12-04
Hi,

I suggest you right click a blank area on a panel, click Add New Item, click the first item Launcher and type gnome-system-monitor in the Command box, then click OK.

Now restart, and for now, close any running programs.

Tell us what it says under File Systems about Total and Available space.
Say, what it says under Resources about Memory and Swap
Tell us the details of the first 3 items under System.

Have a look at Processes:
click on the name column heading to sort and then click again - do you see zombie in the sleeping column?
Click on the CPU and then the Memory column headings to sort and note any large usage under each heading.

Then this System Monitor itself uses a lot of resource so close it.

My regards

PS Try opening your usual programs one at a time and check on Memory/Swap and Resources to see there are any interesting changes.

You could also add the CPU Graph to the panel as it is light on resource.

Added:

I was not aware of the suggestion immediately above when I posted this - so follow that line first or concurrently.

Further added:

There are, I am sure I have read, far more resource efficient ways to install Xubuntu/xfce than via the Ubuntu desktop. Someone may advise here, but if not try googling.

---

