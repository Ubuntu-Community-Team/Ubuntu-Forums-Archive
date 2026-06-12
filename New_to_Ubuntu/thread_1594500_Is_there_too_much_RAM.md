---
title: "Is there too much RAM?"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-10-12
I have an old presario with I think 128 or 256 RAM.  I would like to add, say 1 GB. Can there be too much RAM for a computer to handle? Quite new to messing with this stuff?


Thanks  :popcorn:

---

### Post by CharlesA on 2010-10-12
You would be best off looking up the owners manual or specs at the HP/Compaq site.

---

### Post by Grenage on 2010-10-12
> **Jolicoeur said:**
> I have an old presario with I think 128 or 256 RAM.  I would like to add, say 1 GB. Can there be too much RAM for a computer to handle? Quite new to messing with this stuff?


Thanks  :popcorn:

Absolutely; the older the board, the more likely you'll have problems.  Check the board model online.

---

### Post by Jerry N on 2010-10-12
The amount of RAM and the RAM technology depends on the age of the computer.  Many older machines could handle only 256mb and if the machine is old enough the type of RAM it uses might be out of production.  You could try crucial.com.  You can enter the computer part number and find out how much RAM your computer can use and the cost of that RAM from Crucial.  You can also let Crucial scan your computer but you probably have to be running Windows to make that work.

I have found Crucial to be a reliable company.

Jerry

---

### Post by CharlesA on 2010-10-12
+1 to Crucial.

---

### Post by fatality_uk on 2010-10-12
Big vote for crucial. Even if you don't buy it from their site, it will quickly give you details of what RAM is for pretty much any machine.

---

### Post by Jolicoeur on 2010-10-12
Thanks, Does Crucial have a way to scan linux?

---

### Post by CharlesA on 2010-10-12
> **Jolicoeur said:**
> Thanks, Does Crucial have a way to scan linux?

Not that I know of. You might be able to run it in Wine, but I doubt it.

You can always search by the model of the machine.

See [here]("http://www.crucial.com/store/drammemory.aspx").

---

### Post by cascade9 on 2010-10-12
> **Jerry N said:**
> The amount of RAM and the RAM technology depends on the age of the computer. Many older machines could handle only 256mb and if the machine is old enough the type of RAM it uses might be out of production. You could try crucial.com. You can enter the computer part number and find out how much RAM your computer can use and the cost of that RAM from Crucial. You can also let Crucial scan your computer but you probably have to be running Windows to make that work.

There is only 1 chipset I know of thats limited to 25MB- the 440EX chipset. 512MB is a far more common max RAM limit on older chipsets

> **Jolicoeur said:**
> Thanks, Does Crucial have a way to scan linux?

Not as far as I know. If the crucial 3 step 'what RAM do I need' is a bit to complicatied for you, it might be easier to opena  terminal, then run- 

sudo lshw

Then find the motherboard model in that list, copy and paste it here (in 'code' tags, to use tham hit the '#' symbol over where you post). 

Eg- 

```
description: Motherboard
       product: GA-770T-USB3
       vendor: Gigabyte Technology Co., Ltd.
```

That should give me, or somebody else, the info to tell you what RAM you need and how much you can install into your motherboard. ;)

---

### Post by Jerry N on 2010-10-12
> **cascade9 said:**
> There is only 1 chipset I know of thats limited to 25MB- the 440EX chipset. 512MB is a far more common max RAM limit on older chipsets


The three Pentium 233-400 mhz class machines I have kicking around are definitely limited to 256MB RAM.  I don't know what chipsets - one is an HP Pavilion with 366mhz Celeron, one is an IBM Aptiva, 400mhz I think, and the other one, considerably older, has a Tyan MB and a 233mhz Pentium.  These are, of course, grossly out of date computers. 

Jerry

---

### Post by QLee on 2010-10-12
> **Jerry N said:**
> The three Pentium 233-400 mhz class machines I have kicking around are definitely limited to 256MB RAM.  I don't know what chipsets - one is an HP Pavilion with 366mhz Celeron, one is an IBM Aptiva, 400mhz I think, and the other one, considerably older, has a Tyan MB and a 233mhz Pentium.  These are, of course, grossly out of date computers. 
...

Jerry, those first two will be Pentium II (likely they are slot CPUs), the 233 will probably  be a Pentium I. The P1, isn't going to have 256. I wouldn't be at all surprised to see the P2s limited to 256, My old Aptiva only had two slots and an 128 DIMM was a lot of memory in those days, most systems shipped with 32 or 64. 

You could probably run Ubuntu on the P2s, just. However, I think you would not find it to be a good user experience, although, you'd probably have time to make yourself a coffee while you were waiting for boot. I suggest you stay away from the big desktop environments if you choose to try. The P2s might make useful servers, without X. The P1 could still be used as a separate hardware NAT/Firewall if you have use for one of those, I'm running one on a P1, 166, 64MB.

---

### Post by Jerry N on 2010-10-12
> **QLee said:**
> Jerry, those first two will be Pentium II (likely they are slot CPUs), the 233 will probably  be a Pentium I. The P1, isn't going to have 256. I wouldn't be at all surprised to see the P2s limited to 256, My old Aptiva only had two slots and an 128 DIMM was a lot of memory in those days, most systems shipped with 32 or 64. 

You could probably run Ubuntu on the P2s, just. However, I think you would not find it to be a good user experience, although, you'd probably have time to make yourself a coffee while you were waiting for boot. I suggest you stay away from the big desktop environments if you choose to try. The P2s might make useful servers, without X. The P1 could still be used as a separate hardware NAT/Firewall if you have use for one of those, I'm running one on a P1, 166, 64MB.

I'm drifting off topic here but one of the reasons I first tried Linux was to see if I could rejuvenate these old computers into something useful.  So far, I consider the experiment to be a failure. I tried dozens of Linux variations, including those that claimed to be "light" and have failed to find a one that I would consider to be satisfactory.  DSL probably worked the best but what a kluge!  Xubuntu 6.06 LTS might have been minimally acceptable but I never did get it to print, either directly or on a networked printer.  Legacy OS is showing some promise but the second time I re-booted it failed to start the GUI and I have been too busy to get back to it.  Windows 2000 works very well on all these machines but my target was a non Windows environment.  I have modern computers to play with and fiddling with those old machines is just kind of a fun side activity.    

Jerry

---

### Post by cascade9 on 2010-10-12
Opps, I forgot, there are other P2/P3 chipsets that were limited to 256MB, but they were mobile chipsets (440ZX-M, 440MX). 

> **Jerry N said:**
> The three Pentium 233-400 mhz class machines I have kicking around are definitely limited to 256MB RAM. I don't know what chipsets - one is an HP Pavilion with 366mhz Celeron, one is an IBM Aptiva, 400mhz I think, and the other one, considerably older, has a Tyan MB and a 233mhz Pentium. These are, of course, grossly out of date computers. 

Jerry

The P2s could be running the 440EX chipset. Or you could have hit the 'only has 2 slots, the slots will only take 128MB sticks' problem, which is more of a manufacturering/BIOS issue than the chipset. Not that it mkaes much diference to an end-user.....

> **QLee said:**
> Jerry, those first two will be Pentium II (likely they are slot CPUs), the 233 will probably  be a Pentium I. The P1, isn't going to have 256. I wouldn't be at all surprised to see the P2s limited to 256, My old Aptiva only had two slots and an 128 DIMM was a lot of memory in those days, most systems shipped with 32 or 64. 


The P1 *could* have 256MB+. If its an itel chipset, its not going to like it much. Quite a few P1 intel chipsets went to 128MB+, but apart from 2 expensive server chipsets they were normally limited to 64MB cacheable......running 64MB+ on chipsets limited to 64MB cacheable could actually be slower than 64MB.

The VIA P1 (OK, socket 7/super socket 7) chipsets normally went to 512MB cacheable, but that was with 2MB on-board cahce, with 1MB it was 256MB cacheable, and with 512k (the most common onboard cache) 64MB cacheable.

---

