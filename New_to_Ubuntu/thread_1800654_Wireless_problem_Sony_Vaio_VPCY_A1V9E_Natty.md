---
title: "Wireless problem Sony Vaio VPCY A1V9E Natty"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by nyaturu on 2011-07-09
Hi,

I am a complete Ubuntu beginner... hit a problem installing Ubuntu Natty 11.04 on a new Sony Vaio VPCY A1V9E: the network connections dropdown had "enable wireless" greyed out and nm-tool reported the WiFi card was unavailable. The card and connection worked without problems under the factory-installed Windows 7.

I couldn't find any help in forums or elsewhere for this problem in English, but then I found a report on a French forum which pointed me to the solution:
[http://forum.ubuntu-fr.org/viewtopic.php?id=467961](http://forum.ubuntu-fr.org/viewtopic.php?id=467961)
right at the bottom... in short, add the line 

blacklist acer-wmi

as the last line to /etc/modprobe.d/blacklist.conf (sudo gedit /etc/modprobe.d/blacklist.conf) and the problem is immediately resolved at the next reboot. 

Worked 100% for me, so I repeat it here in case other English-speakers hit a dead-end. Thanks to Nicococo64 and Jean49.

---

### Post by westie457 on 2011-07-09
Well done for getting it working and showing a solution for others.

Welcome to the forums.

Any other questions just ask.

---

### Post by schizm_studio on 2011-12-29
Worked perfectly on Sony vaio vpceg2dfx.
Thanks!

---

