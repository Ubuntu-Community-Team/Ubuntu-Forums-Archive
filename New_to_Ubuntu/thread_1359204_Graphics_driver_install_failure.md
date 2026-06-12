---
title: "Graphics driver install failure ?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-19
Hi,

I have installed Ubuntu  9.10, but no longer have my prefered crt display spec of 1600 x 1200 @ 75/85 Hz. Instead i have the basic 800 X 600 @ 60 Hz. 

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

Then i get 4 options:

"Run in low graphics mode

Reconfig graphics

Troubleshoot error

exit console"


Troubleshoot error leads to four more options

"Review Xserver log file

Review startup errors

Edit config files

Archive config and log" 

What should i do next?

---

