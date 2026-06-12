---
title: "Enabling AMD Cool 'n' Quiet on an HP dv5?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Adamantus on 2008-12-13
Hey,

Whenever I unplug my computer, it's been running down the battery really quickly and making a loud noise. I was looking through google and realized it is probably because I don't have AMD's Cool 'n' Quiet enabled. I just recently came over from Vista and the battery life was longer and noise from the computer was much lower (because CnQ comes enabled).

Anyway, I can't really find out how to enable this driver on my computer. I've downloaded the driver from AMD but don't know really what to do with it. I've seen in a couple places that new versions of Ubuntu come with it installed, but I don't know how to enable it. I've gone into the BIOS and the closest thing I can find is "Keep fan on at all times" but no "enable cool 'n' quiet". Does anyone have a similar computer that has been able to use it?

---

### Post by Michaelg14 on 2008-12-13
Might not help but check your BIOS settings.  I have an AMI BIOS and there is a setting to enable Cool & Quiet.

---

### Post by uniqueumang on 2008-12-13
Umm...since you got DV5, can I ask you is your wireless working fine. Sorry mine isn't....

Thanks

---

### Post by Michaelg14 on 2008-12-13
There is a "cpu frequency scaling monitor" panel app that will tell you what your cpu is running at.  Mine varies from 41% to 100%.  It will also tell you actual frequency if you want it to.  Most of the time mine is at 41%.

---

### Post by Adamantus on 2008-12-13
When I try to add the CPU Frequency thing to my panel, I get this:

CPU Frequency Unsopported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

And typing cpufreq-info into a terminal gets this:
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

When the CPU regulator shows up on my panel, it says it's constantly at 100%. And I've checked everywhere in the BIOS and there's nothing about Cool 'n' Quiet there.

To uniqueumang:

I just got it working. It actually wasn't that hard using Madwifi, but the wireless button will stay orange whether the wireless is on or off (not a big deal for me). I can't remember the link I used, but it was something like what the guy says here ([http://ubuntuforums.org/showthread.php?t=921329]("http://ubuntuforums.org/showthread.php?t=921329")), without the mkdir part. And when it had me change directory to the madwifi directory, I actually found that my directory was called something different. Sorry I can't be much help, I'm a pretty big newb.

---

### Post by Michaelg14 on 2008-12-14
I haven't tried it but there is an app in Symantic called emifreq-applet that says it controls the cpu frequency.  You might look into it.

---

