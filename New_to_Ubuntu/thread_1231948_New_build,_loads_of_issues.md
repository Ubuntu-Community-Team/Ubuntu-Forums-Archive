---
title: "New build, loads of issues"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by pissedoffdude on 2009-08-05
I've recently put together a new rig with the following specs:
GIGABYTE GA-EP45C-UD3R
Intel Core 2 Quad Q9550 @ 2.83Ghz
EVGA GeForce 9800GTX
4gbs mushkin ddr3 ram
2 640gb Western Digigal hdd's
20x Sony DVD+/-R SATA
750watt Corsair PSU

This rig has given rise to problem after problem. The entire system hard-locks randomly (but it seems to do it like 100% of the time when doing large data transfers) and the only option is to manually power down or reboot.  Sometimes firefox will close at random.  I don't know if this has anything to do with the problems mentioned above, but about a week ago after putting it together, my usb mouse and keyboard would not be usable until 5 minutes after booting any os.  Also, the computer would not shut down and ubuntu would report some usb errors.  These errors were fixed by unplugging my card reader, but other issues still persist.  I'm also getting some i/o errors when trying to transfer files to a fat32 partition on one of my hdd's.  I am not 100% certain, but I do not think it is an os or hdd issue, as I have 2 os's on separate hdd's and both are having the same issues.  Does anybody have any ideas on where I could start? Thanks

---

### Post by automaton26 on 2009-08-05
With random system crashes, always try memtest first (from the boot menu) for a number of complete cycles.

After that, you might want to:
[LIST]
[*]disconnect all non-essential hardware, to reduce the number of possible problems.
[*]see if there's a BIOS update for your motherboard manufacturer (probably needs to be run from within a Windows installation).
[*]fully check your hard drives for errors (if either drive is USB external, make sure they are connected to a separate power adapter if possible).
[/LIST]

---

### Post by indytim on 2009-08-05
From the 30,000 foot vantage point, you might be having hardware problems.  A couple of the 101's:

1.  Run a memory check (never heard of "mushkin" ram).
2.  Check the bios rev and tech alerts on your motherboard.

IndyTim

---

### Post by tom66 on 2009-08-05
Make sure your PSU is up to spec (is 750 watts (I assume Corsair 750 is 750 watts) enough with two HDDs, a powerful processor, a powerful graphics card, and accessories?) Run without one HDD, remove CD drive, and put an older graphics card in or use the built in one to see if the system is stable. If so it might be you're drawing too much power from the PSU or it isn't regulated enough.

Make sure your RAM is OK, test it using memtest86. 

Install lm-sensors and see the readings for the voltages and the temperatures - check these are in spec. Not all motherboards have sensors so you might need a multimeter as well; use this to measure voltage from a spare drive connector and check it's within 5% for both 5v (red) and 12v (yellow).

---

### Post by pissedoffdude on 2009-08-05
Thanks for the suggestions guys.  I did run a memtest earlier today for about 9 hours and it reported no errors.  Also, I installed the latest bios yesterday, but it doesn't look like it has improved the situation.  I will try disconnecting an hdd and I'll swap the graphics card with an old one to see if it makes a difference.  If you guys have any more suggestions, keep 'em coming :D

---

### Post by wizard10000 on 2009-08-05
Hardware geek walks in, looks around, waves to the crowd  :)

750w is more than enough juice to drive that computer.  Newegg's got a link to a pretty good power supply calculator here

[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

Mushkin RAM is generally pretty high-quality stuff.

You'll most likely need to install the current lm-sensors.  I know that with my i7 920 I had to use the latest and greatest as the version of lm-sensors in the repos is v1.x and current is v3.x  - had to satisfy some dependencies (bison and I think one other) but I got it working without too much trouble.

[http://www.lm-sensors.org](http://www.lm-sensors.org)

Is that Core2 Quad running at stock frequency and voltage?  Is RAM timing and voltage within specs?

---

### Post by Bölvaður on 2009-08-05
Please narrow down where the problem may lie

1. Harddisk problem, run only on live cd
2. Software problem, install another distro that uses a different desktop environment and set of applications
3. Install ubuntu again on a different filesystem

actually... this should give you pretty good idea what is going on.

If the computer freezes on 1, then you need a better hardware possibly... should try 2 though, could be data curruption when you burned the cd or downloaded the iso

If 2 then it is probably not software related unless if the problem lies either in drivers or... drivers

3. if it breaks here also then it is either software or some of your hardware is broken.

---

### Post by XCan on 2009-08-05
> **wizard10000 said:**
> Hardware geek walks in, looks around, waves to the crowd  :)

750w is more than enough juice to drive that computer.  Newegg's got a link to a pretty good power supply calculator here

[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

Mushkin RAM is generally pretty high-quality stuff.

You'll most likely need to install the current lm-sensors.  I know that with my i7 920 I had to use the latest and greatest as the version of lm-sensors in the repos is v1.x and current is v3.x  - had to satisfy some dependencies (bison and I think one other) but I got it working without too much trouble.

[http://www.lm-sensors.org](http://www.lm-sensors.org)

Is that Core2 Quad running at stock frequency and voltage?  Is RAM timing and voltage within specs?

+1. 750 W is totally overkill for that rig so the PSU won't be an issue. Mushkin RAMs are good, however, have you checked that they are getting fed with the correct voltage? A lot of these high-end RAMs run at a slightly higher voltage than the default modules.

---

### Post by pissedoffdude on 2009-08-05
Thank you guys so much for the help.  After increasing the ram voltage from 1.50 to 1.86 and setting the correct timings, it's been running without a hard-lock or crash.

---

