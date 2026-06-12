---
title: "nvidia Drivers Installation Help"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by 2soos2 on 2011-06-23
I know that Ubuntu can automatically download and install drivers, but I downloaded the driver file from the nvidia site at my university to save usage at home. I tried the running the file, and I get the following error:  
"Could not open the file /media/The BIGDADDY/LINU&#8230;inux-x86_64-275.09.07.run

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again."

I tried selecting one of the encodings displayed in the menu, but I get the same error?
How do I install the update without having to download it again?
Thanks :)
Oh and I forgot, the nvidia driver I'm trying to install is:  NVIDIA-Linux-x86_64-275.09.07.run

---

### Post by BicyclerBoy on 2011-06-23
One defining difference between Ubuntu linux & windows is package management.

Do not do anything with that file until you read & understand..

That file you have downloaded is an executable script.
You can run it by setting the execute bit or
sh ./script_name
The nvidia installer also needs sudo privileges & the X server stopped/not loaded.
I'm not going to explain how-to use this nvidia driver.

This install method is outside the Ubuntu package management, there are dependencies required that you do not have.
This is not like a self contained windows program, it must be built against your kernel.
This install will break with every kernel update.

I strong suggest you obtain the nvidia driver thru' the Ubuntu package management.
If you need the latest driver version you will need to add a ppa to your package manager.

The xorg-edgers ppa has 275 for natty
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=natty)
so does ubuntu-x-swat ppa
[http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

---

### Post by grahammechanical on 2011-06-23
If it has deb as the file extension and you right click on it you should get the option to Open with Ubuntu Software Centre. That will install the program or in this case, the driver.

Regards.

---

### Post by BicyclerBoy on 2011-06-23
The nvidia driver (from nvidia) is not a deb package.
It is a script that builds open source component against the kernel headers for 64 & 32 bit, installs the close source components etc..
It can not be installed without stopping gdm.

Downloading debs from untrusted sources is not really any more secure than using windows & running anything from the web.

---

### Post by wolfen69 on 2011-06-23
Go to **Additional Drivers** section in ubuntu and download the recommended nvidia driver.

---

