---
title: "Nvidia graphics problems with ubuntu 10.10"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Heavenborncaptain on 2011-02-15
Recently I installed ubuntu 10.10 on a virtual machine in vmware since I didn't want to mess with my HDD, I have been trying to install the nvidia graphics drivers, when I do so nothing I am doing seems to work, i run "sudo nvidia-xconfig", when i do it creates the configuration file, however when i reboot, X does not start and I receive the error "Could not load the nvidia kernel module". 
When i check to see what graphics card I have, I get "00:0f.0 VGA compatible controller: VMware SVGA II Adapter"
I have a Nvidia 470 graphics card, I wish to install the drivers to use themes and the sort with emerald, so any help would be greatly appreciated!

---

### Post by sikander3786 on 2011-02-15
You are running Ubuntu inside VMWare therefore you can't install Nvidia drivers. It just uses a virtual graphics card.

VMware tools can provide some 3d acceleration I think but not sure if you'd be able to use compiz effects with that.

[http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

---

### Post by linuxsyst on 2011-02-15
Here's a [HOWTO]("http://ubuntuforums.org/showthread.php?t=1687189")

---

