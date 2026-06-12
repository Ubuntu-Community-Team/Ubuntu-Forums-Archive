---
title: "video broken"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by headdog on 2009-01-20
i really did it now i somehow lost my video driver i cant get any better than 800 x 600 resolution I have a old ati radion mobility m6 it worked until  i tried to upgrade the driver          please help im a newbeeeee

---

### Post by minsf on 2009-01-20
i am not an ATI expert, but we need more info. in the terminal/konsole enter the following command
```
sudo lshw -C display
```
and post the output here

---

### Post by minsf on 2009-01-20
if you cannot open a terminal/konsole window, try to use alt+ctrl+F1 to get to the command line interface. when done enter "exit" to get back to the graphical interface

---

### Post by headdog on 2009-01-20
this is what my computer said  

*-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8

---

### Post by minsf on 2009-01-20
ok it does seem that you lost the driver. before we install the new one, let's be sure you dont have the propriety ati driver installed somewhere in your system. please enter (in a command line interface, such as terminal/console or via alt+ctrl+f1)
```
sudo dpkg -l | grep fglrx
```
and post here the output.
also pust here the output of 
```
sudo lspci -ns 0000:01:00.0
```
the latter should give us more info about the graphic card you have, that sits at 0000:01:00.0 according to the output you posted above.

---

