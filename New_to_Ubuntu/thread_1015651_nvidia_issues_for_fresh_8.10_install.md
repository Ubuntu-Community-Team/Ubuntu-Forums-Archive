---
title: "nvidia issues for fresh 8.10 install"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by dobbsjr on 2008-12-19
i just got a new MB with a brand new HD and a fresh install of Ubuntu(8.10 iso). the only card i have installed is the GeForce 9400 GT. i have 2G of memory, but can only seem to get about an hour of random surfing before Flash etc starts to act up and play about 2 secs worth, then freeze. FF never freezes, but when i try and restart FF i get an error msg saying it is already running.i have a feeling that this is a driver issue, but not sure how to start tackling it, any suggestions for a n00b?

---

### Post by Michael.Godawski on 2008-12-19
> **dobbsjr said:**
> i just got a new MB with a brand new HD and a fresh install of Ubuntu(8.10 iso). the only card i have installed is the GeForce 9400 GT. i have 2G of memory, but can only seem to get about an hour of random surfing before Flash etc starts to act up and play about 2 secs worth, then freeze. FF never freezes, but when i try and restart FF i get an error msg saying it is already running.i have a feeling that this is a driver issue, but not sure how to start tackling it, any suggestions for a n00b?

hey dobbsjr, 
let's check if your graphic card drivers are installed properly.
Open the terminal: Applications > Accessories > Terminal

and run this command:
```
sudo lshw -C display
```
you will have to type in your login/root password. It won't be displayed whatsoever. Just type it in blindly and hit enter.

Post the output. Copying from the terminal goes with Ctrl+Shift+C or just highlighting with the mouse and for copying use the middle mouse button.

This might be an issue with Copmiz. Are you running Ubuntu with effects?
System >Preferences > Appearance >Visual Effects

---

### Post by dobbsjr on 2008-12-19
> **Michael.Godawski said:**
> hey dobbsjr, 
let's check if your graphic card drivers are installed properly.
Open the terminal: Applications > Accessories > Terminal

and run this command:
```
sudo lshw -C display
```
you will have to type in your login/root password. It won't be displayed whatsoever. Just type it in blindly and hit enter.

Post the output. Copying from the terminal goes with Ctrl+Shift+C or just highlighting with the mouse and for copying use the middle mouse button.

This might be an issue with Copmiz. Are you running Ubuntu with effects?
System >Preferences > Appearance >Visual Effects
normal visual effects....


this is the terminal output

d@d-desktop:~$ sudo lshw -C display
[sudo] password for d: 
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
d@d-desktop:~$

---

