---
title: "[SOLVED] Using a lot of memory but two programs"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-10
'Morning all, well for me it is morning.
I'm trying to work out why Ubuntu is using so much memory on my computer. I have two programs running - Firefox for the internet and System Monitor to see the usage, etc.
That tells me I am using 72.5% of my Memory and Swap is using 42%.
Surely this doesn't leave much for running an application?
Also, why are there over 100 processes listed as running, all except 1 or 2 are sleeping. Seems a lot of processes. I can't figure out which applications they belong to, they don't seem to have a name that is related to an application.
Cheers to everyone for their help so far.****

---

### Post by egalvan on 2008-12-10
> **thadacto said:**
> 'Morning all, .
why Ubuntu is using so much memory on my computer. I have two programs running - Firefox for the internet and System Monitor to see the usage, etc.
That tells me I am using 72.5% of my Memory and Swap is using 42%.

Also, why are there over 100 processes listed as running, all except 1 or 2 are sleeping. Seems a lot of processes. ****

What version of Ubuntu?

What desktop (gnome,kde,xfce)?

How much physical RAM is installed?

How large a drive?

How large is 'swap'?

For example, if you have 129Meg RAM, using 72% RAM is OK.
But if you have 4G RAM, using 72% RAM indicates something amiss.
Your high 'swap' usage usually indicates not enough physical RAM.

As for the processes, others will have to chime in.

ErnestG

---

### Post by kpkeerthi on 2008-12-10
[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by thadacto on 2008-12-10
**What version of Ubuntu?**
Hardy 8.04
**What desktop (gnome,kde,xfce)?**
Gnome 2.22.3
**How much physical RAM is installed?**
There is 512 Ram of which 64 is used by the graphics card
**How large a drive?**
I am running dual boot with XP on the same drive. Linux partition is 52 GB with 12.4 GB free space and Windows Partition 68 GB with 15 GB free space. Though from memory, I thought I had 40 GB for Linux and 80 GB for Windows. Possibly Ununtu is not reading correctly? I also have a 2nd HD of 40 GB (but Ubuntu tells me it's only 27.6 GB
**How large is 'swap'?**
423.6 MB

I see from many other posts that people are using much, much more RAM than 512 - 1 GB of Ram?

---

### Post by billgoldberg on 2008-12-10
Use "top" in the terminal instead of the system monitor and post the output here.

--

That being said, firefox can be a memory hog.

You could try a more lightweight browser like "epiphany-browser".

If you install the extras from synaptic, you can have an adblocker, mouse gestures, ...

--

Also memory prices are at an all time low.

You can pick up an extra 512mb ram bar for $20 or less. 

Your pc will be a lot faster.

---

### Post by thadacto on 2008-12-10
Hi billgoldberg
I was checking up what my Windows XP had to say - I have an 80 Gb hard drive which has 55 GB for windows and 21 Gb for "other" i.e. Linux.
Attached is screen shot of "top". Hope it is attached correctly - First time I've done that.

---

### Post by Tatty on 2008-12-10
Linux uses memory differently to windows.  After memory is freed up by an application Linux does not wipe the memory clear, it leaves the application loaded.  This is to speed things up the next time you open that application.

This results in lots of memory which is marked as available, but is being occupied by application data.  So it often appears that you have less memory available than you actually do.

Linux will only wipe over that data when another application needs it.

To see how much memory you actually have available run the command "free", and the free memory you have is : memory used - buffers/cache used

---

### Post by thadacto on 2008-12-10
Thanks for the explanation tatty

---

### Post by laceration on 2008-12-10
The operating system will use what memory you have, so just looking at what is available is not a good measure.
I don't know if Argentina is the quite the consumerist orgy like the usa, but I just got 2 gigs of hi-performance memory for $13 (after they send me a rebate).  A memory upgrade is a highly cost effective way to improve your computing experience.
System monitor is a resource hog.  Mostly in regard to using up cpu.  I do not leave it open unless I am using it and I have a fairly beefy computer.  I keep an eye on things by the system monitor applet in the gnome-panel.

---

