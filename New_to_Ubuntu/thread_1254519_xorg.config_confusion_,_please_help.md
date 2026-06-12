---
title: "xorg.config confusion , please help"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Silvain on 2009-08-31
This PC has Ubuntu 9.04. Have been trying to add the Nvidia drivers to obtain the 3D acceleration. The display adapter has a Riva TNT chip. Have been attempting to setup with the driver file, NVIDIA-Linux-x8671.86.11-pkg1.run .

While running this seems OK. But the problem, seems most likely to be, that the auto-config option for the xorg.config never shows up. It appears to compile a NVIDIA kernal and install numerous files. However when I looked at the file last time,the xorg.config file appears to be empty.

Every how-to guide I have looked at so far, implies the that some kind of auto configuration of the xorg.config file occurs. What am I doing wrong? Also another note; I have not found any Nvidia drivers installation how-to thread, that is written just for the Jaunty Jackalope edition. If there is one. will someone please alert me to it? Thanks in advance.

:)

---

### Post by TeoBigusGeekus on 2009-08-31
Have you tried to go to System->Administration->Hardware Drivers and install restricted drivers from there?
In jaunty, the xorg.conf file has little significance.

---

### Post by hyperdude111 on 2009-08-31
Dont bother with the nvidia.run package unless the driver shipped with ubuntu has problems. 

System-admin-Hardware drivers

Then enable the newest one (takes about 1-10 mins depending on Internet speed.

---

### Post by Silvain on 2009-08-31
OK will do the uninstall routine for the nvidia.run package and then try these suggestions. Thanks!

---

### Post by Silvain on 2009-08-31
Checked System->Administration->Hardware Drivers...

Window says no proprietary drivers are in use on this system.

Does Jaunty now support open GL acceleration ,taking advantage of the display adapter chips' processing power, for games such as Oolite now?

---

### Post by Silvain on 2009-08-31
Founds this thread: Post # 5 looks worth a try !
[http://ubuntuforums.org/showthread.php?t=1253384&highlight=nvidia-glx-71]("http://ubuntuforums.org/showthread.php?t=1253384&highlight=nvidia-glx-71")



> I think you may be in luck. Apparently the Nvidia version 71 driver fully supports the RIVA TNT2 card and is still available in the repositories.

Start the Synaptic Package manager and do a search for 'nvidia-71'. Select the following 3 packages for installation:

nvidia-glx-71
nvidia-71-modaliases
nvidia-71-kernel-source

Hopefully all you'll have to do now is reboot. If the driver is still not functional, go back to Hardware Drivers to see if it is listed and make sure it's selected and activated.

tgeer


More info on package at :
[http://packages.ubuntu.com/ko/jaunty/nvidia-glx-71]("http://packages.ubuntu.com/ko/jaunty/nvidia-glx-71")

It says my card is supported !

Trying the quote action now ...
__________________

---

### Post by unutbu on 2009-08-31
Silvain, I think you are taking the right path by trying the Ubuntu packages from the official repository first.

However, since you asked for a how-to guide, if for some reason you end up wanting to try the the latest Nvidia drivers, here is a very nice howto: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

Edit: Oops... I'm not sure that guide is meant for the Riva TNT ...

---

