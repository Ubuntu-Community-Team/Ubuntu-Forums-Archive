---
title: "Ubuntu 8.10: NVidia 6600GT &amp; Compiz Solution [SOLVED]"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2009-01-09
These solutions involve downloading the seperate .deb files from the websites listed below, then double clicking the .deb files (once downloaded) to install.

**Nvidia 173 Driver**

Website: [http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source]("http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source")

*FILES REQUIRED BY UBUNTU 8.10:*

[COLOR="Orange"]dkms_2.0.20.4-0ubuntu2_all.deb
nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb
nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb[/COLOR]
[B]
Nvidia 177 Driver (Recommended for use with Ubuntu 8.10 instead of the 173 Driver)[/B]

Website:[http://packages.ubuntu.com/intrepid/nvidia-177-kernel-source]("http://packages.ubuntu.com/intrepid/nvidia-177-kernel-source")

*FILES REQUIRED BY UBUNTU 8.10:*

[COLOR="Orange"]dkms_2.0.20.4-0ubuntu2_all.deb
nvidia-177-kernel-source_177.80-0ubuntu2_i386.deb
nvidia-glx-177_177.80-0ubuntu2_i386.deb[/COLOR]

To install these .deb file double click on the icon and click install in the package manager that appears either install the 3 Nvidia 173 (or Nvidia 177) driver files mentioned above, then go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 173 (or VERSION 177 if installed this instead) click enable, an arrow should appear asking you to restart your system.

After restarting your system the driver will enable, select your desktop effects from appearances
and your up and running

**Nvidia Settings (For Both 173 & 177 Drivers)**

Website:[http://packages.ubuntu.com/intrepid/nvidia-settings]("http://packages.ubuntu.com/intrepid/nvidia-settings")

Adds System/Administration/NVIDIA X Server Settings (GUI to Ubuntu's Menu Bar)

*FILES REQUIRED BY UBUNTU 8.10:*

[COLOR="Orange"]nvidia-settings_177.78-0ubuntu2_i386.deb[/COLOR]

**Compizconfig-settings-manager**

Website:[http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager]("http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager")

Adds System/Preferences/CompizConfig Settings Manager (GUI to Ubuntu's Menu bar)

*FILES REQUIRED BY UBUNTU 8.10:*

[COLOR="Orange"]compizconfig-settings-manager_0.7.8-0ubuntu3_all.deb
python-compizconfig_0.7.8-0ubuntu1_i386.deb[/COLOR]

After installing these 2 files go to System/Preferences/CompizConfig Settings Manager and click "General Options", "Desktop Size" Tab, set Horizontal Virtual Size to 4.

If required click "back" and turn off "Cube Reflection & Deformation" under the effects menu, If you prefer the the 3D Cube effect, switch this on if you prefer the 3D Sphere effect.

To enable 3D Cube Reflection effects

If you want 3D cube reflection Effects (requires Compiz Config Setings Manager Installed)

Under SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS>

**EFFECTS**

Click "Cube refelection & deformation" box so tick appears, Then double click on the description part ("Cube refection and deformation" text) on the deformation tag set deformation to "none".

Your 3D cube should now have reflection effects

**PS:** You download from the bottom header on each page in either amd64 (For 64bit users), i386 (For 32bit users) or all (if no other options present). Click other files names to download other dependancy files and then do same as above.

---

