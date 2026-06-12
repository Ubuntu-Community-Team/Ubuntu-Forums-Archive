---
title: "WoW - Wine - Nvidia and 3D Rendering"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Tylerdurden03 on 2009-01-05
Ok, any help would be greatly appreciated and I'm fairly new to Ubuntu so keep that in mind.

I've been trying desperately to get WoW installed and working on Ubuntu for a couple days now but to no avail.

Here is my current situation...

Whenver I open WoW with Wine it will open the launcher just fine but crashes immediately when trying to open the game itself. When I try to open it through the terminal it says;
"NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
"NVIDIA: Direct rendering failed; attempting indirect rendering."

Which leads be to believe that WoW is crashing because I do not have direct rendering enabled. Which if I do glxinfo | grep render it says "Direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Right now if I got ot Hardware drivers, it lists the Nvidia 177 version as the recommended driver (which is what I have installed)

When I use the nvidia-glx in terminal I get "bash: nvidia-glx: command not found"

Any suggestions would be awesome, I'm pulling my hair out right now trying to figure this out. Thanks.

---

### Post by RomeReactor on 2009-01-05
Hi. Did you install the driver from Synaptic? if so, did you also run:
```
sudo nvidia-xconfig
```
after installing the drivers?

Have you searched the [Wine section]("http://ubuntuforums.org/forumdisplay.php?f=313") to see if anyone else had this problem before?

---

### Post by flytripper on 2009-01-05
also the card id would be a good heads up for us. is it apg/pcix / onboard?

---

### Post by Tylerdurden03 on 2009-01-05
> **RomeReactor said:**
> Hi. Did you install the driver from Synaptic? if so, did you also run:
```
sudo nvidia-xconfig
```
after installing the drivers?

Have you searched the [Wine section]("http://ubuntuforums.org/forumdisplay.php?f=313") to see if anyone else had this problem before?

I searched high and low for a solution but nobody seems to have the same problems as me (at least not that I could find)

Also it's a Nvidia 9800 GTX video card.

---

### Post by RomeReactor on 2009-01-05
Try running:
```
sudo nvidia-xconfig
```
from a terminal; you'll probably be asked to reboot or logout afterwards. Then see if you have direct rendering.

EDIT: make sure the 177 driver is listed as activated in Hardware Drivers.

---

### Post by Tylerdurden03 on 2009-01-05
> **RomeReactor said:**
> Try running:
```
sudo nvidia-xconfig
```
from a terminal; you'll probably be asked to reboot or logout afterwards. Then see if you have direct rendering.

EDIT: make sure the 177 driver is listed as activated in Hardware Drivers.

When I do that it says 

>  Using X configuation file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.confg' as '/etc/X11/xorg.confg.backup'
New X configuaration file written to 'etc/X11/xorg.conf'

Also under Hardware Drivers it shows that the NVIDIA accelerated graphic driver (version 177) is installed and activated.

---

### Post by RomeReactor on 2009-01-05
Did you reboot after running nvidia-xconfig? Do you still get "Direct rendering: No" on glxinfo? Have you uninstalled any packages that would coincide with this problem? In case you're missing any packages, run:
```
sudo aptitude install ubuntu-desktop
```
Are you running Ubuntu 32 bit or 64?

---

### Post by Gosujii-sama on 2009-12-18
I seem to be getting this same error of the nvidiactl file be unable to be accessed. I've installed a new driver over did the sudo cmd got the same message he recived and installed the desktop again. However this issue seems to still be there. List of my stats are:

Graphic Proccessor: GeForce 6150SE nForce 430
VBIOS ver: 05.61.32.25.02
Memory: 256 
Bus type: Intigrated
Bus ID: 0:13:0
PCI Device ID: 0x03d0
PCI Vendor ID: 0x10de
IRQ: 23
XScreens: Screen 0

Using nVidia driver version: 190.53

---

