---
title: "Nvidia 185 problem"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Sherfin on 2009-07-17
Hi , I've just started using Ubuntu 9.04 and not experianced with deep linux commands otherthan school linux.but ,with very difficulties i managed to install my nvidia graphics driver and i cant enable the desktop effects.my card is Geforce 6200 Turbocache (supports version 185).please help me out....

I installed Nvidia 185 driver successfully.
(All options are showing in the Nvidia X-Configuration window.)
But i cant enable the Visual Effects.Its telling "Desktop effects could not be enabled".

When i typed Nvidia-smi ,the result was..

"Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 185.18.14.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
Failed to allocate an RM client
Could not allocate resources!"

From that i understood i've installed the 185 driver and my kernel module has version 180. i checked the Hardware Drivers option , and it says that i have enabled the Nvidia driver version 180. 

BUT VERSION 185 IS NOT THERE.WHAT CAN I DO TO BRING THE OPTION TO ENABLE VERSION 185 ON THAT HARDWARE DRIVERS WINDOW ? What Package should i install ?

Pls tell me a way either to install version 185 or any older versions ,but it just have to work.please.

---

### Post by desperado665 on 2009-07-17
Sounds like you may not have removed the old driver before installing the 185 version. 185 works great in Jaunty (I am using it now on a 9500GT). I followed this:

1) First step: you must reset the Xorg to its default conf. Before, you should backup it, to avoid any mistakes.

In the Terminal:

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
$ sudo dpkg-reconfigure -phigh xserver-xorg


2) Installing packages and dependencies:

uname -r to get your kernel and ammend next line as required

$ sudo apt-get install build-essential linux-headers-`uname -r`


3) Remove old version drivers if installed otherwise skip to 4

$ sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')

Download the driver from nvidia website. Use the correct architecture ie 32 bit or 64 bit.


4) goto [www.nvidia.com](www.nvidia.com) and download the appropriate driver for your hardware.


5) Move driver to /usr/src/ folder

$ sudo mv drivername.run /usr/src/

Stopping the xserver and installing you may want to write the following down as you wont be able to refer back once we logout!!


6) So, press "Ctrl+Alt+F1", login and stop gdm:

$ sudo /etc/init.d/gdm stop for gnome

or

$ sudo /etc/init.d/kdm stop for kde


7) Install the driver

$ sudo sh /usr/src/drivername.run

Cool When it is done, restart your computer:

$ sudo reboot

After boot up, go to terminal and:

$ sudo nvidia-xconfig

$ sudo nvidia-setting

this last one allows you to specify settings and save to the xorg.conf if you wish.



The installer will ask if you want to recompile your kernel to which you need to respond yes.
Hope this helps

---

### Post by ptn107 on 2009-07-17
People who want the 185 driver should try the stable upstream PPA[1] and not the driver from nVidia's website (unless you like recompiling your drivers manually after every kernel upgrade).

```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
```

Don't forget to import the signing key for verification.

[1] [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

---

### Post by Sherfin on 2009-07-17
But my problem hasn't been solved yet.And ptn107 , beginers like me can't understand what you are saying.

Desperado , you made things more worse ,  on the last step ($ sudo nvidia-setting) , the reply is 

ERROR: The control display is undefined; please run `nvidia-settings --help`
for usage information.

I checked the Hardware drivers option ,its dead blank..

pls help me out..

---

### Post by cariboo on 2009-07-17
I would suggest you remove all Nvidia drivers, go to System-->Administration-->Synaptic Package Manager and search for nvidia, mark all mention of nvidia for complete removal, Then remove /etc/X11/xorg.conf, to do this press Alt-F2 and type:

```
gksu nautilus
```

This will open the file manager in root mode, next navigate to /etc, click File System in the left hand pane, then click /etc then /X11 and delete xorg.conf.

Once you have done the above reboot your system, once at the desktop go to System-->Administration-->Hardware Drivers, enable the recommended drivers. Don't get impatient, as the drivers will have to be downloaded, there really is no indicator of what it is doing until the packages have been downloaded, and the installation starts. Once the drivers have been installed you will be prompted to reboot.

Once back at your desktop, you should be able to enable full effects.

---

### Post by omarly on 2009-07-18
> **ptn107 said:**
> People who want the 185 driver should try the stable upstream PPA[1] and not the driver from nVidia's website (unless you like recompiling your drivers manually after every kernel upgrade).

```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main
```

Don't forget to import the signing key for verification.

[1] [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
this made it for me :)  after stubeling around and failing a bit with all the terminal install

thx a lot!

---

### Post by Sherfin on 2009-07-18
Thank you very much for all of your help , its perfectly working now. But i've to set the visual effects and the resolution every time i login. So , please help me out.meanwhile, i'll mark this post as solved.

                                                 :popcorn::D:D:D:D:D:D:popcorn:

---

