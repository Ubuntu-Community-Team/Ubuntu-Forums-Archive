---
title: "Lenovo Yoga Slow Wifi"
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by BobbySoSlo on 2016-11-04
Hi Ubuntu Forums people, really hoping someone can help me out.

**Wireless info attached**:
[ATTACH]271964[/ATTACH]

**Behavior**:
Wifi works normally from home but has terrible speeds from the office space my company works out of.

The connection speed on my phone is ~25dwn/25up whereas my laptop hovers around 0.5dwn/0.1up while connected to the same wifi.

I've noticed my phone seems to have a higher signal strength than my laptop (which is always pretty weak) so possibly it's an access point issue?
I've tried moving around to different locations in the building but that hasn't shown to help.

This thread from another Yoga user coincidentally was just posted: [https://ubuntuforums.org/showthread.php?t=2342154](https://ubuntuforums.org/showthread.php?t=2342154)
The power management off change didn't seem to help.

I've gone through a few guides but haven't found anything that worked, please help and thank you very much.

---

### Post by BobbySoSlo on 2016-11-07
Any chance someone has time to help me debug this?

Thank you,
Robert

---

### Post by Hadaka on 2016-11-07
Hi, please keep in mind that your portable Walkie-talkie/cell-phone isnt ubuntu 16.04
and likely not linux. Also you have no control over the connection configuration at work like
you do with your own personal router, so I suspect the problem is with the settings of your office/work
access point and probably not your Unubtu settings.
Here are some things that may help...
Please open a terminal ...ctrl/alt/t...and do..
```
sudo modprobe -rf ideapad-laptop
sudo modprobe -rf rtl8xxxu
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rfkill unblock all
```
Boot and test wireless

Once you are home..from a wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
Thanks.

---

