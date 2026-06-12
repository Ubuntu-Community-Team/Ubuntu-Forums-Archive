---
title: "Acer x183H Resolution"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by kydavis77 on 2010-06-22
Very happy with the new distro of Ubuntu. Upgraded yesterday from 9.10 to 10.4. In the older distro my monitor displayed the proper resolution with no issues. After upgrading, my monitor is stuck in the "auto" resolution.

I have the Nvidia graphics driver installed and use that control panel to change settings. So here is what happens. I got to System>Admin>Nvidia x server settings. Select the X server display config, highlight the acer monitor, (named crt-0) change the resolution to 1360x768 and click apply. When I do that the monitor goes into this "auto config" mode and just does that over and over and over. I have to set it back to auto to make it stop.

The "auto" resolution looks like garbage on the widescreen and I want to use the 1360x768 res. Any help on how to get the monitor to properly display that res without the auto config repeat happening. 

THanks

---

### Post by cariboo on 2010-06-23
Try opening a terminal and typing:

```
sudo nvidia-xconfig
```

the above command will create a new /etc/X11/xorg.conf, once the command has finished, reboot, and you should be able to set the resolution to what you want. You may have to run nvidia-settings as rot to make the new settings stick, press Alt-F2 and type:

```
gksu nvidia-settings
```

---

### Post by A Zenful Person on 2010-07-07
hello, please check out my post here if your still having trouble.

i spent almost 3 days workign through all the right steps to figure it out, hope it helps :). 

--->[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9510678](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9510678)

---

