---
title: "nVidia - what is the proper way to install nVidia Drivers?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by cwmoser on 2009-01-11
I have difficulty installing nVidia video drivers.
So, what is the proper way to install them?

The only way I could get the nVidia video drivers to install properly for Ubuntu 8.04 was using the package "Envy".  Envy works for 8.04, but does not work for Ubuntu 8.10.

I downloaded the drivers from nVidia's website and ran:
**NVIDIA-Linux-x86-180.22.pkg1.run**

It installed without error.  Then I ran **nvidia-xconfig**.

But, when I run the settings utility, **nvidia-settings**, I get this message:

[COLOR="DarkRed"]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/COLOR]

I run **nvidia-xconfig** and restart X and still I get this message.

So, what is the proper process to install nVidia video drivers?

Thanks

Carl

---

### Post by RomeReactor on 2009-01-11
Hi. There are several posts on the nVidia forums [regarding]("http://www.nvnews.net/vbulletin/showthread.php?t=126093") [problems]("http://www.nvnews.net/vbulletin/showthread.php?t=125964") [installing]("http://www.nvnews.net/vbulletin/showthread.php?t=126003") [the 180.22 driver]("http://www.nvnews.net/vbulletin/showthread.php?t=126063"). One of the problems is that it seems the driver complains about a kernel module version mismatch; try looking in 'System->Administration->System Log' for this message:
> API mismatch: the client has the version 180.22, but this kernel module has the version ***.**
Try removing the current driver: from the terminal, navigate to where the driver is, stop gdm:
```
sudo /etc/init.d/gdm stop
```
and remove the driver:
```
sudo sh NVIDIA-Linux-x86-180.22-pkg1.run --uninstall
```
Then install the one in 'System->Applications->Hardware Drivers', or the [180.16]("ftp://download.nvidia.com/XFree86/Linux-x86/180.16/NVIDIA-Linux-x86-180.16-pkg1.run").

NOTE: I just edited the post to correct the driver version in the uninstall command (was x86_64 before) and the link to the driver (was x86_64 also). Sorry for the confusion.

---

### Post by lazyart on 2009-01-11
the catch is that when you run the settings utility it will always report that you are not using the nvidia drivers...

*unless you run it as root.*

```
gksudo nvidia-settings
```

---

### Post by nrjrfmg on 2009-01-20
This solution worked for Ubuntu 8.04 and it should be OK for some other Linux distributions too but not for all.

After installing the NVIDIA driver make sure the location where it was installed

ls -l /lib/modules/`uname-r`/kernel/drivers/video/nvidia.ko

-rw-r-r-1 root root 11224469 2009-01-19 11:15 nvidia.ko

verify that the file date is the one when you installed the driver, i.e. January 2009

Stop the Xserver like in this case is gdm
/etc/init.d/gdm stop

if you see the error window of xorg configuration kill its processes

ps xa | grep safe
kill -9 + processid separated by space

remove nvidia module
rmmod nvidia

Remove all the old files on this directory
rm /lib/modules/`uname-r`/kernel/drivers/video/nvidia/*

move the new driver file to the directory where the system will search for and finding the old ones resulting in the well known API version error.
mv /lib/modules/`uname-r`/kernel/drivers/video/nvidia.ko /lib/modules/`uname -r`/kernel/drivers/video/nvidia/

load the new nvidia 180.22 kernel module
modprobe nvidia

start the X server wich in this case is gdm
/etc/init.d/gdm start

That's all folks.

I hope this little guide would be helpfull.

Cheers. ;)

---

