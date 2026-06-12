---
title: "Battery Life Reduction - eee PC 1000HE"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by rbscairns on 2010-02-07
I recently switched from the OEM XP to Ubuntu 9.10 on my eee PC 1000HE (Atom N280 1.66GHz CPU). My biggest surprise was the greatly reduced battery life with Ubuntu. With XP I was getting 8 to 8.5 hours under normal use with wifi on and bluetooth off. With Ubuntu clean install, this dropped to 5.5 to 6 hours in the same configuration.

I looked into Systems>Preferences>Power Management but found little there to be of much help, I then installed the Powertop utility. Powertop showed Power usage (ACPI estimate) of 10.7 W to 12.7W and suggested-
[LIST]
[*]Enable USB Autosuspend
[*]Increase the VM dirty writeback time from 5 to 15 seconds
[*]Enable SATA ALPM link power management
[/LIST]
Acting on these suggestions reduced the power usage to about 9.2W to 9.6W and increased the battery life accordingly to 6.8 to 7.5 hours. The problem with this is that it appears I need to run Powertop after each reboot to achieve this power saving.

I then reduced my display brightness down to 50% (about the lowest acceptable for me) and this lowered my power usage to about 8.7W to 9.1W, increasing battery life to 7.2 to 7.8 hours.

I have the CPU Frequency Scaling Monitor 2.28.0 utility installed and that has CPU usage set to "Ondemand". The minimum CPU frequency appears to be set at 1GHz. I can accept a CPU frequency of say about 750MHz if that will noticeably decrease power usage.

Ideally, I would like to get my power usage down to about 8.2W that will give me the original battery life I had in XP. So the questions are-
[LIST=1]
[*]Is there a way to automatically execute the Powertop suggestions at boot-up?
[*]Is there a way to lower the minimum allowable CPU frequency? (There is nothing available in the BIOS.)
[*]What other options are there available to me to decrease power used and increase battery life (besides turning the computer off :P)?
[/LIST]

---

### Post by acascianelli on 2010-02-07
I'm also very interested in lowering the CPU speed of the N280 in Linux.  I've been trying to do this for a month now with no success.

As for executing the changes suggested from powertop on boot, you could write a script then have it executed at bootup that would apply the changes.

I have an Asus 1005HA-P.

---

### Post by warfacegod on 2010-02-07
Have you actually tested these battery life times or just going by what the OS tells you? My laptop tells me I can run on battery in Linux for about 45 minutes and I can usually get about 90 minutes. When I had XP, it was the opposite. Windows would tell me I had about 2.5 hours and I'd get 45 minutes, if I was lucky.

---

### Post by mikewhatever on 2010-02-08
You could try and enable laptop mode. To do that, install laptop-mode-tools, then open /etc/default/acpi-support and make sure the following line ends with true:

ENABLE_LAPTOP_MODE=true

Then open /etc/laptop-mode/laptop-mode.conf, find the following line and change 0 to 1.

ENABLE_LAPTOP_MODE_ON_BATTERY=0

There are more settings in laptop-mode.conf, and under /etc/laptop-mode/conf.d, most of them pretty much self explanatory.

---

### Post by juancarlospaco on 2010-02-08
> **rbscairns said:**
> 
[*]What other options are there available to me to decrease power used and increase battery life (besides turning the computer off :P)?
[/LIST]

**xset dpms force off**

*make a panel launcher, usefull when you dont need to use the screen.*

---

### Post by mhpathfinder on 2010-02-10
As I am typing, and ocassionally highlighting my battery monitor, it sometimes reads 4 hours 45 minutes left, and jumps up to 5 hours or more left at times.  i've been at my eee pc 1000he since five a.m. this morning, beginning with a 9-cell battery at full charge. I have one of the utilities to control the EEE PC CPU power.  This one is called eee-control.  You can download the latest version at the eee-control developer website, [http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/).  It's a nice utility, and there are others like it that some of you are using.

My point here is that there is a fluctuation in the reading and actual battery time remaining as one is using their eee pc, which is to be expected.  If you click on a video, the projected life will decrease, as the auto over-clocker/under-clocker app responds to the power needs.  With eee-control I set it to "Powersave" and this seems to provide me with maximum time.  I've maxed out at between 7 and 8 hours, just typing text and reading.  This is very good.

Under normal use, which is usually a combination of reading, text-typing, web browsing with some video content, I expect the time to be less.  Turning off some of the other elements will obviously help, but unless I am on an extended international flight to some place, I can't imagine I would need eight to ten full hours of battery time.  I consider my present battery's potential and times to be quite impressive.  No need for MS Windows and their Super Hybrid Engine software.  Open source developers seem to have come up with some good and easy-to-use apps for LINUX-based systems.

---

### Post by bornagainpenguin on 2010-05-01
> **mhpathfinder said:**
> This one is called eee-control.  You can download the latest version at the eee-control developer website, [http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/).  It's a nice utility, and there are others like it that some of you are using.

How are you getting the eee-control powermanagement to work in Karmic\Lucid?

I have been able to get the application to install, have been able to get it to do hotkeys, but have utterly failed at making it do automatic cpu scaling like it did in Hardy, Intrepid, and Jaunty.  I have tried the one on the developer's site, the hacked versions in the PPA, etc none of them have been able to scale the machine automatically.  If I manually click it, the OSD tells me the scaling is active, but CPU scaling applet says that is a lie and the system still runs hot...  :/

--bornagainpenguin

---

### Post by jadymitchell on 2010-05-09
I think the answer to this is in his FAQ:

> I switched to high performance/powersave mode, but the CPU frequency scaling applet still shows the same frequencies and governor. Why?
While eee-control adjusts the FSB, the CPU frequency scaling applet is a frontend for cpufreq. FSB and cpufreq are two separate things. Furthermore, cpufreq cannot detect the FSB change and therefore still will display the original frequencies, even with the FSB underclocked/overclocked.

[http://greg.geekmind.org/eee-control/#faq](http://greg.geekmind.org/eee-control/#faq)

---

### Post by bornagainpenguin on 2010-05-10
> **jadymitchell said:**
> I think the answer to this is in his FAQ:



[http://greg.geekmind.org/eee-control/#faq](http://greg.geekmind.org/eee-control/#faq)

I am aware of that issue; the one I am having trouble with is the lack of automatic switching from normal to powersaving when I unplug the AC adapter.  In Hardy using the array.org kernel and eee-control unplugging the AC adapter resulted in an automatic switch to powersaving mode.  This does not happen for me in Karmic or in Lucid.  In those two versions of Ubuntu the only way to access the powersaving mode is by manually switching to it.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-07-26
> **bornagainpenguin said:**
> I am aware of that issue; the one I am having trouble with is the lack of automatic switching from normal to powersaving when I unplug the AC adapter.  In Hardy using the array.org kernel and eee-control unplugging the AC adapter resulted in an automatic switch to powersaving mode.  This does not happen for me in Karmic or in Lucid.  In those two versions of Ubuntu the only way to access the powersaving mode is by manually switching to it.

--bornagainpenguin

The latest version of eee-control fixes this issue.

--bornagainpenguin

---

