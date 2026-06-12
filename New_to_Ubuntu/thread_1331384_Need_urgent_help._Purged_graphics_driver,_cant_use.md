---
title: "Need urgent help. Purged graphics driver, can:t use ubuntu."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-11-19
I was trying to fix a problem on my computer after not receiving a reply to a post, asking for accurate advice. I found a thread in the wiki about updating ATI graphics card. The first thing I was told to do was purge the fglrx driver and restart, and that's exactly what I did. Now I can't use Karmic, when I restarted it took me to a black page similar to terminal and asked for my name and password there. Then it just went to root whatever as seen in terminal. I tried to use the safemode to see if there's anything I could do, but the screen would break with text going in weird places, so I cannot do anything there. Thankfully I have dual boot, so went to start windows, but that spat out some funny code in a black page also, then rebooted. So I tried again, and it sucessfully let me in. I decided to try update my ATI driver, or even reinstall it through windows, but that won't let me either.

I have much important information on my machine and cannot do a reinstall. Is there any way, I can reinstall the graphics card that I purged, without having to reinstall Karmic? Maybe when I get the terminal like window, there is some nice simple code I can enter to get it back? 

I have searched to try find the damned wiki entry that I followed but can:t seem to locate it. I really would appreciate immediate help.

---

### Post by ukripper on 2009-11-19
Do the normal boot of 9.10 and when you reach that black terminal screen can you type your username and password and then run this command:
```
sudo /etc/init.d/gdm start
```
```
startx 
```


any error post here.

---

### Post by halitech on 2009-11-19
what ati video card do you have?

---

### Post by T4K3Z0U on 2009-11-19
> **ukripper said:**
> Do the normal boot of 9.10 and when you reach that black terminal screen can you type your username and password and then run this command:
```
sudo /etc/init.d/gdm start
```

any error post here.

Thank you. Will try that now.

---

### Post by T4K3Z0U on 2009-11-19
> **halitech said:**
> what ati video card do you have?

Not entirely sure. think it's ATI Radeon 3400 or some such.

---

### Post by Jon Monreal on 2009-11-19
If that doesn't work, try typing in
```
sudo apt-get install xorg-driver-fglrx
```and pressing enter. This should reinstall the driver.

---

### Post by halitech on 2009-11-19
> **T4K3Z0U said:**
> Not entirely sure. think it's ATI Radeon 3400 or some such.

to find out for sure what card you have, run
```
lspci | grep VGA
```

---

### Post by T4K3Z0U on 2009-11-19
That took a while coz when I restarted, windows decided it wanted to install updates. 

I'm not sure what is the problem but I am not getting that login page anymore. It stops at a place saying "*Srarting Apparmor profiles" has a bunch of other things and says *fglrx (8.660).....Fail.

Looks like I'm really screwed. And coming back into windows I got teh funny black code again, this time whatever it was going through, was going through 20583, as opposed to the earlier 980 something, before rebooting. Never seen that before today. But at least it lets me into windows on the second try so I can at least reply here.

---

### Post by T4K3Z0U on 2009-11-19
Finally after much waiting, I got the terminal like screen again. I have multi-quoted some posts and given replies.

I wonder if I should mention here, my reason to try upgrade my driver which led to this problem.....:-k

> **ukripper said:**
> Do the normal boot of 9.10 and when you reach that black terminal screen can you type your username and password and then run this command:
```
sudo /etc/init.d/gdm start
```
```
startx 
```


any error post here.

I could only grap part of the message coz am unsure how to scroll back up, but here's what I got. My screen started blinking when I did this too.

```
Using config file "/etc/x11/xorg.conf"
(EE) Failed to load module "fglrx" (module does not exist, 0)

Fatal server error: No screens found.

ddxsigGiveUp: closing log, giving up.

xinit: no such file or directory (errno 2) unable to connect to xserver.
xinit: no such process (errno3)
```

> **halitech said:**
> to find out for sure what card you have, run
```
lspci | grep VGA
```

Seems I was close.

```
ATI Technologies inc Mobility Radeon HD 3400 series
```

> **Jon Monreal said:**
> If that doesn't work, try typing in
```
sudo apt-get install xorg-driver-fglrx
```and pressing enter. This should reinstall the driver.

This code worked, and successfully has my computer working again.

Thank you very much, all who helped me in this crisis.

---

