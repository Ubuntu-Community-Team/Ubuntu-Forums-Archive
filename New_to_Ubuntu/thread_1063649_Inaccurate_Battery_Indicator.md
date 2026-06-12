---
title: "Inaccurate Battery Indicator"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by daved2424 on 2009-02-08
I have just aquired a second-hand eee 900 running Ubuntu.

My battery indicator is woefully inaccurate. I have read that other people have had the same problem and most seem to suggest calibrating the battery in the BIOS but I cannot find this option.

Should I be calibrating the battery in teh BIOS? If so, how do I do it, if not, what should I be doing.

Many thanks for any help in advance.

---

### Post by GCoffee on 2009-02-08
In your BIOS settings (F11, DEL, F1, at start up) are there power options?

Im running a Dell Studio with 8.10 on and the battery seems fine.

GC.

---

### Post by Kellemora on 2009-02-08
Hi Daved

Technically, it's an impossibility to determine available battery power for more than a few days.  And it's harmful to a battery to try to find it's exhausted state with any accuracy at all.

As an example:
You have a brand new battery with an expected capacity of 1 hour usage time.  So a clock driven timer is set to 60 minutes upon recharge of the battery.  It may or may not have a self-calibration checksum to check load voltage at like 10 minute increments to see if the load voltage is holding within the softwares display parameters and adjust the display to show 40 minutes instead of 45 minutes left.

However, as your battery ages, it may only have a 45 minute or less total capacity.  Yet your display will still show 60 minutes left after a full recharge, because that is what is fixed in the software display program.  If it checks in 10 minutes and adjusts the display it may show only 30 minutes left, because it assumes a full life battery, not an old dying battery.

I've seen very few laptops that allow the user to CHANGE the battery life value so that the display is more accurate.  Meaning, if you know your battery now only lasts 30 minutes, you can change the display to show 30 minutes left after a full recharge.  Even then, the battery is still going downhill, so what was correct yesterday may not be correct tomorrow.

Even the super high tech battery life indicators that track power loss on a continuing basis are still only plus or minus 20% and were talking about on million dollar equipment where such devices are used.

With that in mind, I wouldn't think a cheaper device would have anything anywhere as accurate.

Hope that made a little sense????

TTUL
Gary

---

### Post by daved2424 on 2009-02-09
Thanks you for your help.

There are no power options in my BIOS. Hardly anything in my BIOS as a matter of fact.

I understand the problems with getting an accurate reading, its just my battery indicator goes from 90% to 20% in about an hour and from 20% to 0% in just over over. Very frustrating!

---

### Post by MrFX on 2009-03-05
But are there any alternative power managers? I replaced the gnome network manager with WICD because it works better with my wireless card.
Is there something I can do about the battery issue?

---

### Post by hesjnet on 2009-05-08
Bump! I am also experiencing this issue. Any ideas? the timer is just not working.

---

### Post by KevHed on 2009-05-08
Battery monitor for GNUstep 
Battery Monitor is a battery monitor for laptops. It displays the current status of the battery (charge/discharge and energy level) as well as some information about the general health of the cell.
Due to the way Battery Monitor is implemented it currently works only on linux 2.6 kernels with ACPI and that too reliably only on some acpi/bios combination (it is being worked on: the /proc file system is very inconsistent.) A user-contributed patch to make it work on FreeBSD has been merged in.

This application is provided by the Ubuntu community.
Homepage: [http://www.nongnu.org/gap/batmon/](http://www.nongnu.org/gap/batmon/)

Not sure if this is what you are using now or not.  This is available through the repos.

---

