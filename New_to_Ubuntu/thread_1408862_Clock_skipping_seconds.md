---
title: "Clock skipping seconds"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-16
I just noticed that the clock in the upper panel is skipping some seconds. Is anybody experiencing this?

---

### Post by v1ad on 2010-02-16
replace your rtc battery on your motherboard

---

### Post by SteelCore on 2010-02-16
I surely will. Thanks

---

### Post by egalvan on 2010-02-16
the battery on the motherboard only powers the clock when the mb is not receiving power from the power supply.

You state that the clock is "skipping" seconds...
is the clock actually "losing" time?
does this only happen between re-boots?
if it happens between reboots, then most likely the battery does need replacing.
if the clock is accurate, then this is just a display problem.
if the clock is actually losing or gaining time (not between reboots), then this is a more serious problem.

and if the battery is more than 2-3 years old, you may want to replace the battery anyway,
as it is reaching it's end-of-life.
Blow out the dust-bunnies while you have the case open... :)

---

### Post by SteelCore on 2010-02-16
The clock isn't losing time. The time actually appears to be accurate. it's just that some seconds don't appear. So it goes 1 2 3 _ 5 6 7 _ 9 (4 and 8 were skipped)

I don't understand what you mean by it happening between re-boots.
Thank you for your time.

---

### Post by egalvan on 2010-02-17
> **SteelCore said:**
> The clock isn't losing time. The time actually appears to be accurate. it's just that some seconds don't appear. So it goes 1 2 3 _ 5 6 7 _ 9 (4 and 8 were skipped)

Clock displays are usually low-priority items, so the display update may be "pushed aside" by more important processes (disk read/write, memory checks, etc).
This "skipping" seconds is normal.

If the skipping is a problem for you,
it may be possible to change the priority of the clock display.
Others will have to chime in on this.

> 
I don't understand what you mean by it happening between re-boots.
Thank you for your time.

When a computer system boots, the software reads the hardware clock to get the time and date.
While the computer is actually running, the hardware clock is not referenced any more.
Updates are gotten from a reference, usually an on-line time clock reference, such as NIST servers.
When Linux shuts down, it updates the hardware clock from the software clock with the current time and date (this is an option, usually set by default, but it can be changed)
As the machine powers down, the battery takes over the task of keeping the RTC (Real Time Clcok) on the motherboard up and running.
If the battery is weak or dead, the clock will change the time and date (if the battery is low enough, the BIOS will reset to factory defaults, and the clock will not have an accurate time)
When you next start the computer, it will not have the correct time/date.

Note that this only happens with a full re-boot, also called a hard re-boot.
Simply re-starting the operating system will not result in the clock going to battery mode.
The motherboard has to actually lose power (power_good has to go false, as the techs say) for the clock to change to battery.

And having the time change during power-down re-boots is 99% related to a dead/dying battery
(the other 1% is a problem with the time daemon)

---

### Post by SteelCore on 2010-02-17
Thanks for the detailed explanation.
So the answer is no, it doesn't lose time between reboots. I actually shut it down for hours and the time doesn't get lost.
I guess if it's only a display issue, the battery can wait :)
Thanks again

---

### Post by egalvan on 2010-02-17
> **SteelCore said:**
> it doesn't lose time between reboots. I  **shut it down for hours and the time doesn't get lost.**
if it's only a display issue, the battery can wait :)


Most definitely a display issue.

BTW, the cell is a 2032.
It can be found in the electronics, camera, watch and jewelry sections.
That list is in more-or-less increasing order of cost :)
Wally-World type stores will generally be cheaper.
The better brands have dates on them ("use-by" or "made-on")
to help make sure you get a fresh cell.

Be well.

---

### Post by pbpersson on 2010-02-17
If you find that the clock on your Ubuntu machine is skipping seconds it is because time flies when you are having fun.  ;)

---

### Post by SteelCore on 2010-02-17
> **pbpersson said:**
> If you find that the clock on your Ubuntu machine is skipping seconds it is because time flies when you are having fun.  ;)

True  :D

---

### Post by v1ad on 2010-02-17
o i though it was running slow. nvrm. i had that happen to me the sys time was running slow replaced rtc it fixed it. if the time is accurate then the rtc is fine

---

