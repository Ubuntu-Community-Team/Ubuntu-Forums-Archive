---
title: "My time is wrong...? Ubuntu 9.04"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by xFlowx on 2009-07-04
Whenever I turn my computer on, the time is wrong. An hour behind the real time....I think it happened when I installed Ubuntu...but is there anyway to fix it?

Fixing it manually every time is getting annoying.

Thanks for any and all help! I'm still new to this.

This has been solved! Just an update.

---

### Post by alphacrucis2 on 2009-07-04
> **xFlowx said:**
> Whenever I turn my computer on, the time is wrong. An hour behind the real time....I think it happened when I installed Ubuntu...but is there anyway to fix it?

Fixing it manually every time is getting annoying.

Thanks for any and all help! I'm still new to this.

Maybe something to do with daylight saving. It normally figures that out based on the country you tell the installer.

---

### Post by stalkier on 2009-07-04
> **xFlowx said:**
> Whenever I turn my computer on, the time is wrong. An hour behind the real time....I think it happened when I installed Ubuntu...but is there anyway to fix it?

Fixing it manually every time is getting annoying.

Thanks for any and all help! I'm still new to this.

I know mine was wrong as well. Some how the time zone was wrong. Double check to see if it is correct for your area.

---

### Post by xFlowx on 2009-07-04
> **stalkier said:**
> I know mine was wrong as well. Some how the time zone was wrong. Double check to see if it is correct for your area.

I honestly do not know what my time zone is. All I know is that it's Mountain Time...but I don't understand the negative time things...

---

### Post by AntiVista on 2009-07-04
Mountain time should be -7.
 
I'm in Central time and mine is -6.
 
Also check your system BIOS to make sure that your time is set correctly there.

---

### Post by SunnyRabbiera on 2009-07-04
Give this a read over:
[http://www.go2linux.org/how-to-set-the-date-and-time-in-linux](http://www.go2linux.org/how-to-set-the-date-and-time-in-linux)

---

### Post by xFlowx on 2009-07-10
> **AntiVista said:**
> Mountain time should be -7.
 
I'm in Central time and mine is -6.
 
Also check your system BIOS to make sure that your time is set correctly there.

How would I check my system Bios?

---

### Post by XCan on 2009-07-10
Usually you would press 'del' or 'f2' when your computer starts. There should be a notification saying something along the lines of: "Press <key> to enter setup".

---

### Post by xFlowx on 2009-07-10
> **XCan said:**
> Usually you would press 'del' or 'f2' when your computer starts. There should be a notification saying something along the lines of: "Press <key> to enter setup".


Would that work on a dual-booted computer thing?

---

### Post by epicoder on 2009-07-10
> **xFlowx said:**
> Would that work on a dual-booted computer thing?

Yes.

---

### Post by earthpigg on 2009-07-10
to change the time zone from within ubuntu:

```
sudo dpkg-reconfigure tzdata
```

pick your country, and a major city in the same time zone.

if you want ubuntu to sync your system time automatically:

system -> administration -> time and date -> unlock -> keep synced with internet servers -> let it install NTS

close the time and date app -> restart it -> should now have the option to sync automatically -> select servers if you want -> pick some servers that look trusty to you.

i trust the germans to build a good clock, so i picked a few of theirs.

---

### Post by xFlowx on 2009-07-10
> **sh228 said:**
> Yes.


I don't have that option. I only have an option to edit windows...

---

### Post by xFlowx on 2009-07-10
> **earthpigg said:**
> to change the time zone from within ubuntu:

```
sudo dpkg-reconfigure tzdata
```pick your country, and a major city in the same time zone.

if you want ubuntu to sync your system time automatically:

system -> administration -> time and date -> unlock -> keep synced with internet servers -> let it install NTS

close the time and date app -> restart it -> should now have the option to sync automatically -> select servers if you want -> pick some servers that look trusty to you.

i trust the germans to build a good clock, so i picked a few of theirs.

I did that, aaand...the time is still an hour behind. What am I doing wrong?
Edit: Nevermind, I picked the wrong city. >w< I think that fixed it!

---

### Post by earthpigg on 2009-07-10
glad you fixed it :P

i was about to suggest the not-so-ideal solution of picking a city one time zone east and then moving back and forth every daylight savings, lol

---

### Post by xFlowx on 2009-07-10
> **earthpigg said:**
> glad you fixed it :P

i was about to suggest the not-so-ideal solution of picking a city one time zone east and then moving back and forth every daylight savings, lol
 That would have been horrible. XD Thank you! I hope it fixed it

---

