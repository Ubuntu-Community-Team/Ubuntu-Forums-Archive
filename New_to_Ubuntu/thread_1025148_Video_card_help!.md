---
title: "Video card help!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by hakum on 2008-12-29
i just got ubuntu today and i was doing all the updates. i updated my nvidia video card driver and then rebooted. when i reboot there is a message saying that it could not enable my card and it had to use default video settings. when i got on the desktop i went to system> administration>nvidia x server settings. when i went there, there was a pop up saying "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I have no clue what to do. Any help would be greatly appreciated.
Thank you

---

### Post by Hospadar on 2008-12-29
It sounds like your video driver isn't installed right. Take a look in System->Administration->hardware driversand make sure the nvidia driver is enabled. Also maybe post your /etc/X11/xorg.conf file and the output of "lsmod" run in a terminal

---

### Post by hakum on 2008-12-30
It says that it is using a different version of the latest driver. Also how do i find this /etc/X11/xorg.conf? Heres what i got when i ran "lsmod" run  in a terminal-Usage: lsmod 

 Im sorry aboout all the questions im a complete nub to ubuntu.

---

