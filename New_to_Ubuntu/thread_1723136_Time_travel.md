---
title: "Time travel?"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by beew on 2011-04-06
I notice recently that the time on my laptop is off when I am not connected to the internet.

Is there any way to fix that?

I am on Ubuntu 10.10

Thanks.

---

### Post by sydbat on 2011-04-06
> **beew said:**
> I notice recently that the time on my laptop is off when I am not connected to the internet.

Is there any way to fix that?

I am on Ubuntu 10.10

Thanks.And here I was hoping you solved the quantum physics problems surrounding time travel and were going to tell us you were going back in time to punch out a dinosaur or something...I am disappoint.

On topic - what does the BIOS time state? Is it accurate?

---

### Post by beew on 2011-04-06
> **sydbat said:**
> And here I was hoping you solved the quantum physics problems surrounding time travel and were going to tell us you were going back in time to punch out a dinosaur or something...I am disappoint.

On topic - what does the BIOS time state? Is it accurate?

Yeah, just hoping to get more attentions. If I can go back in time I have more interesting projects than to pick on the poor dino. :)

The bios time is incorrect as well, same as what Ubuntu displays. So I should just change it in the BIOS? I am not sure why it is out of sync suddenly (and is exactly 4 hours off)

---

### Post by Hedgehog1 on 2011-04-06
Is this a 'local time' (on your MB clock) vs GMT (Greenwich Mean Time) time getting pulled from the web?  Are you 4 hours different from Greenwich?

If it is exactly 4 hours, this makes sense...


***The Hedge***

:KS

p.s. And have you been using the Natty beta on this PC? If so, you have a bug to report...

---

### Post by safarin on 2011-04-06
Maybe your cmos clock already dead... :confused:

---

### Post by lixianlee1988 on 2011-04-06
hahaha`~~~~ nice shot~~~! it really makes me smile for a while~~~ if it can thumb i will thumb twice, if it can rate i will rate double 5, and if i can ..........

---

### Post by beew on 2011-04-07
> **Hedgehog1 said:**
> Is this a 'local time' (on your MB clock) vs GMT (Greenwich Mean Time) time getting pulled from the web?  Are you 4 hours different from Greenwich?

If it is exactly 4 hours, this makes sense...




:KS

p.s. And have you been using the Natty beta on this PC? If so, you have a bug to report...

Yes, i think that is the difference between the local time and GMT. As soon as I get connected the time is correct again. So should I just reset the BIOS time?

I have run Natty on the pc. from an external drive. I am not sure how it could have affected the BIOS time though.

---

### Post by beew on 2011-04-07
> **safarin said:**
> Maybe your cmos clock already dead... :confused:

Don't think so, because it is always four hours ahead. If it were dead it wouldn't change.

---

### Post by Hedgehog1 on 2011-04-07
OK beew - You caught me.  It turns out it is not a **bug**, it is an **option** in Natty:

[IMG]http://img713.imageshack.us/img713/3254/settime.png[/IMG]

This options sets your CMOS clock to GMT when you boot Natty.


***The Hedge***

:KS

---

### Post by srs5694 on 2011-04-07
Hedgehog1, I don't see anything in your screen shot about the hardware/CMOS clock being set to local time vs. UTC (aka GMT). There *is* such an option on installation, though.

Background: Windows, like DOS before it, assumes that the hardware clock is set to local time. Computer timekeeping is better done using Coordinated Universal Time (UTC), aka Greenwich Mean Time (GMT); this simplifies Daylight Saving Time changes and coordination of time between computers on a network, among other things. Thus, Unix systems have traditionally stored time in their hardware clocks in UTC. Linux has the option to do either, and most distributions, Ubuntu included, provide this option when you first install the OS. If your computer dual-boots Windows, it's simplest to tell Linux to store local time in the hardware clock; but if Linux boots alone on the computer, or dual-boots with another UTC-using OS (such as FreeBSD or Mac OS), you're better off using UTC in the hardware clock.

It sounds like beew set the wrong option. Unfortunately, I don't know of a GUI way to change this option. In fact, I'm not even positive of a non-GUI way -- it's not exactly something I need to change very often! I *think* it can be changed by editing /etc/default/rcS and changing the "UTC=" line from "no" to "yes" or vice-versa, depending on how it's misconfigured.

If Ubuntu is set to use UTC and it boots alone but the hardware clock is set to local time, then it's better to adjust the hardware clock. Assuming the software clock (as shown or set by the "date" utility or most other time/date tools) is set correctly, this can be done in Linux by typing:

```

sudo hwclock --systohc --utc

```

Incidentally, in a dual-boot configuration with Windows, it's possible to reconfigure Windows to interpret the hardware clock as UTC. This will reduce the risk of problems when there are Daylight Saving Time adjustments. [This blog post](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx) describes how to make the change.

---

### Post by sydbat on 2011-04-07
beew - change the BIOS clock and see if the changes are permanent. If they are, even after you go online, then you are done.

If not, try srs5694's suggestion.

No need to over complicate things. Always try the simple solution first, then you won't get as frustrated and think that the solution always has to be overly complicated.

---

### Post by traceur23 on 2011-04-07
Darn.  I was really hoping you'd built a linux-based machine to travel through time. You know...

```
~ $ sudo reverse time -600 years
[sudo] password for sean:
Initializing...
WARNING:  This action will REVERSE TIME 600 years.  Proceed at your own risk! 
Do you want to continue [Y/n] ? y
Calculating...   done.
Initializing flux capacitor...  done.
Reversing time...  done.
Action completed.  Enjoy 1411!
```

---

### Post by srs5694 on 2011-04-07
> **sydbat said:**
> No need to over complicate things. Always try the simple solution first, then you won't get as frustrated and think that the solution always has to be overly complicated.

I disagree with this advice, at least to a point. Much of my post was aimed at providing information with which to properly diagnose the problem. I've seen far too many threads here (and elsewhere) in which people attempt simple solution after simple solution, in the process digging themselves in deeper and deeper because they're creating new problems atop old problems. If you understand the cause of the problem, you can fix it properly. If you don't, trying a "simple" solution is like playing Russian Roulette.

That said, if there are multiple equally good solutions to a problem, using the simplest solution does make sense. There are also situations where trying something simple might work and is unlikely to have negative consequences down the line -- but you've got to have a pretty good understanding of the issues to make that determination.

In this specific case, it *seems to be* a UTC/localtime issue, but I'm not positive of that -- I didn't notice beew specifying if the computer was dual-boot or dedicated to Ubuntu, whether UTC or local time was selected at installation, what time zone s/he is in, etc.

---

### Post by Hedgehog1 on 2011-04-08
> **srs5694 said:**
> Hedgehog1, I don't see anything in your screen shot about the hardware/CMOS clock being set to local time vs. UTC (aka GMT). There *is* such an option on installation, though...

I remember seeing a setup for this when installing one of the many Natty builds.  I looked everywhere to find the GUI (or CLI) way that it can be displayed/changed.  This was the only place where it even showed in the Beta 1 + updates.  This option, if unchecked, ***otta*** stop overwriting beew's on-board clock.

I know I saw this setting and carefully selected to not store the time in GMT on my testing laptop (we do run all of our Linux servers on strictly GMT in their on-board clocks, they are spread across 5 time zones and it is the only way to keep things straight).

The lack of any ability to see or change this option after the install of Natty feels like a bug to me.  I did not really see it on my testing laptop as Natty is the only OS on it.

***The Hedge***

:KS

**srs5694** - you continue to keep me on my toes... :D

---

