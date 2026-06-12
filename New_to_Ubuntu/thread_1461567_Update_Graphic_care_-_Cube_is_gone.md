---
title: "Update Graphic care - Cube is gone"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by George7a on 2010-04-24
Hi all,

I have updated my graphic card from GT7300 to ATI HD 4770. After installing the driver (it is working now) all the graphice options like the cube, drawing fire and others are not working!

Where should I start looking?

Thanks,

- George

---

### Post by George7a on 2010-04-24
any clues?

---

### Post by roger_1960 on 2010-04-24
Hi

Have you tried reinstalling compiz?

---

### Post by anewguy on 2010-04-24
I don't think it will solve the problem, but the terminal output may give us an idea of what is wrong, so please do the following:

- close any existing windows so you just have your desktop

- open a terminal window

- metacity --replace 

- compiz --replace

Hopefully the compiz --replace will show some output on the terminal -> copy this information and post it back here.

Dave ;)

---

### Post by George7a on 2010-04-24
I have tried this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

but i am getting the following errors:

> george@george-u:~/Desktop$ sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/karmic
Created directory fglrx-install.Ng7BEC
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/karmic
[B][COLOR="Red"]Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions[/COLOR][/B]
Removing temporary directory: fglrx-install.Ng7BEC

Help please

---

### Post by quadproc on 2010-04-24
> **George7a said:**
> Hi all,

I have updated my graphic card from GT7300 to ATI HD 4770. After installing the driver (it is working now) all the graphice options like the cube, drawing fire and others are not working!

Where should I start looking?

Based on the error messages from a later posting, your driver did not get installed.

You'll need to have a copy of the appropriate driver for your Ubuntu version.  I think that ATI is at 10.3 now for your card but you should check with their web site for the latest info.  I suggest storing the file in a working directory on your system, maybe ati_drive_10.3 or something like that.

The next thing to do is to completely remove the old driver.  You should do this using the same means by which it was installed: e.g., if you used Synaptic to install then use Synaptic to uninstall.

With the old driver gone, start the .run file from ATI:
sudo sh <the_ati_driver_file_name> --keep --install
It will ask some questions about the install.  When it has finished then you'll have your directory left behind so that you can examine their files and scripts.

Depending on how ATI is treating your xorg.conf file, you may have to modify the file's driver section to specify "fglrx" or maybe they did that for you.  I once found that ATI's scripts had put duplicate entries into my xorg.conf file and that confused X windows.  It is wise to check the file contents after the install has finished.

After restarting your X server you should be running with the new driver.

Edit: here is another thought.  The X windows servers changed drastically between Ubuntu 8.10 and 9.04.  The new X server cannot work with the old ATI drivers and I think that you attempted to install an old one.  You will probably have to get a new driver and use a late enough Ubuntu version.

Edit continues: Roughly 1 year ago, ATI relegated a lot of their products to "legacy" status and ATI no longer supports drivers for those.  If you need a different arrangement then you might be able to use the open source ATI driver which is progressing rapidly.

BTW, the Ubuntu "Hardware Drivers" utility does not correctly report the status of your driver.  It also does not allow you to choose which ATI driver gets installed.  I no longer try to use that utility.

Once your driver is working OK then you can go into the Compiz settings and enable the features that you want.  Also, to allow the cube to work you'll need to have at least 4 workspaces in the horizontal direction. You can set that by right clicking on any of the little workspace "icons" near the trash can, choose Preferences, then set columns to 4. Also, you will need to enable effects.  You can set that by right clicking on the desktop background, choosing Change Desktop Background, Visual Effects, and then choose the level that you prefer.

Good luck!

quadproc

---

