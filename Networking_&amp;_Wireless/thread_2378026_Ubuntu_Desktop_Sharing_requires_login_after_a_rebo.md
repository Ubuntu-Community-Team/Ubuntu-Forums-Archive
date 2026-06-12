---
title: "Ubuntu Desktop Sharing requires login after a reboot for Mac OS Screen Sharing"
date: 2017-11-19
forum: Networking &amp; Wireless
---

### Post by freeflyjohn on 2017-11-19
I have managed to get desktop sharing working on Ubuntu (running on a headless server) so that I am able to view and control Ubuntu Desktop using the Screen Sharing tool on the Mac OS.

This works great BUT it doesn't work after the server has been rebooted.

After a reboot I have to login to Ubuntu Desktop in order to view the desktop using my Mac.

But to login to Ubuntu desktop I have to connect a monitor, keyboard and mouse which defies the point of running the server headless !

Is there a way around this ?

---

### Post by freeflyjohn on 2017-11-19
Managed to get it working by allowing auto login in the User account setting in Ubuntu Desktop

---

### Post by gofman-mike on 2017-12-04
Enabling Auto Login is not working for me. Do you have the proprietory Nvidia drivers installed? Seems like that forces the manual login requirement for a lot of people. Unfortunately I need CUDA to be enabled in the environment and that requires the drivers.

---

