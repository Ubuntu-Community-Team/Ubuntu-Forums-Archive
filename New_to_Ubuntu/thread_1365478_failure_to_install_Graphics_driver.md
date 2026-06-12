---
title: "failure to install Graphics driver ?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-27
Hi,

I have installed Ubuntu 9.10, but no longer have my prefered crt display spec of 1600 x 1200 @ 75/85 Hz. Instead i have the basic 800 X 600 @ 60 Hz.

When i search using 'Hardware Drivers', Ubuntu recommends i activate Nvidia version 173.

I activate dl and install this, and when attempting to use the "display" app to select my spec, i got the message:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vender's tool instead?"

'Yes' produces a further notice:

"You do not appear to be using the nvidia X driver. Please edit your X config file (just run 'nvidia-xconfif' as root), and restart the X server."

So I:

sudo nvidia-xconfig

and reboot.

At reboot i get:

"Ubuntu is running in low graphics mode

The following error was encountered. You may need to update your config to solve this.

(EE) NVIDIA (0) FAILED TO LOAD NVIDIEA MODULE
(EE) ***ABORTING***
(EE) SCREENS FOUND, BUT NONE HAVE USEUABLE CONFIGS"

(Should i uninstall and re-install at this point?)


I then i get 4 options:

"Run in low graphics mode

Reconfig graphics

Troubleshoot error

exit console"


Troubleshoot error leads to four more options

"Review Xserver log file

Review startup errors

Edit config files

Archive config and log"


Edit config files yealds options:

"Use default (generic) config" -Which is low graphics mode.

"Use backup config"

"Create new config for this hardware" - This responds with;

"A new config has been generated and your old one backed up. Please reboot"

But this lands me back at the scrn;

"Ubuntu is running in low graphics mode

The following error was encountered. You may need to update your config to solve this.

(EE) NVIDIA (0) FAILED TO LOAD NVIDIEA MODULE
(EE) ***ABORTING***
(EE) SCREENS FOUND, BUT NONE HAVE USEUABLE CONFIGS"


What should i do next?

---

### Post by Methuselah on 2009-12-27
```

gedit /etc/X11/xorg.conf

```

Proceed in low graphics mode and try to get to your desktop then execute the above command.
Can you post the contents of that file when it comes up in your editor?
I'm guessing xorg.conf is messed up and this is the file that controls your display.

---

### Post by nnjond on 2009-12-27
Thanks for your interest.


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

---

