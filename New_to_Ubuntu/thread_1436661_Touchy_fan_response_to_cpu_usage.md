---
title: "Touchy fan response to cpu usage"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Zerp64 on 2010-03-22
This is horribly annoying. My computer has been behaving oddly in the past few months. With my old Windows install, my CPU and case fans always fan at 100%, but I was able to control it easily with SpeedFan, which is an awesome little fan control app.

Ubuntu behaves a little differently: the CPU fan seems to run at a decent speed when there is no CPU use, but when the CPU is used *at all*, fan speed jumps up to 100 until CPU usage is down to a stable 2-3%

I've messed with lm-sensors, but after running sensors-detect, pwmconfig states:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

But I'm sure it worked before my fans started acting to oddly. So what does everyone think? Could it be a sudden problem with the BIOS? Or something hardware-related? And most importantly, can I get these darn fans under control?

*edit:* Oh, and take a look at my trip_points file in /proc/acpi/thermal_zone/THRM/....

```
critical (S5):           100 C
passive:                 -248 C: tc1=4 tc2=3 tsp=60 devices=CPU0 
active[0]:               -266 C: devices= FAN 
```

---

### Post by OriginalName on 2010-03-23
Some motherboards have fan control settings in the BIOS... might be worth a look. I had similar problems on a Intel m/b (sounded like it was going to take off!) - I updated the bios and it sorted it (it's a windows box so was nothing to do with Ubuntu). 

Be careful updating the BIOS I managed to turn the PC into a brick for a while (nothing like a borked BIOS to bring you out in a cold sweat!) - Have another PC with internet access on standby as you may need to try a few different versions of the update method (Intel have a few dif methods i.e. boot cdrom, usb, exe from the o/s etc) and if it breaks something you'll need the m/b manual or help file to do a hard BIOS reset (usually involving opening up the PC and moving some jumpers around). 

Just to note that I tried the "operating system" method of updating the BIOS and it failed so had to reset it, download and burn the CDROM method (a slightly older version of the update) and basically mess around with it till it worked. Not recommended if it's your only PC or you're not happy taking the side of etc... If it aint *that *broke I'd leave it alone!

---

### Post by 3rdalbum on 2010-03-23
It's something to do with the BIOS. Fan control is done at the BIOS level by default.

If the fan noise gets too loud, you can always buy a Noctua CPU cooler; the fans there are so quiet you can have them on 100% and barely hear them. Some cases with restricted airflow will be noisier than others, too. Drilling a couple of holes in the side can help reduce noise.

---

### Post by Zerp64 on 2010-03-23
> **OriginalName said:**
> 
Just to note that I tried the "operating system" method of updating the BIOS and it failed so had to reset it, download and burn the CDROM method (a slightly older version of the update) and basically mess around with it till it worked. Not recommended if it's your only PC or you're not happy taking the side of etc... If it aint *that *broke I'd leave it alone!

Oh, I have no fear of breaking this old computer. I mean, one of the PCI slots nearly melted clean off after making my old video card smoke up... I'm not a hardware guy, but I know my way around.

So you guys think it's a BIOS problem, eh? Could something like this really just appear out of the blue with a BIOS that has otherwise been just fine?

---

### Post by Gadgetech on 2010-03-23
Are you using a stock CPU heatsink with the regular thermal interface pad that it comes with? 

I run on an aftermarket heatsink using Arctic Silver thermal grease. I find that it tends to melt away after a year or so and my CPU starts to run a bit hotter. 

A few minutes to clean up the old grease and re-apply and my quiet computer is back.

---

### Post by Zerp64 on 2010-03-23
> **Gadgetech said:**
> Are you using a stock CPU heatsink with the regular thermal interface pad that it comes with? 

I run on an aftermarket heatsink using Arctic Silver thermal grease. I find that it tends to melt away after a year or so and my CPU starts to run a bit hotter. 

A few minutes to clean up the old grease and re-apply and my quiet computer is back.

Now that could indeed be the problem... I swapped my CPU quite a bit ago and used the same brand of grease. Maybe I should reapply it. The problem is my heatsink is so hard to put back on that last time my thumbnail was torn off...

Oh, and for the guys thinking I need to flash my BIOS: I'm already running the latest version. I'm not sure how well motherboards react to a 'BIOS reinstall', or if it's even possible. Is it? On second thought, it's just another piece of software, isn't it...

---

### Post by 3rdalbum on 2010-03-23
> **Zerp64 said:**
> Now that could indeed be the problem... I swapped my CPU quite a bit ago and used the same brand of grease. Maybe I should reapply it. The problem is my heatsink is so hard to put back on that last time my thumbnail was torn off...

Oh, and for the guys thinking I need to flash my BIOS: I'm already running the latest version. I'm not sure how well motherboards react to a 'BIOS reinstall', or if it's even possible. Is it? On second thought, it's just another piece of software, isn't it...

A BIOS reinstall is completely unnecessary. Like Linux programs, the BIOS itself won't ever get opened read/write unless it is being updated, so there's no chance of corruption except when reflashing it.

---

### Post by Zerp64 on 2010-03-23
Couldn't be corrupted, do you think? I doubt it myself. Don't think a BIOS effort could be so specific that it does absolutely everything else perfectly except for managing fan speeds, especially all of a sudden.

So I'm going to try adding a new spot of thermal paste onto the CPU. Hopefully I can keep all of my fingernails this time.

---

