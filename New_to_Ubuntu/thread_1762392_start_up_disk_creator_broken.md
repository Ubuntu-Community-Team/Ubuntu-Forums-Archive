---
title: "start up disk creator broken"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Legeril on 2011-05-19
I'm trying to make a Live USB, but I can't seem to get the thing to work =/

I've made them before with no problems, but for some reason this isn't working.

I'm trying to install 10.04 on a 4GB USB, I've included a screen shot as reference.

Also for some reason the list of devices is showing two USBs

/dev/sdb and /dev/sdb1, though neither of them work..

Any insight greatly appreciated as I am making this for a friend who is having Windows problems and is interested in switching to Linux

---

### Post by lmarmisa on 2011-05-19
They are not two devices: /dev/sdb is related to the USB device; /dev/sdb1 is related to the partition defined in this /dev/sdb device.

Are you able to select /dev/sdb1 and erase it?.

I remember some problems about it in 10.04 that were solved in 10.10.

---

### Post by jtarin on 2011-05-19
Have you tried just unplugging the USB and plugging back in then start Disk Creator? Unplug then reboot....then try?

---

### Post by jre6 on 2011-05-19
Otherwise try Unetbootin.

---

### Post by bennachie on 2011-05-19
This is a perfectly normal display for Startup Disk Creator. You should select the partition (sdb1) for the installation, and everything should work properly. There was a problem at one stage in using SDC in 10.04 to make a 10.10 Startup Disk, which is no doubt what a previous contributor had in mind.

---

### Post by Legeril on 2011-05-19
> **jtarin said:**
> Have you tried just unplugging the USB and plugging back in then start Disk Creator? Unplug then reboot....then try?

I have tried this and still no joy, erased the USB and formatted it... The USB had data on it before that worked fine so I don't think the problem is with it, but I can't imagine my SDC has just suddenly stopped working either :confused:

---

### Post by Legeril on 2011-05-19
> **jre6 said:**
> Otherwise try Unetbootin.

Did this, worked perfectly

Thank you

---

