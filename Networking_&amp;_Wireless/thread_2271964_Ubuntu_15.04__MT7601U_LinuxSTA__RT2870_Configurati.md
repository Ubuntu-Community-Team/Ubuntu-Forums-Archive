---
title: "Ubuntu 15.04 | MT7601U_LinuxSTA | RT2870 Configuration | USB Wifi Chinese Dongle"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by jskandhari on 2015-04-03
Well various people have posted various inputs to make this driver work, here me posting mine. 

apparently the drivers suggested for RT2870 from Media link are old and newer version is available which has most of the configurations already done and goes by the name **DPO_MT7601U_LinuxSTA_3.0.0.4_20130913**

Firstly I would like to thank contributers to following links for the inputs which made it work or allowed me to put 2+2 together to make it work.


[http://ubuntuforums.org/showthread.php?t=2152658](http://ubuntuforums.org/showthread.php?t=2152658) <-- Most of the changes are already made in the DPO package
[http://ubuntuforums.org/showthread.php?t=2228347](http://ubuntuforums.org/showthread.php?t=2228347) <-- This allowed me to understand most of it

So the challenge being faced by me was at line 1221 & 1122 of rt_linux.c file which was not allowing my Make to complete hence I simply commented those two lines to facilitate the building (actually inshort I did this only I think which made it work but the whole process is as follows )

**Step #1: Disable Default Drivers**

Type the following command to black list default drivers:
$ sudo vi /etc/modprobe.d/blacklist.conf
Append the following driver names:
```

blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```

Save and close the file.
Reboot

**Step #2 Correcting rt_inux.c (My Version already has it commented )**

Goto Extracted Driver folder (preferably in Terminal & stay in it if stated otherwise) & in it make your way to os/linus (cd os/linux)
open file rt_linux.c comment the following lines (find & replace )

```
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,29)
		pOSFSInfo->fsuid = current->fsuid;
		pOSFSInfo->fsgid = current->fsgid;
		current->fsuid = current->fsgid = 0;
//#else
//		pOSFSInfo->fsuid = current_fsuid();
//		pOSFSInfo->fsgid = current_fsgid();
#endif
		pOSFSInfo->fs = get_fs();
		set_fs(KERNEL_DS);
	} else {
```

in terminal come back to Extracted folder location ( in my case $cd '/home/arvind/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913' )

Go to DRIVER_FOLDER/include/os
Open rt_linux.h with your favorite text editor (e.g. gedit)
Changing all occurances of these function calls (two important functions were renamed in the newer versions of Ubuntu):
**usb_buffer_alloc** CHANGES TO **usb_alloc_coherent**
**usb_buffer_free** CHANGES TO **usb_free_coherent**

Come back to DRIVER_FOLDER

**Step #2.2 sta_cfg.c EDIT ** <-- Required for Ubuntu 15.04 onwards only, prior version Ubuntu can skip this step

Apparently sta_cfg.c Line Number 5766 throws warning which is treated as error.  

```
/home/arvind/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5766:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                     ^
/home/arvind/Downloads/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5766:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             snprintf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                               ^

```

Solution : Goto Line No.. 5766 and remove ** ,__DATE__, __TIME__ ** from the line.

**Step #3 Make Clean **

If you are utilising my version of folder please perform make clean operation 

```
sudo make clean
```
[B]
Step #4 Most Imp Step  (I did it in root mode )[/B]

```
sudo lsusb
```
Lets build
```
sudo -i
```
Navigate to Driver Folder
```
make
```
This should complete successfully without Errors, a few warnings are normal ignore them.

After completion give it a while i.e. give it 60secs ( I gave it 3 or maybe less)
```
make install
```

```
cd ~
```
```
modprobe mt7601Usta
```

Remove the Dongle and reinsert it
```
lsusb
```
It should reflect there and your Network manager on top right should show you your wifi signals 
[B]
Files :- [/B]
My Version : [DPO_MT7601U_LinuxSTA_3.0.0.4_20130913_myfolder.tar.bz2]("https://drive.google.com/file/d/0BwZtsBIiDfUFbncxUEhPczI2WDA/view?usp=sharing")
Orignal : [DPO_MT7601U_LinuxSTA_3.0.0.4_20130913_orignal.tar.bz2]("https://drive.google.com/file/d/0BwZtsBIiDfUFbEIwVjVVZVN1N00/view?usp=sharing")

---

