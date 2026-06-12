---
title: "Nvidia display problems"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by InsidiousGrin on 2009-09-18
Hi, I'm fairly new to ubuntu and am having trouble with my display range, which is stuck in 800x600. My xorg file seems strange and I'm wondering if it can provide clues to my issue:
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by NoaHall on 2009-09-18
Try opening a terminal and doing "gksudo nvidia-settings" and changing the settings from there .

---

### Post by InsidiousGrin on 2009-09-18
> **NoaHall said:**
> Try opening a terminal and doing "gksudo nvidia-settings" and changing the settings from there .
Whenever I do that, Nvidia gives me this message: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Which does not work either.

---

### Post by NoaHall on 2009-09-18
Go to System -> Admin -> Hardware Drivers and make sure your driver is installed.

---

### Post by InsidiousGrin on 2009-09-18
> **NoaHall said:**
> Go to System -> Admin -> Hardware Drivers and make sure your driver is installed.
I don't even have a Hardware Drivers menu option. I haven't since I upgraded to 9.04.

---

### Post by lukeiamyourfather on 2009-09-18
> **NoaHall said:**
> Go to System -> Admin -> Hardware Drivers and make sure your driver is installed.

True that. But this only works if the driver was installed from the repositories. If it was installed from a binary driver (from nVidia download site) then you will want to remove that and install from the hardware drivers tool included with Ubuntu. Cheers!

---

### Post by NoaHall on 2009-09-18
Really? That's weird. Try right click on the menu -> Edit Menus -> System -> Admin -> and see if hardware drivers is there/ticked.

---

### Post by InsidiousGrin on 2009-09-18
> **NoaHall said:**
> Really? That's weird. Try right click on the menu -> Edit Menus -> System -> Admin -> and see if hardware drivers is there/ticked.
Well, a quick trip to synaptic showed me that I didn't have jockey installed, so that fixed that problem. However, when I run my Hardware Drivers command, it shows two Nvidia accelerated graphics drivers, but when I try to activate either, nothing happens.
> **lukeiamyourfather said:**
> . If it was installed from a binary driver (from nVidia download site) then you will want to remove that and install from the hardware drivers tool included with Ubuntu.
How would I go about checking and deleting this if it is the case?

---

### Post by NoaHall on 2009-09-18
Try restarting before attempting to activate. Note, you'll need to restart for the changes to take place. Make sure that your whole system is fully up to date.

---

### Post by InsidiousGrin on 2009-09-18
> **NoaHall said:**
> Try restarting before attempting to activate. Note, you'll need to restart for the changes to take place. Make sure that your whole system is fully up to date.
No, still nothing. Whenever I reset my computer, it tells me that my graphics are not recognized and I have to boot in low-res mode just to access my desktop. But first, it has to go through several display servers that never work. I am so confused!!!

---

### Post by NoaHall on 2009-09-18
Ah, I had that problem. I got rid of it by a complete reinstall. It seems like a error with the kernel to me.

---

### Post by JDShu on 2009-09-18
Agreed, I would purge the nvidia drivers and then install the latest driver from the nvidia site.

---

### Post by RedRat on 2009-09-18
Have you tried using EnvyNG to install the drivers?

---

