---
title: "[SOLVED] Questions about 32 vs 64 bit"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-05
So I have a 2.5GHz quad core with 4GB ram, and .x86 ubuntu 8.10 installed.  I am trying to decide wither to install x64 and migrate over, have both installed, or just stick with 32 bit.  Currently, it seems that processor stays at 2.0GHz, and it only sees 2GB ram, although I know it can't see 4 due to 32 bit.  I will be running a virtual machine to house windows for some engineering apps that don't like wine, so I will stress system sometimes.  Also, stability is really important because computer stays on for long periods of time.  Being a college student, I also need lots of media capabilities.  What should I do?

---

### Post by bodhi.zazen on 2008-12-05
Umm, minus 10 geek points for that post :twisted:

32 bit OS can access up to 64 Gb ram

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

To say otherwise only makes you appear uneducated, not good, don't do it, and don't spread mis information.

Second, if you have a 64 bit CPU I can see no reason not to run a 64 bit OS. There are many benefits including increased security.

There was a time when the 64 bit OS was in development and "not up to par" with 32 bit OS, but this is no longer the case with Linux. 

With that said there may be a rare application here and there that may give you trouble, but they get rarer every day it seems.

---

### Post by handydan918 on 2008-12-05
under those circumstances, with disk real estate as cheap as it is these days, I'd add a partition or two for the new system, at least to try it out. That would have the advantage of allowing a fairly rigorous A/B comparison, just so you can determine if 64bit gives you any real advantages.

---

### Post by cdmike2k8 on 2008-12-05
Thanks so much for your help.  In windows, I only could use 3.2GB on 32 bit.  But this brings up another question.  Why is ubuntu not seeing my other 2gb ram?  It only shows 2GB in system monitor.  My cpu is also only going at 2.0ghz, but I am guessing that it is clocking down because of low load.  So is there a way to upgrade without full install, or is that the best route?

---

### Post by bodhi.zazen on 2008-12-05
yea, for windows you need to pay to upgrade to a PAE enabled kernel.

My best guess would be a hardware problem of some kind.

+1 on the suggestion to dual boot. The easiest (and probably only) way to upgrade is to re install.

You probably will not notice a huge performance boot between 32 and 64 bit OS unless you are doing something more cpu intense then posting on the Ubutu fourms (which is a cake walk for your CPU).

---

### Post by cdmike2k8 on 2008-12-05
After some research, I think thats what I will do.  Thanks again for your help.

---

### Post by bodhi.zazen on 2008-12-05
Welcome to Ubuntu. Thank you for marking the thread as solved, that is appreciated.

---

