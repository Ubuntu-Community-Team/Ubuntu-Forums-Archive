---
title: "Crashes After 10 mins."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Lukehluke on 2009-01-19
Hi,

I installed ubuntu about a week or so ago.
After 10 mins or so it crashes and I have no idea why.
When I say crashes, I mean completely freezes.

---

### Post by cmnorton on 2009-01-20
Please post something about your hardware, laptop or desktop, memory, graphics card, and cpu would help for starters. 

Please try to boot with a live CD. Does that crash after 10 minutes?

During the 10 minutes you have, look through /var/log/syslog and /var/log/messages, along with the output of dmesg to see if there is anything tell-tale that might explain why this is happening.

What is your graphics setting (resolution)?

---

### Post by lukjad on 2009-01-20
Also, were there any programs that were running just before the computer crashes?

---

### Post by Lukehluke on 2009-01-21
> **cmnorton said:**
> Please post something about your hardware, laptop or desktop, memory, graphics card, and cpu would help for starters. 

Please try to boot with a live CD. Does that crash after 10 minutes?

During the 10 minutes you have, look through /var/log/syslog and /var/log/messages, along with the output of dmesg to see if there is anything tell-tale that might explain why this is happening.

What is your graphics setting (resolution)?

It is a desktop.
3GHz CPU.
512MB RAM.
ATI ATI Radeon 300SE.

I will try running the Live CD.

Also I am using 1024 x 768 Pixelz.

> **lukjad007 said:**
> Also, were there any programs that were running just before the computer crashes?

I am only running this program.
[http://graha.ms/androidproxy/](http://graha.ms/androidproxy/) & Firefox.

---

### Post by 2hot6ft2 on 2009-01-21
Maybe these will help.
System Freezes
Ubunut Intrepid - Clocksource From Hell
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell)

Ubuntu Intrepid - Clocksource Fixed, System Still Hangs, AND No Videos - FGRLX Fixes It
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)

---

### Post by Facetious Falcon on 2009-01-21
Have you ran the memtest86 option at the grub menu. It could be bad RAM but unlikely, always useful to check.

---

### Post by mkvnmtr on 2009-01-21
Before you get worried about the system check to see if it is just getting hot. If it has some time one it it might be full of dust. Alittle use of a can of compressed air might solve your problem. Laptop will be a lot more work than a desktop and you will have to be much more careful.

---

### Post by northern lights on 2009-01-21
> **mkvnmtr said:**
> Before you get worried about the system check to see if it is just getting hot.
+1

After booting, open a Terminal (Applications > Accessories) and run```
sudo apt-get install lm-sensors
```and subsequently```
sensors-detect
sensors -s
/etc/init.d/lm_sensors restart

```and finally```
sensors
```to check

---

### Post by SunnyRabbiera on 2009-01-21
What version are you running?
I find Ibex to be a unstable mess, it might be best to use hardy instead

---

### Post by handydan918 on 2009-01-21
> **SunnyRabbiera said:**
> What version are you running?
I find Ibex to be a unstable mess, it might be best to use hardy instead
+1


Maybe we're spoiled by that OTHER linux....:p

---

### Post by xXZeroXx on 2009-01-21
Put this en the Terminal:
```
sudo apt-get remove powernowd
```
Then it will ask for your password, type it and with some luck, you won't have that problem again. ;)

---

### Post by handydan918 on 2009-01-21
It might be interesting to see if you can ssh in to that machine after the crash....and do ```
dmesg | tail -40
```

---

### Post by Lukehluke on 2009-01-21
I don't think its the system over heating as I also have XP on there and everything works fine on XP.


> **xXZeroXx said:**
> Put this en the Terminal:
```
sudo apt-get remove powernowd
```
Then it will ask for your password, type it and with some luck, you won't have that problem again. ;)

What does that do?

---

### Post by handydan918 on 2009-01-21
> **Lukehluke said:**
> I don't think its the system over heating as I also have XP on there and everything works fine on XP.




What does that do?
Well, it removes the powernow daemon, and if it causes a problem you can reinstall with ```
sudo apt-get install powernowd
```

---

### Post by Lukehluke on 2009-01-21
Ah.

There is a lot of information in the system log.

How do I copy it into a text document or something?

---

### Post by Lukehluke on 2009-01-21
Also I don't know if this matters but... I don't have a direct internet connection to the computer and it was installed via Wubi.

---

### Post by handydan918 on 2009-01-22
> **Lukehluke said:**
> Also I don't know if this matters but... I don't have a direct internet connection to the computer and it was installed via Wubi.

Wubi is not a good method of permanent installation. It is intended to let you sample the features of Ubu without the lag inherent when running from a live cd.

If you intend to continue to use Ubu, please, do yourself a favor, and do a standard install, whether dual-boot or standalone.

---

### Post by Lukehluke on 2009-01-22
Well I tried petitioning my HD but I think there is something to do with bad sectors or something @_@'

---

### Post by DM was on fire! on 2009-01-22
> **Lukehluke said:**
> How do I copy it into a text document or something?

Open your System Log, go to Edit -> Select All, and then copy and paste it into your word processor/text editor/et cetera. :)

Are you having any program crashes either?
If it's on the dot after ten minutes, that would lead me to believe you have bad RAM or your system is overheating, but with an ATI video card, it's hard to tell. 
ATI =/= good with Linux, most of the time atleast.

---

### Post by suri.mahendra on 2009-01-22
How old is your equipment?  Are you running name brand equipment?  Some of those Winblows machines have poor quality components.

Also you might want to check all your connections and move everything off cards and plug straight into your motherboard.  I have had video and sound cards yield these problems.

RAM can also give you these problems.  

Linux is less tolerant of "slop" in hardware.  Chances are you have a bad component.

---

