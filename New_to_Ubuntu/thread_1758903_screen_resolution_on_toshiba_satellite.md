---
title: "screen resolution on toshiba satellite"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by enetic on 2011-05-15
Im having some problems configuring the screen resolution on my laptop. Personally I want the screen resolution to be higher, but its not possible to change in system - preferences - monitors.. is there a way to do it in terminal?

---

### Post by im_NOT_a_PC on 2011-05-15
n00b here this might help if you have a nVaidia onboad card
Try typing
 	Code:
 	sudo /usr/bin/nvidia-settings 
into a console (also under System>Administration>NVIDIA X  Server Settings) and setting it there. Under "X Server Display  Configuration" change your resolution to what you want, then hit "Save  to X Configuration File".

It'll may fail. If so type:
 	Code:
 	sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old 
to back up just in case. Then try:
 	Code:
 	sudo /usr/bin/nvidia-settings 
and retry the nvidia-settings above.

If you need the old config back type:
 	Code:
 	sudo mv /etc/X11/xorg.conf_old /etc/X11/xorg.conf

---

### Post by enetic on 2011-05-15
thank you, but I forgot to mention that the laptop has a intel graphics card. I have heard that I dont need any drivers installed because intel is supported by default in ubuntu. hmm...

---

