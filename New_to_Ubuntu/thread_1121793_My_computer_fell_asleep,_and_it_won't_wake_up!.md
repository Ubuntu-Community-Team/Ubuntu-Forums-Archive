---
title: "My computer fell asleep, and it won't wake up!"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-10
When the system goes to sleep (NOT screensaver), the fans spin down, power light starts flashing, and so on.  I THINK that is normal.  If I press keys, nothing happens.  If I hit the power button, fans spin up- power light goes solid, and...  The screen stays black.  I can't do ANYTHING!  The only way to shut the system down then is to hold the power putton down until it shuts off, or plip the main PSU switch on the back.  Help please?

P.S.  I think the same thing happens for hibernation.

---

### Post by eeeandrew on 2009-04-10
I've had this same problem on ocassion. My rather unhelpful solution: don't let it go to sleep! Change the power settings system -> preferences -> Power Management so that it doesn't sleep. If anyone has a real solution to this then I'd like to hear it too!!

Good luck!
Andrew

---

### Post by FrankT-Qc on 2009-04-10
Give it some coffee...

---

### Post by eeeandrew on 2009-04-10
> Give it some coffee... 

I tried that once before...it had to go to the repair shop:lolflag:=D>

---

### Post by Therion on 2009-04-10
> **FrankT-Qc said:**
> 

Give it some coffee...

More Java?








/Two shows nightly...
//Be sure to tip your server!

---

### Post by qwertyuiop96 on 2009-04-10
> **eeeandrew said:**
> I've had this same problem on ocassion. My rather unhelpful solution: don't let it go to sleep! Change the power settings system -> preferences -> Power Management so that it doesn't sleep. If anyone has a real solution to this then I'd like to hear it too!!

I did that- just that it would be nice to conserve power...  Maybe its some glitch.  If so, lets hope it is fixed in Jaunty!

---

### Post by eeeandrew on 2009-04-10
> Give it some coffee...
More Java?


Release a python in the room with it. Would certainly wake me up:lolflag:

---

### Post by qwertyuiop96 on 2009-04-10
I would go for cappucino with extra caffine!  And a python for good measure.:lolflag:

---

### Post by acimmarusti on 2009-04-10
I have the same problem (I disabled suspend/sleep mode in my laptop). However Hibernate does work for me. This is how you make it work:

First lets see how much ram and swap you have by doing this:

```
free -b
```

Now check that swap is bigger than ram, if so then copy the amount of total memory you have and do:

```

sudo -i
gedit /etc/rc.local

```

Once gedit opens the file, add this line before the *exit 0*  line:

echo your_total_memory > /sys/power/image_size

Save the file exit root mode and restart. Now try hibernating!

If your swap is insufficient to hold your total RAM, you need to increase your swap. You can do this by resizing your partitions (but this takes forever!!) or you can follow the procedure I outlined here which is a lot faster: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

if you have questions, let me know

---

### Post by Therion on 2009-04-10
> **qwertyuiop96 said:**
> And a python for good measure.:lolflag:
I hope you don't constrict yourself to python...


[COLOR="White"].[/COLOR]

---

### Post by LowSky on 2009-04-10
if you use any proprietary drivers in use (ie wireless or video) it may casue an issue with Standy/Hibernation

---

### Post by acimmarusti on 2009-04-10
That would explain why it doesn't work for me. I'm using broadcom's firmware to make my wireless card work...is there any way around it?

---

### Post by qwertyuiop96 on 2009-04-10
similar for me.  I have a proprietary ATi driver I need for compiz and make Ubunt look like anything?  IS there any way to fix this?

---

### Post by CRIMPS on 2009-04-10
Its no secret that Linux has always had some issues with Suspend/Hibernate.  However, many of these issues have been receiving a lot of attention as of late.  I even read a blog post from Linus stating he thinks some of these issues have been worked out.  Im not sure if Power Management changes will be coming in Jaunty.  Stay tuned!

---

### Post by Yvan300 on 2009-04-10
Seems to be a hardware problem, my bud running vista got this same problem, but he didn't get it in ubunu, strange, it's like ubuntu cures the sick :)

---

### Post by qwertyuiop96 on 2009-04-10
If it is fixed in Jaunty, then I'll be looking forward to it!  The days till it comes must go faster... :p

---

