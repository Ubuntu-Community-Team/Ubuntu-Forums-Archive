---
title: "Trouble suspending after kernel update (to 2.6.32-25-generic)"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2010-10-03
Im running 10.04 on a Lenovo 3000 V100. Updated a couple of days ago to kernel 2.6.32-25-generic and after that I have been unable to suspend (screen shuts down, can hear HD spinning down but the screen returns immediately to the lock screen). When running "sudo pm-suspend" the HD spins down, wireless shuts down but the screen stays on and the computer returns to active immediately. Hibernate works fine. I have had issues in the past with suspend on this laptop and it has been due to the BisonCam (Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller). I've tried the solution on post #13 of:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998)

but I get a "bash: /sys/bus/usb/devices/usb1/power/wakeup: Permission denied" even when trying it under sudo

Anyone have any suggestions/fixes? 

Thanks in advance, I appreciate any help







UPDATE:
This fixed the issue:
```
sudo -i
echo disabled > /sys/bus/usb/devices/usb1/power/wakeup
```

Sorry for any clutter

---

