---
title: "HP DV6T-6100 CTO HDD Runs Hot (Ubuntu 11.04 x64)"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by adoster on 2011-08-02
Hi all, this is my first post in the beginner's forum.

I recently installed Ubuntu 11.04 on my new laptop, an HP DV6T-SE (a DV6T 6100 CTO for driver reference) and the bottom left of my laptop, where the HDD is, runs hot to the touch when I'm using Ubuntu 11.04 64-bit. 

Comparable to the same time and resource usage on Windows 7, when on Ubuntu 11.04 my laptop is unusually hot where the HDD is. I Googled it, and the most relevant topic that showed up was a thread started in the Ubuntu forums discussing some sort of 'kernel bug' issue with v11.04 causing the *CPU *and* GPU* to run hot while the *battery* was being dangerously drained quickly, but there didn't seem to be documentation for issues with hard drives.

I really want to learn how to use Linux, but I am wary of jeopardizing my brand new laptop's hardware health and its battery. Any insight would be appreciated, I will include a link to the mentioned 'kernel bug' thread.

[http://ubuntuforums.org/showthread.php?t=1745389](http://ubuntuforums.org/showthread.php?t=1745389)

System Information:

2nd generation Intel(R) Dual Core(TM) i5-2410M (2.3 GHz, 3MB L3 Cache) with Turbo Boost up to 2.9GHz       

6 GB DDR3

Integrated Radeon HD 3000 GPU

640 GB Hitachi HTS547564A9E

---

### Post by cbennett926 on 2011-08-02
NO WAY! I have the same computer and the same problem, I installed a temperature sensor and it reads that it is running at 50 degrees celsius, which is kinda toasty but high is 95 so it isn't too bad. I think it's that Ubuntu doesn't know how to properly utilize the cooling drivers.

---

### Post by wildmanne39 on 2011-08-03
Hi, also use a chilling pad. Make sure you are not covering the fans,you should use it on a flat surface. Here is a link that might help.

Read post #4.

[http://ubuntuforums.org/showthread.php?p=10821788#post10821788](http://ubuntuforums.org/showthread.php?p=10821788#post10821788)

---

### Post by Mark Phelps on 2011-08-03
I would agree that a chilling pad will help cool down the laptop -- a bit.  

But, in the long run, you're damaging your components due to overheating.  You would do better staying away from Ubuntu until that bug gets addressed.

---

### Post by adoster on 2011-08-03
Thanks for the responses, I wasn't planning on using my laptop until there was a solution to this problem anyways. I just wanted to know if there was already a fix out. 

In response to the laptop cooling mat suggestion, I am running a large $40 3-fan elevated Targus mat that can keep laptops sufficiently cool, but it won't be able to do anything in the long run against a kernel/driver issue. How will I know if a fix has come out for this issue--where would I check?

 Hope this gives insight on anyone else who's having the same problem.

---

### Post by cbennett926 on 2011-08-03
I'm not sure if I can tell if mine is actually having an issue, it does feel hot/warm but only after prolonged use. I too would like to know when and where I can check

---

### Post by adoster on 2011-08-04
> **cbennett926 said:**
> I'm not sure if I can tell if mine is actually having an issue, it does feel hot/warm but only after prolonged use. I too would like to know when and where I can check

My laptop usually runs hot after only ~20 minutes of very light usage (Firefox & Ubuntu Software Center).

Do older versions of Ubuntu (10.xx?) have the same issues with laptop overheating?

---

### Post by adoster on 2011-11-16
Has there been any recent development or progress concerning this issue? Sorry if this counts as "bumping" your own thread, but I haven't posted for quite a while.

---

### Post by erikschmitz on 2012-01-08
I don't think this is a hard drive problem... I have an HP DV6t-6000 Quad Edition. It runs hot and sucks power because both your Intel and AMD graphics chips are turned on and running full bore. 

I've only been able to ever get the Intel graphics to work, but they work swell. Add this line to /etc/rc.local, it tells your computer to shut off the radeon gfx at boot.

```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

after adding this, my rig runs nice and cool and the battery life is exceptional (~8 hours on the 9cell battery).

---

