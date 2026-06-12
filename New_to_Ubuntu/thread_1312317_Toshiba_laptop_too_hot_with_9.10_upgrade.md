---
title: "Toshiba laptop too hot with 9.10 upgrade"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Qazase on 2009-11-03
I had no problems running 9.04 but since upgrading to 9.10 my Toshiba laptop is constantly hot. Any help?

Specs for the laptop are:
T5450 @ 1.66 HGz
Intel core 2 Duo CPU
need to know anything else?

Also since upgrading I have been unable to print to my Lexmark x2650 printer, which I had no problem doing so with 9.04.

Qaz

---

### Post by NickJones on 2009-11-03
Nothing over clocked? Did you re-set your Bios when booting off a CD? Did you install anything that would cause it to run overly hard?

---

### Post by Peter09 on 2009-11-03
Use htop, it in the repositories, to see if you have any task which is running with high cpu load.

---

### Post by TheForumTroll on 2009-11-03
Why not just use gnome-system-monitor?

---

### Post by Xatolos on 2009-11-03
I found the same issue with my laptop was fixed when I added this:

"
2. Add the following to your /etc/modules: (sudo gedit /etc/modules)
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace
"

I found it in this thread:
[http://ubuntuforums.org/showthread.php?t=539365&highlight=laptop+runs+hot](http://ubuntuforums.org/showthread.php?t=539365&highlight=laptop+runs+hot)
Someone claims that the commands are no longer needed but after I did that and restarted I noticed a difference from the start. Also made the fan stop screaming all the time. 
Granted do this at your own risk.
Good luck

---

