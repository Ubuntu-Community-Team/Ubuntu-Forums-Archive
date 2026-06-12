---
title: "Does Compiz cost more CPU in 11.04?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by ngubk on 2011-05-19
Since using 11.04, i've disabled almost every possible Compiz effects for me( i only add wobbly window to the default setting, yet Top command always shows Compiz among the top CPU cost ( it wasn't like that in 10.10)

What do you think?

---

### Post by wildmanne39 on 2011-05-19
> **ngubk said:**
> Since using 11.04, i've disabled almost every possible Compiz effects for me( i only add wobbly window to the default setting, yet Top command always shows Compiz among the top CPU cost ( it wasn't like that in 10.10)

What do you think?Hi compiz is second on mine to firefox which is a hog.

---

### Post by jtarin on 2011-05-19
Does Compiz cost more CPU in 11.04?
> **ngubk said:**
> Since using 11.04, i've disabled almost every possible Compiz effects for me( i only add wobbly window to the default setting, yet Top command always shows Compiz among the top CPU cost ( it wasn't like that in 10.10)
What do you think?

I think........ you answered you own question. Mark it solved.:P

---

### Post by mcduck on 2011-05-19
Assuming you have a graphics card (and drivers for it) that can handle the effects fine, the Compiz should not cost you any CPU time at all, quite the opposite, it would take some load off from your CPU and move it to GPU.

On the other hand if your graphics card isn't up to the task, or lacks decent drivers, then your CPU might end having to do some of the work.

So the CPU time cost of Compiz doesn't depend on what version of Compiz (or Ubuntu) you use, bu simply on how well your graphics card & drivers can handle it. IF you see Compiz using a lot of CPU time, then finding better drivers for your graphics card is the first thing to do.

---

### Post by jtarin on 2011-05-19
> **mcduck said:**
> Assuming you have a graphics card (and drivers for it) that can handle the effects fine, the Compiz should not cost you any CPU time at all, quite the opposite, it would take some load off from your CPU and move it to GPU.

On the other hand if your graphics card isn't up to the task, or lacks decent drivers, then your CPU might end having to do some of the work.

So the CPU time cost of Compiz doesn't depend on what version of Compiz (or Ubuntu) you use, bu simply on how well your graphics card & drivers can handle it. IF you see Compiz using a lot of CPU time, then finding better drivers for your graphics card is the first thing to do.Well the constant in this is his computer.......he upgraded and sees a difference in usage with 11.04 compared to 10.10. Where would you suggest he gets better drivers for his card? Drivers should be appreciably better each version......not downgraded when the OS upgrades.It is the OS...it is compiz. Isn't it possible both have been optimized for the latest hardware leaving a few behind in the rush? Wouldn't be the first time.

---

### Post by mcduck on 2011-05-19
It's a bit hard to say where to get better drivers for a graphics card without knowing what the graphics card in question is. ;)

Anyway, there's the [X Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") and the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa") and the [drivers-only version of the xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/drivers-only"), which all provide updates for graphics drivers.

---

### Post by ngubk on 2011-05-19
Thank you for your reply!
My HP4410s has an onboard Intel Graphic Card. If the Driver for this GC doesn't change or there isn't any possible solution,maybe i've to turn back to using 10.10. Compiz cost me 30% CPU every time i open a folder(nautilus) :)

---

### Post by ngubk on 2011-05-19
The reason for this is UNITY!!!.
When i disable UNITY, compiz doesn't cost much CPU anymore.
The same when i enable UNITY in Classic Mode.
It's a shame 'cause I thought i've finally come to like Unity top panel.

---

### Post by jtarin on 2011-05-19
> **ngubk said:**
> The reason for this is UNITY!!!.
When i disable UNITY, compiz doesn't cost much CPU anymore.
The same when i enable UNITY in Classic Mode.
It's a shame 'cause I thought i've finally come to like Unity top panel.I agree. This reminds me so much of that other operating system that always leaves its users in a constant state of hardware catch-up.

---

### Post by wildmanne39 on 2011-05-19
> **jtarin said:**
> I agree. This reminds me so much of that other operating system that always leaves its users in a constant state of hardware catch-up.

Ho no you did not go there?

---

### Post by CaptainMark on 2011-05-19
i find exactly the same, compiz is always running as my 1st 2nd 3rd highest cpu hog, and no it definitely wasnt like that before 11.04, it seems to me unity is just wasting resources, i have a plenty powerful enough gpu for anything i can throw at it and running propietary drivers which always work best. Its not my pc its not my gpu its not the drivers, what has changed, unity.

---

### Post by Frogs Hair on 2011-05-19
I experience no increased CPU usage with Compiz running Unity . The cube is enabled also.

---

### Post by mc4man on 2011-05-19
If you're seeing high CPU use with compiz then that is not a normal situation
Most times compiz has  virtually no cpu use or very little, 1% or so. .
When opening things it may spike a bit for a sec. or 2, running some app's here it may hang around 3-7% off and on.

As far as ram, compiz in unity will usually be the biggest user, though generally not an issue unless you have less that 1GB ram

---

