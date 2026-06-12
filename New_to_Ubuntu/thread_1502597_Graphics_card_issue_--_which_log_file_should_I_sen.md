---
title: "Graphics card issue -- which log file should I send to the manufacturer?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by MathMcC on 2010-06-05
I've had problems with my Evga Nvida GTX 260 in the past. Its not a compatibility issue with Ubuntu because Windows is blue-screening.

Which log should I send to the manufacturer in the hope it will shed some light on the problem?

This was in an Xorg.failsafe.log file, but I don't know whether it relates to me logging into Ubuntu with full graphics enabled (I don't have a problem in failsafe mode):

```
(--) PCI:*(0:1:0:0) 10de:05e2:3842:1257 nVidia Corporation GT200 [GeForce GTX 260] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/524288
```

That unidentified memory address seems wrong...

---

### Post by MathMcC on 2010-06-06
```
sudo rm -f /etc/X11/xorg.conf
```I rather stupidly ran this code (I'd seen it on another forum post and rather stupidly thought it was a reply to my thread): what has it done exactly?

Now when logging in normally to ubuntu it goes straight into failsafe mode...

---

### Post by warfacegod on 2010-06-06
That erased your xorg settings file. Go to the location in the code and create a new one called "xorg.conf", no quotes. You'll need to be root to do it. Hit Alt+F2 and enter gksudo nautilus.

---

### Post by MathMcC on 2010-06-06
> **warfacegod said:**
> That erased your xorg settings file. Go to the location in the code and create a new one called "xorg.conf", no quotes. You'll need to be root to do it. Hit Alt+F2 and enter gksudo nautilus.

I created the xorg file and ```
gksudo nautilus
``` seemed to create a .nautilus folder. Not sure what comes next though.
```

sudo dpkg-reconfigure xserver-xorg
```

I've been recommended this method now... gonna reboot.

---

### Post by realzippy on 2010-06-06
sudo dpkg-reconfigure xserver-xorg

should only run on older versions...btw,which version are you running?
9.10/10.04 should start X even without xorg.conf (which you deleted);
if you have formerly installed the nvidia-driver,run  

```
sudo nvidia-xconfig
```

which creates a new xorg file.

According to your first post,I do not see which ubuntu logfile should be able to help you with window bluescreen issues  (probably a windows-nvidiadriver problem)

---

### Post by warfacegod on 2010-06-06
Since 9.10, the xorg files have been shipping blank but I *think* they still actually need to be there for proper booting.

---

