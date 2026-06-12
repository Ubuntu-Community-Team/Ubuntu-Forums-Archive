---
title: "Forced into Low-Graphics"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Tahakki on 2010-05-19
Every time I boot Ubuntu, I get an error message saying that it can't start the graphics kernel. This leaves me in low-graphics mode. I am on the Lucid Lynx 64-bit, and this happens with both 'version current' and 'version 96'. I have a GeForce 220GT.

Can somebody please help me out before I give up on Ubuntu entirely? This happens with *every* new release - some problem involving graphics. Please, please help me out before I'm forced to go back to Windows 7. At least I know it works.

---

### Post by apjone on 2010-05-19
Can you post the contents of your /etc/X11/xorg.conf

---

### Post by -humanaut- on 2010-05-19
Hit enter before the bootsplash and add nomodeset to your boot options then install the "current driver" unless your using an Ancient TNT or Vanta card you don't need the 96 Driver nomodeset should boot it into atleast 1024x768

---

### Post by nhasian on 2010-05-19
yes remove the version 96 drivers.  you should use the nvidia-current.  also make sure your system is up to date with:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Tahakki on 2010-05-19
I have removed all graphics drivers.

@nhasin: Using nvidia-current results in the error I described.

@-humanaut-: Before the bootsplash? Do you mean immediately after GRUB? And will this resolve my issue?

Thanks, guys. Any help is appreciated.

---

### Post by Tahakki on 2010-05-19
AAAAAAARRRRGGGHHH

It's happened again. *Help.*

---

### Post by nhasian on 2010-05-19
can you give us the output of the following terminal command:

```
lshw -C display
```

for example mine says:

>   *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 250]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f8000000-f8ffffff memory:e0000000-efffffff memory:f6000000-f7ffffff ioport:bf00(size=128) memory:f9000000-f901ffff


as you can see i'm running a similar graphics card and it worked right away on ubuntu 10.04 lucid lynx.  i didn't have to do anything special.  although the I got a high res desktop with the open source Nouveau driver, i did enable the restricted nvidia-current anyway in the Hardware Drivers because Boxee was sluggish with the Nouveau driver.

---

### Post by Tahakki on 2010-05-20
```
*-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 220]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fb000000-fbffffff memory:c0000000-cfffffff(prefetchable) memory:de000000-dfffffff(prefetchable) ioport:af00(size=128) memory:d0000000-d007ffff(prefetchable)

```

Looks fairly similar.

I'm wondering if this could be a kernel issue? On the latest kernel, nouveau runs at 1080p and looks very well, except there's no effects, but on the slightly older realtime kernel I get a really low resolution. And the error messages seem to say something to do with the 'kernel module'.

Same error as here, actually:
[http://ubuntuforums.org/showthread.php?t=213409](http://ubuntuforums.org/showthread.php?t=213409)

---

### Post by nhasian on 2010-05-20
yes that shows that your using the nouveau driver built into the kernel so newer kernel has better improvements for nvidia GPUs.  Unless you have a reason not to, i'd recommend switching to the nvidia-current driver instead.

> **Tahakki said:**
> ```

       configuration: driver=nouveau latency=0
```

I'm wondering if this could be a kernel issue? On the latest kernel, nouveau runs at 1080p and looks very well, except there's no effects, but on the slightly older realtime kernel I get a really low resolution. And the error messages seem to say something to do with the 'kernel module'.

---

### Post by Kafubie on 2010-05-20
I am running low graphics, and it's not bad at all..
More speed.

---

### Post by Tahakki on 2010-05-21
Switching to nvidia-current causes the above error.

---

### Post by diablo75 on 2010-05-21
I had this same problem last week with a GeForce 220 and thought I would have to install the latest drivers manually.  Turns out there were some kernel updates and what not still pending that needed to be installed.

First, disable your nVidia drivers in the Hardware Drivers Manager.  Then check Update Manager and apply everything that's out there.  Reboot, then use the Drivers Manager to re-enable the nVidia drivers for your card.  Cross your fingers.  Hope this works for ya!

---

### Post by cryptotheslow on 2010-05-21
This is interesting - I failed miserably to get a GTS250 to work on a test clean install of lucid in a scrap partition using anything other than Nouveau. That was right after lucid was released. I'll have to go and try it again now and check for those kernel updates before applying the NVidia driver.

---

### Post by Tahakki on 2010-05-21
I'm convinced this is a kernel issue - it doesn't work in the latest kernel but it does in the older linux-rt kernel.

---

### Post by cryptotheslow on 2010-05-21
OK I got my GTS250 to work in a new scrap install of lucid - (once I'd got all the updates) - installed it from the Hardware Drivers section, but had to use a backup copy of my xorg.conf file from my karmic install to get the screen resolution working right - but I had to hand craft it on karmic anyway as my monitor is old and unrecognised.

Soo... I took the plunge and upgraded my karmic install to lucid using the Update Manager. That went quite smoothly overall, but the NVidia Drivers were not available in the Hardware Drivers section.

I had to go to Synaptic and manually install:
nvidia-current
nvidia-current-dev
nvidia-kernel-common
nvidia-current-modaliases

Then on reboot X fell back to using Nouveau complaining that the configured screen resolution was unsupported. Running nvidia-xsettings from Terminal made no difference. So I just copied in my old xorg.conf file again and it is all working fine with driver vers. 195.36.15 - and the driver now shows up as Installed and Active in the Hardware Drivers.

Happy days :) Now to explore and see if everything works!

Oh and for reference - this is on kernel 2.6.32-22-generic


**edit to say:- **I spoke too soon. After a few reboots, Hardware Drivers says that the driver is "activated but not currently in use". However, lsmod shows that it is in use. GLX is also broken :(

---

### Post by pkbyron on 2010-05-21
> **diablo75 said:**
> I had this same problem last week with a GeForce 220 and thought I would have to install the latest drivers manually.  Turns out there were some kernel updates and what not still pending that needed to be installed.

First, disable your nVidia drivers in the Hardware Drivers Manager.  Then check Update Manager and apply everything that's out there.  Reboot, then use the Drivers Manager to re-enable the nVidia drivers for your card.  Cross your fingers.  Hope this works for ya!
I have exactly the same problem with the NVIDIA GeForce GT 220.  I upgraded the driver as I have a FAN going full speed and it was suggested it might be because of the graphics card.  So went to current driver and system regressed into a caveman like VGA.

Am doing the Update Manager, and updating all.  And will try the driver again afterwards.

UPDATE: this procedure didn't work for my issue.  The Update Manager was run, and after restart the machine started in good high definition but without the NVIDIA driver.  As soon as I reinstalled the driver (as suggested) and restart - it went back into low res mode...
and I still have a Fan that is going top speed! and has been for hours now...



regards,
pkbyron

---

### Post by Tahakki on 2010-05-21
@pkbyron: Are you in Lucid?

---

