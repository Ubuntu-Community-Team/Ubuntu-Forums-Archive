---
title: "No propriety drivers are in use on this system"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Pikzilla on 2009-11-07
Hey, whenever I open system/administration/hardware drivers I get "No propriety drivers are in use on this system"

---

### Post by Sourmiloko on 2009-11-07
These are drivers that ubuntu recognises as working for the OS. You still have drivers, but they might be blacklisted.

---

### Post by overdrank on 2009-11-07
> **Pikzilla said:**
> Hey, whenever I open system/administration/hardware drivers I get "No propriety drivers are in use on this system"

Ok what version of Ubuntu are you using? You can check under system, about Ubuntu.
You may also use the command in the terminal  to identify your hardware.
```
lspci
```
I see in your past post it appears you are having graphical issues?
```
lspci | grep VGA
```

---

### Post by Pikzilla on 2009-11-07
> **overdrank said:**
> Ok what version of Ubuntu are you using? You can check under system, about Ubuntu.
You may also use the command in the terminal  to identify your hardware.
```
lspci
```
I see in your past post it appears you are having graphical issues?
```
lspci | grep VGA
```
I'm using Karmic Koala. I can see some hardware stuff after using the lspci command, but I number one, don't know what to make of it, and number two, can't actually update anything. And by my "past post" do you mean the other thread I have going? Because I never mentioned graphical issues here.

---

### Post by twisted_steel on 2009-11-07
The "no proprietary drivers" message isn't necessarily a bad thing.  It just means that no binary-only drivers are available for your system.  On my laptop, I have an older ATI card that used to use the official ATI drivers.  The official drivers are no longer compatible, so Ubuntu picks the open source driver instead.

Overdrank may have been interested in what graphics card you are using, as the proprietary drivers will show up in the Hardware Drivers program.  You can just paste the output of "lspci | grep VGA" in your reply.  In my case, the result is:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

---

### Post by Pikzilla on 2009-11-07
VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by The Cog on 2009-11-08
No proprietary drivers relly just means that all your hardware is using open-source drivers. That's a good thing - nothing to worry about. The intel open-source drivers are fine.

---

### Post by suri on 2011-10-24
Hi iam also facing same problem  and also another problem is after login to ubuntu working fine but when i keep resume means ideally black screen is appearing and it not showing anything i am restarting my system, I am using ubuntu 9.10 version mercury P1945GZD mother board please help.
My lspci | grep VGA output is 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

Thanks 
Suresh

---

