---
title: "I have a screenshot of my laptop overheating"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Tony.B on 2010-03-30
I hope this error message will help the clever people at Ubuntu to solve this problem that many people seem to have:

---

### Post by KIAaze on 2010-03-30
You should report this as a bug on Launchpad:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Note: I found this by googling for your error message:
[http://superuser.com/questions/26149/lm-sensors-cant-get-cpu-motherboard-temperature-fan-speed](http://superuser.com/questions/26149/lm-sensors-cant-get-cpu-motherboard-temperature-fan-speed)
Maybe it helps.

---

### Post by Tony.B on 2010-03-30
Thanks for the prompt response, KIAaze.

> **KIAaze said:**
> You should report this as a bug on Launchpad:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
I tried following this link which appears to be out-of-date.  It directs me to the main Help Menu where it says I'll find an option saying &#8220;Report a Problem&#8221;.  But this option is no longer there.

> **KIAaze said:**
> Note: I found this by googling for your error message:
[http://superuser.com/questions/26149/lm-sensors-cant-get-cpu-motherboard-temperature-fan-speed](http://superuser.com/questions/26149/lm-sensors-cant-get-cpu-motherboard-temperature-fan-speed)
Maybe it helps.
Thank you for taking the trouble to Google this.  It might indeed have helped me if I understood it all.  But I must confess to being a bit put off by the last entry, 7 months ago, which suggested that this is "an old, old post from 2004, with steps that are not needed now&#8221;.

I'm sorry I don't have sufficient computer know-how to make better use of your suggestions.

Cheers,
Tony

---

### Post by KIAaze on 2010-03-31
First of all, you talk about overheating, but what makes you say it's overheating?
Does it suddenly shut down by itself?
Because the screenshot only shows a sensor problem.

==========
Concerning your previous post:

The following command should still work:
```
ubuntu-bug
```
Run it from a terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

If it doesn't work, you can always report the bug online directly:
[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)
I suggest "lm-sensors" as package.
You can either run:
```
ubuntu-bug lm-sensors
```
or report directly on:
[https://launchpad.net/ubuntu/+source/lm-sensors/+filebug](https://launchpad.net/ubuntu/+source/lm-sensors/+filebug)

Also, if your computer is old, **make sure it's not overheating because of all the dust inside!**
This happened to me once.
An easy way to notice this is the case is that it overheats with other operating systems (ex: Windows) too when you run anything requiring a lot of processing power.

From the link I posted, the best answer seems to be the first one.
Have you tried running:
```
sudo apt-get --purge remove sensors-applet
sudo apt-get install sensors-applet

```
?

And the device support page to see if your device is supported?:
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

Note: This probably won't fix the overheating issue itself, but it would help fix/understand the sensor problem.

---

### Post by iponeverything on 2010-03-31
KIAaze has very good point, you this very well could be an issue with lmsensors working with your hardware.

Here is how I would use google to research your problem and to look for help on the forums.

Needed information -- 

Laptop model 
Ubuntu Release
Symptoms, errors and history

There are way to many unknown variables to give someone a decent shot at helping you diagnose your issue.

---

### Post by Tony.B on 2010-04-01
Thanks for coming back to me KIAaze.  I apologise for my slow response: I've had internet connection problems here in sunny South Africa.

> **KIAaze said:**
> First of all, you talk about overheating, but what makes you say it's overheating?
Does it suddenly shut down by itself?
Because the screenshot only shows a sensor problem.

The reason I'm certain it's an overheating problem is that we've worked through this in a long saga on previous threads:
[INDENT][http://ubuntuforums.org/showthread.php?t=1304612](http://ubuntuforums.org/showthread.php?t=1304612)
[http://ubuntuforums.org/showthread.php?t=1428223](http://ubuntuforums.org/showthread.php?t=1428223)
[http://ubuntuforums.org/showthread.php?t=1431412](http://ubuntuforums.org/showthread.php?t=1431412)[/INDENT]

The sensor problem shown on the screenshot is something I have discovered since then - I merely thought that it might assist the Ubuntu software engineers to solve a commonplace problem.

I don't know if this screenshot is significant (or, indeed helpful) but I've posted it here on the Forum because I don't know of a better place to bring it to the attention of the right people.

I hope all this makes sense.

Thanks again,
Tony

PS: Thank you also for the link to *[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)*.  What at interesting site - I wish I'd seen it before.

---

### Post by Tony.B on 2010-04-01
Thank you for your interest, iponeverything.

> **iponeverything said:**
> KIAaze has very good point, you this very well could be an issue with lmsensors working with your hardware.

Here is how I would use google to research your problem and to look for help on the forums.

Needed information -- 

Laptop model 
Ubuntu Release
Symptoms, errors and history

There are way to many unknown variables to give someone a decent shot at helping you diagnose your issue.

My laptop is an Acer Aspire 5315, and I'm running Karmic 9.10.

I had no problems when I was running Windows Vista, or when I "upgraded" to Ubuntu Jaunty 9.04. In fact I **still** get no problems if I switch to Vista, apart from the fact that I can make a cup of coffee before it finishes booting up :wink:
So that inclines me to believe that Ubuntu is at fault, not my computer.

At first I didn't realise it was an overheating problem, and I posted merely that my system was shutting down unexpectedly *(see [http://ubuntuforums.org/showthread.php?t=1431412](http://ubuntuforums.org/showthread.php?t=1431412))*.  But after researching this forum and googling elsewhere, it became apparent that my fan wasn't kicking-in from a cold start.  As soon as everything has "boiled over", I can restart without problems.

The error message started to appear only since I installed the Core Sensor Applet (before this, the computer still switched off, but I had no idea why).  

I'm not by any means computer-literate, but I thought that posting a screen-shot might assist with finding a solution to this problem, which seems to affect many Ubuntu users.

Cheers,
Tony

---

