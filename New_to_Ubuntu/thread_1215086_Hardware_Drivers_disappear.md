---
title: "Hardware Drivers disappear?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by chouse626 on 2009-07-16
Does anyone know what the issue is with Hardware Drivers that are listed disappearing?  Everytime I update Ubuntu software it deletes out all the proprietary drivers and my desktop effects no longer work.  I'm trying to figure out why it does this and if I have to reinstall and not update or if I can fix it without reinstalling.

What I'm referring to is in Jaunty Jackalope if you go to System--Administration--Hardware Drivers it will normally show your video driver or at least on my HP machines it will show it.  Now it's gone.  

I've tried going into add/remove hardware as well as synaptic package manager to add the nvidia drivers and so far nothing has brought the driver back or allowed desktop effects.

Please help!

---

### Post by nhasian on 2009-07-16
chouse626,

first of all you may want to change your sig so it doesnt display your phone number and email address.  unless your a fan of spam :)
can you give us the output of the following terminal commands:

```
lsb_release -a
```

```
uname -a
```

```
lshw -C display
```

---

### Post by chouse626 on 2009-07-17
Alrighty.  Yeah I know about the phone number and email haha.  It's amazing how many calls and text messages I get from people just randomly saying hello.  Below is the info from the commands you had me run.


Code:
 	lsb_release -a 
  	
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty




Code:
 	uname -a 
  	Linux chris-hp 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

Code:
 	lshw -C display


      *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by chouse626 on 2009-07-17
I decided to run the lshw -C display command on the laptop pc I have that works and here is what I got.  The other command info produced the same results as the desktop pc minus the fact it showed the date on the uname- a as Fri Apr 17...I'm assuming that is when it was last updated.

*-display               
       description: VGA compatible controller
       product: C51 [Geforce 6150 Go]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia


I'm assuming the ATI is the issue on the desktop?  And if so how do I go about correcting that?

Like I said I just posted this in case it proves that updating is somehow changing the video driver and screwing up the pc.

---

### Post by nhasian on 2009-07-17
you said you were trying to install the nvidia drivers on your computer that has an ATI Radeon X300?  I dont think that will work...
I had an idea, try going to System->Administration->Software Sources, then click on the Updates Tab, and make sure that "Unsupported updates (jaunty-backports)" is ticked.  then if there are newer drivers for your video card, they should appear in the System->Administration->Hardware Drivers

> I've tried going into add/remove hardware as well as synaptic package manager to add the nvidia drivers

> **chouse626 said:**
> 
      *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc


---

### Post by chouse626 on 2009-07-17
I went ahead and check marked the jaunty backport box and still nothing.

The thing is my card isn't an ATI Radeon it's an nVidia.  I will log back into windows and find out exactly what card it is.  Like I said before the proprietary drivers area had multiple drivers but once I updated the computer they all disappeared.  I've had this issue on a total of 4 pc's now so there must be something changing somehow.

---

### Post by 3rdalbum on 2009-07-17
It depends how you installed the Nvidia driver.

All Linux kernel drivers need to be built for the kernel they will run with. When you update the kernel, the drivers will not work until they are recompiled for the new kernel.

If you install the graphics card drivers from the Hardware Drivers program, or by using Synaptic Package Manager to install "nvidia-glx-180", the recompiling process will happen automatically.

If you installed the Nvidia driver by downloading the installer at [www.nvidia.com](www.nvidia.com) and running it, then the recompiling will NOT happen automatically, and you will need to run the installer every time you apply a kernel update.

---

