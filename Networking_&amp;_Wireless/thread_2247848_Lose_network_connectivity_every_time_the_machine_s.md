---
title: "Lose network connectivity every time the machine suspends"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by StephenG on 2014-10-10
Running 14.04 with the update of a day ago (10/9/14).  Since then, every time the computer suspends from inactivity, I lose my wired connection and have to reboot the system.  Has not happened before yesterday.  Is this a bug in the update?  Thoughts?

---

### Post by StephenG on 2014-10-20
Anyone???  Bueller??  Bueller??

---

### Post by jeremy31 on 2014-10-20
Try this fix
[http://ubuntuforums.org/showthread.php?t=2218043&p=13000035#post13000035](http://ubuntuforums.org/showthread.php?t=2218043&p=13000035#post13000035)

---

### Post by StephenG on 2014-10-21
Are you convinced that this should work even though I have no wireless on this machine at all?  I only have a cabled connection straight to the modem.  I also have other machines that run to this modem via a wireless router and they never seem to have the issue -- I suppose because they are Macs not Ubuntu.

---

### Post by ibjsb4 on 2014-10-21
I do not know what the problem is, but to save yourself some grief next time it happens.
```
sudo /etc/init.d/networking restart
```
That should make a reboot unnecessary until you get this resolved.

---

### Post by jeremy31 on 2014-10-21
You could try ```
sudo restart network-manager
``` after suspend and see if your network is back

---

### Post by StephenG on 2014-10-21
Thaks for that tip, j31.  I keep hoping that someone from the Ubuntu admin will let me know that it's a now known quirk and is being addressed in the next update.  Fingers crossed.

Oops, sorry ibjsb4, I didn't mean to dis you.  I didn't notice that your repoly wasn't j31's at first.  Thanks to you, too.

---

### Post by ibjsb4 on 2014-10-21
> **StephenG said:**
> Oops, sorry ibjsb4, I didn't mean to dis you.  I didn't notice that your repoly wasn't j31's at first.  Thanks to you, too.
ibjsb4 wipes tears from eyes :)

Good luck

---

