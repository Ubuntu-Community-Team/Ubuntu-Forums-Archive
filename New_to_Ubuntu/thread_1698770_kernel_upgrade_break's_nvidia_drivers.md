---
title: "kernel upgrade break's nvidia drivers"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by jim Kane on 2011-03-02
every time i get a Kernel update, after restarting the PC im dumped to a screen that says unable to load nvidia drivers,
 i chose start in safe mode and reinstall nvidia drivers and restart again but this completely buggers up my desktop settings.
Is there an easy Noobs way of preventing this.

thank
Jim

---

### Post by NCLI on 2011-03-02
Yes, I assume that you've installed the drivers manually from nVidia's website.

Solution: Don't do that. Install them through System->Administration->Additional Drivers instead.

---

### Post by davidmohammed on 2011-03-02
this usually happens when you've manually installed the nvidia drivers - you should really use the suggested driver in Administration  - Hardware drivers.

Suggest remove your manual nvidia driver install and your xorg.conf file.  Reboot, and then reinstall the suggested nvidia driver from Administration - Hardware drivers.

```
sudo apt-get remove nvidia*

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

N.B. if you've blacklisted any the standard nouveau kernel model you'll need to remove the nouveau from the blacklist

---

### Post by jim Kane on 2011-03-02
> **NCLI said:**
> Yes, I assume that you've installed the drivers manually from nVidia's website.

Solution: Don't do that. Install them through System->Administration->Additional Drivers instead.

No they were installed from System>Hardware drivers  
(its xubuntu)

Jim

---

### Post by NCLI on 2011-03-02
Dang. That definitely shouldn't happen. Could you post the output of this command?
```
aptitude search nvidia*
```

---

### Post by JKyleOKC on 2011-03-02
The nVidia drivers require installation of kernel modules, which happens automatically during boot so that you don't see it. These modules must match the kernel version exactly. The kernel upgrades for at least the past four versions have not included the files necessary to create matching modules, which leads to the problem you are facing.

To cure it, get to the grub menu at boot by pressing the left shift key, and scroll down to the previous kernel version so that you get the GUI back. Then open Synaptic, locate "linux-headers-generic" and click it to be installed. Next locate "dkms" (dynamic kernel module support) and click it to be installed also. Finally click "apply" and follow the instructions.

This should automatically create the necessary modules so that when you reboot after the installation finishes, everything will work properly. You may have to install "linux-headers-generic" after each kernel update in the future, but it may update automatically. I only installed it here this morning; for the previous kernel upgrades I only installed the matching header packages and thus did not get new ones updated automagically...

In addition to the video drivers, this same problem applies to installations of VirtualBox, and the same cure applies there.

Hope this helps! It should really be made a "sticky" since it comes up so frequently...

---

### Post by jim Kane on 2011-03-03
> **JKyleOKC said:**
> 
Hope this helps! It should really be made a "sticky" since it comes up so frequently...


Thanks Jim i will print that and stick it on my wall :D
and to everyone else for the help, i would not be able to manage without the help from this forum.

Jim K

---

