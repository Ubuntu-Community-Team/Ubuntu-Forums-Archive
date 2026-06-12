---
title: "Trackpoint sensitivity returns to default when resuming from suspend"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by AncientPC on 2009-05-03
In order to modify my Thinkpad X61s trackpoint I used [configure-trackpoint]("http://tpctl.sourceforge.net/configure-trackpoint.html") and it works fine.  It updates the current sensitivity settings and writes the value out to /etc/sysfs.conf.

However whenever I resume from suspend or hibernation, the trackpoint sensitivity is back to default (extremely slow) despite the fact that /etc/sysfs.conf reports the correct sensitivity.  I have to rerurn configure-trackpoint to set the current sensitivity back to my preferences.

Edit: This is on 9.04 32b x86.

---

### Post by camper365 on 2009-05-09
I have a similar problem on a t43.
However, when I resume from standby or hibernate, I can't even get to configure-trackpoint.
It tells me:
```
Trackpoint is not detected, please check your kernel and trackpoint driver.
```

---

### Post by AncientPC on 2009-05-09
I have to reload psmouse module upon resuming from suspend/hibernate in order to get scrolling working again.  You may want to see if it helps you as well: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Reactivate_Scrolling_after_suspend.2Fresume](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Reactivate_Scrolling_after_suspend.2Fresume)

---

### Post by teramind on 2009-05-23
That does'nt work at least on a T41. I have to type

 echo -n "250" > /sys/devices/platform/i8042/serio1/serio2/sensitivity

as root after every reboot. That is annoying.

Under 9.04 ...one can write the echo command into /etc/rc.local.

---

### Post by kchen on 2009-05-23
Quick question: I've been having problems modifying sensitivity, speed, etc.

Every time I enter:
echo -n "250" > /sys/devices/platform/i8042/serio1/serio2/sensitivity

I get a message saying "permission denied." I've tried this with sudo as well. I'm running Jaunty (kubuntu) and never encountered this problem in Intrepid. Would you happen to have any solutions? This is a clean install.

Thanks!

---

### Post by camper365 on 2009-05-23
I have found that it works fine for me now, I guess I downloaded some update and it fixed it.

---

### Post by vukasin0 on 2009-07-01
Hi,

I've created simple script in /etc/init.d/trackpoint:

Become root:
sudo -s

Create script:
vi /etc/init.d/trackpoint

```
#! /bin/sh
echo -n "250" > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```

make it executable:
chmod +x /etc/init.d/trackpoint

make it execute in startup:
update-rc.d trackpoint defaults


It works after reboot or normal startup but not after resume from standby.
Any idea?

---

### Post by AncientPC on 2009-09-04
This issue has been solved with a kernel update.

---

### Post by habskilla on 2009-09-13
This is my version:
2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

After reboot, I still lose all my settings. What patch do I need?

---

### Post by cdoss on 2009-09-27
Me too (everything works fine upon restart; upon resume from suspend, my trackpoint-scrolling-with-third-mouse-button is horibly slow, although scrolling with the touchpad is fine).
I'm running 8.10 on a lenovo t61:
~$ uname -r
2.6.27-14-generic

Sorry to ask a newbie question, but:
So if this is only fixed with a kernel update, would I need to upgrade back to 9.04 to get this fixed?  (I just downgraded from 9.04, which works too poorly with my lenovo, graphics, powermanagement, problems i cant solve, for me to function).  Can i do a kernel update but not update the version?  Are there any easier fixes?

---

### Post by jblackhall on 2009-10-25
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

### Post by undoIT on 2010-05-21
I have tried every single method that is available online to fix this in Kubuntu Lucid with ThinkPad T410s so that the sensitivity is customized, but nothing works. I have tried udev, sysfsutils, rc.local and the script posted by vukasin0. Forget about suspend, it doesn't even work after reboot. This is crazy.

Is there any way to get Ubuntu Lucid to stop resetting trackpoint sensitivity after every reboot?

---

### Post by pgriffiths on 2010-05-26
You *should* be able to set speed and sensitivity by adding a rule in /etc/udev/rules.d.  However due to a kernel bug [(http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549379)]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549379"), the rule gets triggered before the speed or sensitivity attributes exist.  As a work around, you can add a WAIT_FOR condition.  I set the speed and sensitivity using /etc/udev/rules.d/trackpoint.rules with a single line:

SUBSYSTEM=="serio", DRIVERS=="psmouse", ATTR{description}=="Synaptics pass-through", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity" ATTR{sensitivity}="220", ATTR{speed}="160"

You might also add a WAIT_FOR the speed attribute, but waiting on one  works fine for me.

---

### Post by lophiomys on 2010-12-09
Kubuntu 10.04 LTS all updates on a Thinkpad T42p 2373-KYG, with UltraNav

I've tried it as described:
If you don't look out carefully for the correct device path, and test as advertised with
```
sudo udevadm test /sys/devices/platform/i8042/serio1
```
you are getting an error, 
with my configuration, it should be
```
hal@T42pUXGA:~$ sudo udevadm test /sys/devices/platform/i8042/serio1/serio2
```
(note the serio2 at the end)


Trivial but still a pitfall.
HTH

---

### Post by McBraid on 2011-01-20
I'm having a problem on a T410i running Ubuntu 10.10. The WAIT_FOR code is working on startup, setting the speed and sensitivity according to the values in trackpoint.rules. However it is not applied after suspend.

I tried adding another WAIT_FOR for speed by writing:

SUBSYSTEM=="serio", DRIVERS=="psmouse", ATTR{description}=="Synaptics pass-through", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/speed" ATTR{sensitivity}="220", ATTR{speed}="160"

Did not work.

So i tried to replace sensitivity with speed:

SUBSYSTEM=="serio", DRIVERS=="psmouse", ATTR{description}=="Synaptics pass-through", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/speed" ATTR{sensitivity}="220", ATTR{speed}="160"

Did not work.

Am I doing something wrong here or is this fix not working in 10.10?

---

### Post by McBraid on 2011-01-20
Sorry, double post.

---

### Post by pgriffiths on 2011-01-21
Check whether udevadm test /sys/devices/platform/i8042/serio1 (substituting your appropriate path) corrects the problem after suspend.  WAIT_FOR has a 10s timeout period which might not be enough. ([http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev/udev.html](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev/udev.html))   I have occasionally seen the setting fail to hold, possibly due to a timeout. However, I have not tried this on 10.10.

---

