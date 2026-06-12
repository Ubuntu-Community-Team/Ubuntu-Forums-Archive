---
title: "HDMI and NVIDIA Drivers"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by flavio_ on 2011-05-08
Hi, I installed Ubuntu 11.04 in a dual boot with windows. Every thing's working fine; excepted that my HDMI port does not work and I've been having trouble to install NVIDIA proprietary driver, which the system recommend me. Every time I installed the new driver, my Ubuntu restart with the classic interface - not Natty; and I receive the following message: "You do not appear to be using the NVIDIA X driver.  Please edit your X  configuration file (just run `nvidia-xconfig` as root), and restart the X  server." So, I must uninstall the driver to go back to the new interface. 

What should I do? Is the HDMI problem related to the NVIDIA issue? 

Ubuntu 11.04/ dual boot win 7 
2.66GHz Intel Core i5-480M 							
Type: Hybrid Graphics System
Installed: nVIDIA GeForce 310M with 1GB DDR3 SDRAM Dedicated; Intel GMA HD

---

### Post by wolfen69 on 2011-05-08
You should have run
```
sudo nvidia-xconfig
```
after installing the driver.

---

### Post by flavio_ on 2011-05-08
Thanks, Wolfen69.. but the problem persists. After installing, I had to enter ubuntu through the recovery mode. Tried the command,and that's the result : 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

And when I try to access the Nvidia x server settings, this message again: 

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

