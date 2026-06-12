---
title: "tv as moniter"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by stoneofshadow on 2009-06-05
how do i connect the computer to the tv with an hdmi cable
my pc and tv both have hdmi ports

---

### Post by Hospadar on 2009-06-05
It depends a lot on the video card, what kind do you have?

If you arn't sure, you can "lspci | grep VGA" and/or "sudo lshw -C video"

If it's some kind of nvidia card and you're using the restricted drivers (the configuration line in the lshw command will have something like "driver=nvidia" and _not_ "driver=nv") you can "sudo nvidia-settings" and set it up graphically.

---

### Post by stoneofshadow on 2009-06-05
"sudo lshw -C video"
*-display               
       description: VGA compatible controller 
       product: G70 [GeForce 7600 GS] 
       vendor: nVidia Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vga_controller bus_master cap_list 
       configuration: driver=nvidia latency=0 module=nvidia 




and 


lspci | grep VGA:

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

---

### Post by stoneofshadow on 2009-06-05
sudo nvidia-settings 
command not found

---

### Post by stoneofshadow on 2009-06-05
how do i change the settings?

---

### Post by stoneofshadow on 2009-06-06
?

---

### Post by jimmy the saint on 2009-06-06
try typing nvidia then hitting the tab key to see what comes up.  You may have misspelled nvidia-settings or it may not be installed (which would be odd if you have the restricted driver installed).  

Go to system>adminstration>restricted driver manager to see if youre proprietary driver is enabled.  If it isn't, enable it and restart.  Then you should be able to proceed as directed.

---

### Post by stoneofshadow on 2009-06-07
the problem is my linux computer is not connected to the internet so i have to get any files i need to pysicly transfer between this windows computer and that computer

---

