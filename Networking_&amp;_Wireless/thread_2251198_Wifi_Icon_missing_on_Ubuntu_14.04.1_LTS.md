---
title: "Wifi Icon missing on Ubuntu 14.04.1 LTS"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by ockac23 on 2014-11-02
Hi,

I installed Ubuntu 14.04.1 LTS 64bit. Everything works fine. One small problem, the WiFi icon missing on the right side of the upper panel.
Wifi connection actually exists and is working, but only the icon is missing. Every time when I have to switch to another AP I have to go through the "System Settings" and "Network".

Anyone met this problem also? Any ideas how to solve this?

Many thanks in advance.

Regards

---

### Post by praseodym on 2014-11-02
Tried from terminal

**nm-applet**

??

---

### Post by ockac23 on 2014-11-02
praseodym, Yes and the otput is:

nm-applet-Message: using fallback from indicator to GtkStatusIcon


(nm-applet:4179): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
^Cnm-applet-Message: PID 0 (we are 4179) sent signal 2, shutting down...


(nm-applet:4179): GLib-CRITICAL **: Source ID 112 was not found when attempting to remove it

---

### Post by rackit on 2014-11-02
I had this issue on a laptop after an update about 3 weeks ago. Some of the other system tray icons were missing too. I installed the gnome desktop and all of the icons have returned to Unity.

---

### Post by ockac23 on 2014-11-03
There must be another way to resolve this issue......

---

### Post by grahammechanical on 2014-11-03
You can try this

```
killall unity-panel-service
```

That will kill unity-panel-service and it should restart automatically. If it does not.  Run this

```
/usr/lib/unity/unity-panel-service
```

I just tested the first command on my system even though I have all the icons i need. unity-panel-service did restart but it messed up the theme a little bit and a system restart set that right.

Regards.

---

### Post by ockac23 on 2014-11-04
Hi grahammechanical ,

I have tried 
[COLOR=#000000][FONT=Ubuntu Mono]killall unity-panel-service.
 
It restarted automatically, as you said. But the Wifi icon is still missing. :-(
[/FONT][/COLOR]

---

### Post by mark-lamorey on 2014-11-04
Indeed, I am having an identical problem - my wifi / network indicator has vanished.
Interestingly enough "system load indicator" does not show up either.

---

### Post by mark-lamorey on 2014-11-04
Indeed, I am having an identical problem - my wifi / network indicator has vanished.
Interestingly enough "system load indicator" does not show up either.

I just rebooted and it is still missing

---

### Post by ockac23 on 2014-11-10
Tried also:

sudo service network-manager stop 

sudo rm /var/lib/NetworkManager/NetworkManager.state

sudo service network-manager start


Still no success :-(

---

### Post by syed.zaib on 2014-11-14
I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

---

### Post by ockac23 on 2014-11-14
syed.zaib, thank you much, this has worked for me also!
Issue resolved! :-)

---

### Post by ejum on 2014-11-18
> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

thanks.. this one works for me too!!

---

### Post by Saranga_Abeykoon on 2014-11-29
> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

Thanks a lot. After trying many things, this worked at last.

---

### Post by Roger_Jr on 2015-02-16
**Thank you! This worked for me on the first try! Yesterday, I suddenly noticed my network icon was gone from the top of screen, thankfully this was a quick fix!**

> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

---

### Post by 9-vitaly on 2015-03-30
> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

Works like a charm. Thank yu!

---

### Post by josephinesbed on 2015-05-14
> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

-------
I had been dealing with this for a while in 15.04, and this resolved the issue. Thank you for sharing this.

---

### Post by Nikesh_Yadav on 2015-06-27
yes this work for me too.

---

### Post by diego-giglio on 2015-10-08
thank you so mach, it's worked fine to me. :D

> **syed.zaib said:**
> I was facing this very same issue. Please note that wireless was working fine all this time, its just the missing indicator icon. 

  Here is what worked for me. Unity -> Startup Applications - and  check "Indicator Application" (if its not already checked.) Next install  following two packages: indicator-applet and indicator-network.

```
sudo apt-get install indicator-applet indicator-network
```

reboot and wifi icon should pop-up. 
  I am using Ubuntu 14.04.1 64bit on Dell Inspiron 1564.

---

### Post by john541 on 2016-04-05
worked for me too

---

### Post by cqrity2 on 2016-11-03
> **grahammechanical said:**
> You can try this

```
killall unity-panel-service
```

That will kill unity-panel-service and it should restart automatically. If it does not.

Worked for me on 16.04 LTS 32-bit.

---

