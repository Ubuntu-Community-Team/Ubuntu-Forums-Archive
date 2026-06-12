---
title: "Password freezes me!"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by Albert Wesker on 2009-05-27
Sorry to bother everyone, just started with Ubuntu last night and I'm trying to add programs and drivers and I encountered this recently where when I am required to enter my password my computer freezes. Any idea how I can fix this and proceed with my Wista free life?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
on this I get to the screen where I enter the password and... freeze.

---

### Post by Sealbhach on 2009-05-27
I've never seen that before. It's possible it might be something to do with the graphics. One thing to test is to try to install something from the command like. So open up a terminal and copy and paste this command into it:

sudo apt-get install glunarclock

This will install a little moon calendar on your bottom panel, this is just to test that things install correctly. If they do, then you probably have a graphics problem.

To open a terminal, go to the menu Applications>Accessories>Terminal

.

---

### Post by Albert Wesker on 2009-05-27
Okay well it does seem to be a graphics problem, then. I was able to install fine in the terminal like you suggested.
What would be the next step to correct this problem? Or should I just get better a acquainted with the terminal, for a long long time...

---

### Post by Sealbhach on 2009-05-27
> **Albert Wesker said:**
> Okay well it does seem to be a graphics problem, then. I was able to install fine in the terminal like you suggested.
What would be the next step to correct this problem? Or should I just get better a acquainted with the terminal, for a long long time...

You'll need your password for a lot of things, so maybe you could give us some idea of what hardware you have, what your graphics card is and how much RAM you have? It may be you have not enough RAM.

.

---

### Post by Albert Wesker on 2009-05-27
**Compaq**                                                                                    CQ50-215NR
**Microprocessor**                                          1.90 GHz AMD Athlon X2 QL-60 Dual-Core Processo
 **Microprocessor Cache**                                          1 MB L2 Cache[B]
[/B]**Memory**                                          2048 MB[B]
[/B]**Memory Max**                                          Up to 4 MB DDR2[B]
[/B]**Video Graphics**                                          NVIDIA GeForce 8200M
**Video  Memory**                                          Up to 895 MB
**Hard Drive**                                          160 GB (5400 rpm)
**Network Card**                                          Integrated 10/100 Ethernet LAN
**Wireless Connectivity**                                          802.11b/g WLAN
  
Okay well that's the specs that I think are relevant, notice I really don't but I try and these are what they 
are. I hoped 2 GB would be enough

---

### Post by NyteWyyrm on 2009-05-27
Does it freeze when you hit 'OK' after you've entered your password, or before you even enter your password?

---

### Post by Sealbhach on 2009-05-27
Yeah, that hardware should run just fine with the full Ubuntu desktop. Is your graphics card enabled? Maybe there's driver problems with the nvidia driver.


.

---

### Post by Albert Wesker on 2009-05-27
First, I can't even enter my password.

2nd yeah I thought I installed my drivers properly but it freeze even when I turn off the effects.
System>Preference>Appearance> Visual Effect (none) = freeze = :(

---

### Post by Sealbhach on 2009-05-28
I'm not sure how to proceed with this. Can anyone else think of anything to help?



.

---

### Post by orky7 on 2009-05-28
This freeze thing happens to me also but in my case when i was entering password and hitting enter after the suspend mode(stand by mode). I thing its some kind of rare bug....

---

### Post by NyteWyyrm on 2009-05-28
Since we're running a little low for ideas, take a look at this page.  I have actually experienced this with 8.04, but I'm not sure it is the case here.  Never hurts to give it a shot, however.

[http://www.joewein.net/blog/2008/05/17/update-manager-hangs-in-ubuntu-804-and-how-to-fix-it/](http://www.joewein.net/blog/2008/05/17/update-manager-hangs-in-ubuntu-804-and-how-to-fix-it/)

---

