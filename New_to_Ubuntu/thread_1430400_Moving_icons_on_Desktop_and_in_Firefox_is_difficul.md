---
title: "Moving icons on Desktop and in Firefox is difficult"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by mistypotato on 2010-03-15
Is it just my computer?

When I try to move folders or icons on the Desktop to new locations there is a significant lag.

The lag is very serious.  To the point that it is very difficult to move icons or folders form one place to another on the Desktop or on the Firefox favorites bar.

In Windows, the movements are fast, fluid and accurate.

Is anyone else having this problem in Ubuntu 8.10 or can you move your icons around easily as in Windows XP?

thx

---

### Post by quadproc on 2010-03-15
> **mistypotato said:**
> Is it just my computer?

When I try to move folders or icons on the Desktop to new locations there is a significant lag.

The lag is very serious.  To the point that it is very difficult to move icons or folders form one place to another on the Desktop or on the Firefox favorites bar.

Is anyone else having this problem in Ubuntu 8.10 or can you move your icons around easily as in Windows XP?

thx

I used to run Ubuntu 8.10 and did not see the problem that you described.

To help troubleshoot it, we will need more information.  If you could summarize the following, it would help:

32 or 64 bit processor(s)?
How many and what kind of processor(s)?
Type and manufacturer of graphics card?
Which driver is in use for the graphics card?
Amount of RAM in the main computer?
How much swap space is allocated on disk?
How much memory is in use?
How much swap space on disk is in use?
How busy are your CPUs (you can use "top" or the System Monitor to get this)?

The System Monitor is a good tool for examining resource usage since it tells you the present busyness of the major parts of the system.

Could you perhaps be running from a Live CD?  If so, that will be a lot slower than a version which is installed on disk.

quadproc

---

### Post by cerealtx on 2010-03-15
that sounds like a RAM issue as stated above, open sysmon and see how full your mem gets, firefox can be a resource hog, but if you have nothing open and still get lag with moving icons something is wrong, might check your startup files or just what you have running every boot and cut down on unneed programs

after rethinking possible wrong drivers for gfx card could cause this issuse aswell

---

### Post by mistypotato on 2010-03-16
32 or 64 bit processor(s)?
**AMD X2 64 5200**
How many and what kind of processor(s)?
**2 processors**
Type and manufacturer of graphics card?
**Nvidia 8900 GTX**
Which driver is in use for the graphics card?
**Nvidia Proprietary Linux Driver from Synaptic Package Manager**
Amount of RAM in the main computer?
**4 GB**  (3 useable)
How much swap space is allocated on disk?
**2 GB**
How much memory is in use?
**604MB of 3.0GB**
How much swap space on disk is in use?
**0% of 0**  (huh?)
How busy are your CPUs (you can use "top" or the System Monitor to get this)?
The cpu's are not taxed...they are running around 2% - 40% variably.

---

### Post by Sir Jasper on 2010-03-16
Hi,

You are a long-standing forum member with many beans so it may help to know if these are long-standing problems or, if recent, do you have a new computer or any other major change(s).

I just googled and found there was a serious (perhaps similar) bug re moving Firefox bookmarks using v 3.0 but that involved Ubuntu 8.04 not 8.10 - and in any event there no reference to your Desktop problem.

I expect you have used the Update Manager and probably had automatic File System Checks (every month or 30 or 40 boots) but perhaps an FSCK using a live disk with the auto fix setting might help (if you have not already tried that).

Your specs seem far more than adequate and I have no experience with your problems (except for an occasional crash when moving Firefox Bookmarks which I am now able to avoid by using the Organise Menu).

My regards

---

### Post by andrewthomas on 2010-03-16
> **mistypotato said:**
> 32 or 64 bit processor(s)?
Type and manufacturer of graphics card?
**Nvidia 8900 GTX**
Which driver is in use for the graphics card?
**ATI Proprietary Linux Driver from Synaptic Package Manager**

 Why are you using an ATI driver for a Nvida card?

---

### Post by mistypotato on 2010-03-16
> **andrewthomas said:**
> Why are you using an ATI driver for a Nvida card?

that was a typo.  I corrected it thx.


I doubt an ATI driver would actually work with my Nvidia card

---

### Post by quadproc on 2010-03-16
> **mistypotato said:**
> 32 or 64 bit processor(s)?
**AMD X2 64 5200**
How many and what kind of processor(s)?
**2 processors**
This sounds good
> 
Type and manufacturer of graphics card?
**Nvidia 8900 GTX**
Sounds good
> 
Which driver is in use for the graphics card?
**Nvidia Proprietary Linux Driver from Synaptic Package Manager**
Sounds good (correction noted)
> 
Amount of RAM in the main computer?
**4 GB**  (3 useable)
 OK for size, but I am curious why 1/4 of it isn't available
> 
How much swap space is allocated on disk?
**2 GB**
This is not a problem for the moment, but your swap space should be at least as large as your RAM size.  This is because the hibernate function copies all of RAM into swap for later reawakening, and swapping may turn into thrashing if your applications do need to swap.  Too small a swap space will cause difficulties using some features.
> 
How much memory is in use?
**604MB of 3.0GB**
This is quite reasonable and very consistent with my observations on a 64 bit version 9.04 system
> 
How much swap space on disk is in use?
**0% of 0**  (huh?)
Yes, since you haven't filled up the RAM then there is no need to swap so it will be zero.  Also, there won't be any slowdown due to swapping or thrashing.
> 
How busy are your CPUs (you can use "top" or the System Monitor to get this)?
The cpu's are not taxed...they are running around 2% - 40% variably.OK, this sounds good.

You have eliminated all of the obvious problems that I might have suspected.  At this point I am really guessing, so, for what it is worth, here are some thoughts.

If you can connect to the interrupt lines in your system with a scope or an event counter then you get an interrupt rate.  This should be reasonably low, perhaps less than about 50 interrupts per second.  If this rate is high then you would need to figure out why (perhaps someone doing a "denial of service" attack against your system).

The next suspect area would be the graphics board and driver.  Could you temporarily change either the driver, the board, or both?  Since the reported slowness is related to changing images displayed on the screen then a logical place to look would be the software and hardware that transfers data between main computer memory and the graphics board.

Is your Ubuntu installation from the Live CD or from the alternate CD or some other source?  If it came from the alternate then there might be a configuration issue.

I should ask if you are using any of the fancy features in the Appearance Preferences such as wobbly windows?  If you are running any visual effects then you could temporarily turn that selection to none to see if that makes a difference.  What is your Desktop Background and your Theme (both accessible by right clicking on the desktop background and selecting the change background button)?

At this point I am running out of ideas.  I will think about it some more and post anything that may occur.

quadproc

---

### Post by mistypotato on 2010-03-16
wow.
thx for the indepth help :KS

The only thing that seems to possibly apply is that I think I have compiz (or something like that) installed for enhancing the desktop.

Maybe I'll turn that off and see if it corrects the problem.

---

### Post by tgalati4 on 2010-03-16
Sounds like a software-rendering vs hardware graphics acceleration.  It could be a bug in the proprietary driver.  Check for errors in:

cat /var/log/Xorg.0.log

and

cd
cat .xsession-errors

---

