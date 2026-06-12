---
title: "Gateway M-1625 overheating"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by 00ber n00b on 2009-11-09
My laptop over heats and shuts down in a matter of seconds while in "performance" freq scale mode.  It shouldn't do this...right?

I would use ondemand all the time, but, embedded videos are really glitchy.

How can I fix this?

Thanks.

---

### Post by 00ber n00b on 2009-11-09
Good morning.

---

### Post by 00ber n00b on 2009-11-09
Echo hello world

---

### Post by QIII on 2009-11-09
I googled your model and found a lot of complaints about overheating.

My first suggestion would be to open the case and blow out all the dust bunnies.  You may want to consult your manual or an on-line service manual, since opening the case on a laptop can sometimes be rather involved.

Take a look at the fan/heatsink assembly in particular.

How old is the computer?  Does it have BIOS settings for fan speed at pre-determined temperatures?

---

### Post by 00ber n00b on 2009-11-09
> **QIII said:**
> I googled your model and found a lot of complaints about overheating.

My first suggestion would be to open the case and blow out all the dust bunnies.  You may want to consult your manual or an on-line service manual, since opening the case on a laptop can sometimes be rather involved.

Take a look at the fan/heatsink assembly in particular.

How old is the computer?  Does it have BIOS settings for fan speed at pre-determined temperatures?

Computer is a couple years old. No bios settings for that type of control.  It has always had heat issues,but not to the point of shutting itself off.

---

### Post by sdpiowa on 2009-11-09
See if you can enable a BIOS warning.  Your computer should start beeping when it is overheating.

---

### Post by 00ber n00b on 2009-11-09
> **sdpiowa said:**
> See if you can enable a BIOS warning.  Your computer should start beeping when it is overheating.

That could work.  What about making it throttle back once it reaches a certain point instead of shutting down?

---

### Post by QIII on 2009-11-09
> **00ber n00b said:**
>  It has always had heat issues,but not to the point of shutting itself off.

Over time, a hot system will become more and more damaged.  The "Max operating temperature" figures you see are often the point at which the CPU spontaneously erupts into flames and sets your home fire alarms off.

You may simply have gotten to a tipping point.

You may be able to salvage your CPU for a while longer if you (some frustrating disassembly required) remove the old thermal paste between the CPU and the heat sink (if it is baked hard, you have a problem!) and add some new.

---

### Post by QIII on 2009-11-09
> **00ber n00b said:**
> That could work.  What about making it throttle back once it reaches a certain point instead of shutting down?

On-demand is already throttling.  If what you are doing is CPU intensive, you are going to use more of the CPU's capacity.

The "shut down" is meant to protect your machine and you don't want to thwart that.

---

### Post by 00ber n00b on 2009-11-09
> **QIII said:**
> On-demand is already throttling.  If what you are doing is CPU intensive, you are going to use more of the CPU's capacity.

The "shut down" is meant to protect your machine and you don't want to thwart that.

Ondemand causes embedded videos to be glitchy.  Maybe I can change the trigger points of ondemand?!

---

### Post by 00ber n00b on 2009-11-09
> **QIII said:**
> Over time, a hot system will become more and more damaged.  The "Max operating temperature" figures you see are often the point at which the CPU spontaneously erupts into flames and sets your home fire alarms off.

You may simply have gotten to a tipping point.

You may be able to salvage your CPU for a while longer if you (some frustrating disassembly required) remove the old thermal paste between the CPU and the heat sink (if it is baked hard, you have a problem!) and add some new.

Yeah, with this laptop cpu access if fairly easy.  It may help, but, I think its just a problem with these gateway laptops. after all the laptop was only $500.

---

### Post by LewRockwell on 2009-11-09
it would be a good idea to check for obstructions and also renew your thermal compound

you also should look into the best way to provide additional airflow throughout the case of your unit

sometimes you can make due with one of those cooling pads with powered fans but if your video hardware is overheating ventilating the whole case will provide better overall cooling

that looks like a barrett in your photo...

.

---

### Post by 00ber n00b on 2009-11-09
> **LewRockwell said:**
> it would be a good idea to check for obstructions and also renew your thermal compound

you also should look into the best way to provide additional airflow throughout the case of your unit

sometimes you can make due with one of those cooling pads with powered fans but if your video hardware is overheating ventilating the whole case will provide better overall cooling

that looks like a barrett in your photo...

.

Your eyes do not deceive you.  Never had the pleasure of shooting one.  But, I have had the pleasure with its fully auto counterpart.

---

### Post by 00ber n00b on 2009-12-06
used canned air and cleaned out the internal components really well.  temps are up to 70 celcius, just web browsing in performance mode.  It hasn't shut down on me yet...

---

### Post by chappatti on 2010-01-06
Have the same laptop, exact same problem.  ONLY FIX was to "re-grease" the cpu-heatsink connection.  As 'unecessary' as it may sound, it has stopped all shutdowns.  As your quote shows below, you were so close yet so far, since cheap 'grease' goes with cheap laptops.


> **00ber n00b said:**
> Yeah, with this laptop cpu access if fairly easy.  It may help, but, I think its just a problem with these gateway laptops. after all the laptop was only $500.

UPDATE: Installed Ubuntu 9.10.  Everything ncluding Skype (2.1 beta 2) with video works. One MUST use on-demand or conservative for CPU control since performance still shuts computer down.....critical temperature reached warning.  After greasing my cpu looks like pushing the cpu clearly causes the overheating, and this is not mitigated by the weak heat sink design..!

---

### Post by 00ber n00b on 2010-01-06
> **chappatti said:**
> Have the same laptop, exact same problem.  ONLY FIX was to "re-grease" the cpu-heatsink connection.  As 'unecessary' as it may sound, it has stopped all shutdowns.  As your quote shows below, you were so close yet so far, since cheap 'grease' goes with cheap laptops.

True.  I may re-thermo the cpu in the future.

---

