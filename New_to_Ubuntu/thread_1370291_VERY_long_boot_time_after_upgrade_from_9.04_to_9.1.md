---
title: "VERY long boot time after upgrade from 9.04 to 9.10"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by markowe on 2010-01-02
I'll call this a beginner question, as I suspect I could fix this myself if I wasn't still very new to Linux. After upgrading (through the Update Manager rather than fresh install) from 9.04 to 9.10 I now have some boot items which get stuck until timeout and thus slow down boot time to some 6 minutes. Booting was fine before I upgraded, so something has happened there. Here are the offending sections from the log, but I can't get further with this on my own, so help appreciated:

```

....

[    2.899468] a4tech 0003:09DA:0006.0003: input,hidraw2: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:1d.7-2.4/input0
[    2.992288] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f7aae40f47c]
[  182.562196] PM: Starting manual resume from disk
[  182.562202] PM: Resume from partition 8:6
[  182.562205] PM: Checking hibernation image.
[  182.562401] PM: Resume from disk failed.

....

196.295994] Registered led device: iwl-phy0::TX
[  196.317028] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  199.358510] ppdev: user-space parallel port driver
[  294.463351] CE: hpet increasing min_delta_ns to 15000 nsec
[  314.685062] CE: hpet increasing min_delta_ns to 22500 nsec
[  368.881115]   alloc irq_desc for 32 on node -1

...

```I think these are the main two issues, the first one seems to be to do with trying to resume: I have not hibernated previously, but I think it always does that check anyway, and hibernation doesn't work anyway, have given up on that for now, but don't know why that step would take too long. This second issue, at 294.463351, I have no idea what that's about...

Much obliged.

Mark

---

### Post by duanedesign on 2010-01-02
The application 'bootchart' can help in diagnosing boot problems. I would install and run that. Attach to this thread the .png file from /var/log/bootchart/ after a fresh boot, that might help people in troubleshooting your issue.

---

### Post by markowe on 2010-01-02
Thanks for the suggestion - I thought the boot log would be more revealing than a bootchart, which is even more "Greek" to me! But if this can explain why the two long hangs, one at 1.3s and several at roughly 200-367s, I would appreciate the help. The second "hang" is actually a login prompt, no idea why that appears, but if I wait long enough the GUI fires up...

Click for bootchart:

[http://www.itsgottabered.com/media/mark-laptop-karmic-20100102-4.png](http://www.itsgottabered.com/media/mark-laptop-karmic-20100102-4.png)

---

### Post by ZeroSpawn on 2010-01-02
Check your start up apps, take out all the ones you don't need.

---

