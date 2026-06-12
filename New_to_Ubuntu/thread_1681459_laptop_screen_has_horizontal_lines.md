---
title: "laptop screen has horizontal lines"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by hinata on 2011-02-04
there has been a faint horizontal line across the  bottom of my hp laptop screen. First I thought image permanence, but instead that what was flashing at the bottom of my  screen was what I could see at the top1/8 inch of my screen.  i.e, i could see the application, places, system found on the top panel.

---

### Post by prakashsairam on 2012-03-12
I have the same problem as stated above in my hp laptop the bottom of the screen has lines which flickers also i am able to the image of top panel(replica)
regards,
m prakash

---

### Post by prakashsairam on 2012-03-12
lspci -vnn | grep -A 10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:3607]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at 50000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 40000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 60f0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

the above is lspci of my hp laptop
regards,
m prakash

---

### Post by 2F4U on 2012-03-12
What are your hardware specs? Do you have this problem from the beginning? Are you using Ubuntu with the default Unity desktop?

---

### Post by prakashsairam on 2012-03-12
My hp laptop has intel celeron 2.1ghz processor sata 160 gb hdd,1 gb ram.i am using 11.10 with default unity.
regards
m prakash

---

### Post by matt_symes on 2012-03-12
Hi

I would eliminate hardware first. 

Hook it up to an external monitor and see if you get the same artefacts.

That is the first thing i do with any potential laptop screen or graphics card problem that is different than i have seen before.

Kind regards

---

### Post by prakashsairam on 2012-03-12
Hi matt,
When i connected to external lcd(AOC)monitor the lines did not appear.it is only in laptop screen.
regards,
m prakash

---

### Post by Paddy Landau on 2012-03-12
> **prakashsairam said:**
> When i connected to external lcd(AOC)monitor the lines did not appear.it is only in laptop screen.
I had this same problem on a laptop. It turned out to be a hardware fault (something to do with the "matrix" -- I don't know what that means).

---

### Post by matt_symes on 2012-03-12
Hi

> **Paddy Landau said:**
> I had this same problem on a laptop. It turned out to be a hardware fault (something to do with the "matrix" -- I don't know what that means).

I concur. I would be suspecting hardware. 

Boot into a LiveCD/USB and check out the screen (both laptop and external) to be more confident.

Kind regards

---

### Post by prakashsairam on 2012-03-12
Many thanks for your help , here in india it's 11p.m night i am feeling sleepy so i will post the result of live cd tomorrow.kindly excuse me.
regards,
m prakash

---

### Post by prakashsairam on 2012-03-16
i am unable to boot from live cd when i try to change the boot option from hdd to cd/dvd it does not work also how to make boot from cd option first in list it is second in the list
regards
prakash

---

### Post by matt_symes on 2012-03-17
Hi

There may be a 'quick select boot' option on your laptop. You get to it in my laptop by pressing F10 on the post screen.

If a LiveCD does not work, have you considered a LiveUSB ?

How did you originally install Ubuntu ?

Kind regards

---

### Post by bigmonmulgrew on 2012-03-17
Hi
It was a long time ago (5 year) but if I recall correctly I had this issue when using multi monitor.

The resolution was set just below what my monitor supported (by accident) and instead of filling to fit the monitor repeated the image.

Setting the resolution manually (as opposed to what the pull down offered me)fixed this. I'm afraid I dont remember how I did this and it probably wouldnt apply now anyway.
It also didnt occur in later releases with better graphics drivers.

If this is related to your issue then trying it on an external monitor would not reveal anything since it would likely be on a slightly different resolution.

Try setting your laptop screen to different resolutions and see what happens. If the place where the screen is repeated moves with the resolution then you have the same problem I had a few years ago.

A more up to date/different graphics driver may help this issue.

---

### Post by matt_symes on 2012-03-17
Hi

> **bigmonmulgrew said:**
> Hi
It was a long time ago (5 year) but if I recall correctly I had this issue when using multi monitor.

The resolution was set just below what my monitor supported (by accident) and instead of filling to fit the monitor repeated the image.

Setting the resolution manually (as opposed to what the pull down offered me)fixed this. I'm afraid I dont remember how I did this and it probably wouldnt apply now anyway.
It also didnt occur in later releases with better graphics drivers.

If this is related to your issue then trying it on an external monitor would not reveal anything since it would likely be on a slightly different resolution.

Try setting your laptop screen to different resolutions and see what happens. If the place where the screen is repeated moves with the resolution then you have the same problem I had a few years ago.

A more up to date/different graphics driver may help this issue.

This is a good call and something i would definitely test.

Kind regards

---

### Post by bigmonmulgrew on 2012-03-17
> **matt_symes said:**
> Hi



This is a good call and something i would definitely test.

Kind regards

glad you think so :)

---

### Post by prakashsairam on 2012-03-19
Hi matt
finally i managed to boot from live cd the result is my laptop screen still has lines at the bottom while external monitor works fine.what should i do further?.i think it's not a hard ware problem because i have windows xp loaded earlier and now i have installed ubuntu11.10 fully erased windows .initially the line were very minimal so i did not care but now it is many lines .when i have windows there were no problem like this.all this happens once i migrate from windows to ubuntu.
regards,
prakash

---

### Post by prakashsairam on 2012-03-19
Is complete re installation of ubuntu will solve the problem?
regards,
prakash

---

### Post by matt_symes on 2012-03-19
Hi

Take a look at post #13.

Kind regards

---

### Post by prakashsairam on 2012-03-20
Hi,
how to manually try different screen resolutions to test ?
regards,
m prakash

---

### Post by bigmonmulgrew on 2012-03-20
When I say manually I mean setting it in the configuration files instead of the gui. This lets you set different resolutions that are not offered in the gui, and may be more risky since editing these incorrectly will not give you chance to revert.
I cant find the thread on how I did this and its probably out of date anyway.

Firstly I'd try changing the resolution in the GUI to something lower. If you set it to something lower the line should move up the screen if I'm correct about your problem.

What I suspect is happening is you have a 768 line screen and ubuntu is detecting your resolution as 720 lines, or a similar larger size ie 1080/1024. Your graphics driver then fills in the gap by repeating the image.

I'd also check if your using the latest graphics driver for your hardware.

---

### Post by prakashsairam on 2012-03-22
Hi 
Tried different resolution using Gui but lowering resolution is  not helping so still no solution for the problem.as a temporary solution i am using an aoc 18.5 led external monitor to get rid of annoying screen flickering lines. 
regards
prakashsairam.

---

### Post by bigmonmulgrew on 2012-03-22
I think your missing the point.
Lowering the resolution is not to fix the problem it is to diagnose the cause.
We need to know the results of this.
Does the point where the screen is repeated move when you lower the resolution.
We also need to know what resolution your using and what resolutions your offered.

---

### Post by prakashsairam on 2012-03-23
Hi,
There are three resolutions available in settings---display-- 1280x800 ,1024x768 and 800x600 and i set it to 1280x800 as it is better looking.but line are appearing in all the three modes.when ubuntu 12.04 comes i try to install cleanly to try luckof getting rid of these annoying lines.
regards,
prakashsairam

---

### Post by bigmonmulgrew on 2012-03-23
> **bigmonmulgrew said:**
> I think your missing the point.
**Does the point where the screen is repeated move when you lower the resolution.**


You don't seem to be listening to this point so lets just see what 12.04 does for you.

---

### Post by prakashsairam on 2012-03-23
Hi,
I have tried various methods seen in different threads nothing seems to fix the problem.so let us wait for 12.04.
regards,
prakashsairam

---

### Post by Mark Phelps on 2012-03-24
This is not a resolution problem, folks have tried to tell you that several times.

It is also most likely, NOT a driver problem either.

Thus, it is extremely unlikely that 12.04 will fix this.

I have seen this before, and every time, it was a hardware problem -- failing screen.

---

### Post by matt_symes on 2012-03-24
Hi

> **Mark Phelps said:**
> This is not a resolution problem, folks have tried to tell you that several times.

It is also most likely, NOT a driver problem either.

Thus, it is extremely unlikely that 12.04 will fix this.

I have seen this before, and every time, it was a hardware problem -- failing screen.

After all the tests you have performed, i would agree.

It's not a GPU issue (External monitor).
It's not a driver issue (External monitor, LiveCD).
It's not a resolution issue (Changing resolution did not help and the position of the distortion stays the same).

It's a screen issue (99% sure - i'm never 100% sure unless the hardware is in my hands). Replace your laptop screen.

Kind regards

---

### Post by prakashsairam on 2012-03-25
Hi mark and matt,
Thanks for your inputs for the screen problem i would like try one last hope of installing 12.04 only to my satisfaction if it does not solve the screen problem then as you advised me i will took it to my nearest hp service centre and change the screen.once again thanks for your feed back.have a nice day.
regards,
prakash sairam

---

