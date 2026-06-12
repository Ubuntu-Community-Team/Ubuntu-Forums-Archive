---
title: "Device drivers in Ubuntu Server 8.10"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by zolthar on 2009-01-03
Hi guys, is there an option like in MS to view all device drivers?

Installed Ubuntu first time and everything seems to "just work" out of the box and its concerning!

Thanks in advance.

---

### Post by cariboo on 2009-01-03
I'm not sure what it is you want, but if you want to view the installed modules at the prompt type:

```
lsmod
```

If you want ot see all the modules(drivers) available go to /lib/modules/<your kernel version>/kernel.

Jim

---

### Post by linux_tech on 2009-01-03
If its video drivers, displayconfig shows lots of available drivers
for the display.  System>Administration> hardware drivers does a scan to
report back available drivers

---

### Post by zolthar on 2009-01-03
Thank for the responses.

@linux_tech: how do I perform that in command line? I have the server version installed and have not installed any desktops.

The command "lsmod" just confused the hell out of me.

I think I used the wrong words, with Microsoft OSs, you can get device managers (control panel => system => device manager in Vista) that will show you if any devices or drivers are not installed correctly or the version installed (which is what I'm guessing lsmod is for).

I just want to know if the correct drivers were installed correctly - I'm just used to installing drivers after installing a MS OS such as INF/Chipset, sound, video, NICs, RAID controllers etc etc.

Im just not used to the fact of things just working smoothly!

---

