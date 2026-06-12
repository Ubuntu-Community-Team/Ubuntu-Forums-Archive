---
title: "Low Graphics mode after hareware install"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by stalkier on 2010-05-07
I recently installed a Hauppauge WinTV-HVR-1600 card in my HTPC. I am running 10.04 with MythTV. After installation and system restart Ubuntu went to low graphics mode. How do I get it to go back to NVidea driver.

---

### Post by jbrown96 on 2010-05-07
Switch to a virtual terminal (Ctrl+Alt+F2), login, and run ```
sudo nvidia-xconfig
``` After that reboot ```
sudo reboot
```

If that still doesn't work, then go back to the virtual terminal and reinstall the driver. ```
sudo apt-get purge nvidia-current && sudo apt-get install nvidia-current
``` then reboot

---

