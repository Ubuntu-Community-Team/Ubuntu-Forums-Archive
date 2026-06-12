---
title: "How to restart iwlwifi after it crashes?"
date: 2018-09-02
forum: Networking &amp; Wireless
---

### Post by MisterPi on 2018-09-02
As I mentioned in another thread ([https://ubuntuforums.org/showthread.php?t=2400115&p=13797346#post13797346](https://ubuntuforums.org/showthread.php?t=2400115&p=13797346#post13797346)), my Intel Wireless 7265 just crashed due to a Microcode SW Error reported to syslog.  At that point, the wireless just disappeared.  It no longer showed up in "rfkill list" and any attempt to bring the interface up, e.g., with

sudo ifconfig wlp1s0 up

failed because wlp1s0 was no longer recognized.

So, short of rebooting, what do I need to do to get the interface recognized and up again?

(See the other thread for the attached syslog file.)

---

### Post by jeremy31 on 2018-09-02
Duplicate thread closed, please include all info on the other thread

---

