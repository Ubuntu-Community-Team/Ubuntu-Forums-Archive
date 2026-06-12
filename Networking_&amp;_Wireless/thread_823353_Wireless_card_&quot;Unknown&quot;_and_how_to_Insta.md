---
title: "Wireless card &quot;Unknown&quot; and how to Install drivers for it"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by thejamesman on 2008-06-09
Hi all,

I recently installed a Ralink-chipset (Encore ENLWI-N) card into my system and acquired the drivers for it. Unfortunately, im brand-new to ubuntu, and havent the faintest idea of how to install.

Could someone give me a walk-through?

I have the .tar.gz package downloaded from the manufacturer.

---

### Post by chili555 on 2008-06-09
I went to the manufacturers website and downloaded a .zip file. It might help if you could give us the link so we can all read from the same page.

Generally, the process is to install the tools needed to compile from source:```
sudo apt-get install build-essential
sudo apt-get install linux-headers-generic
```If you can see the .tar.gz in your home folder, or perhaps on your desktop, you should be able to right click the file and select 'Extract here.' A new folder will be created; for the moment, let's call it Encore_driver. Open a terminal, and assuming the folder is on your desktop, do:```
cd Desktop/Encore_driver
less README.txt
```It will explain the install process, which will typically be make, sudo make install, modprobe r2860.ko.

Post back when you get stuck.

---

### Post by mooncaptain on 2008-08-16
I have downloaded the .zip from the manufacturer's website and README_STA file has instructions for compiling. However the driver has only been tested on Redhat and the target directory for the driver file is /etc/wireless/nameofdriver and the etc/wireless folder doesn't currently exist on my system so I don't know if this is the appropriate location in Ubuntu.

Here are the build instructions from the readme.txt

I haven't any idea if they will work in the Ubuntu environment.

I have already downloaded and installed build-essential and 
linux-headers-generic



Any help would be appreciated.

Thanks

MC

Link to Linux driver for the wireless card.

[http://www.encore-usa.com/download/driver/ENLWI-N_ENPWI-N_Linux_Driver.zip](http://www.encore-usa.com/download/driver/ENLWI-N_ENPWI-N_Linux_Driver.zip)

------------------------------------------------------------------

Build Instructions:  

====================



1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz

    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.

    

2> In Makefile

	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"

	 define the linux kernel source include file path LINUX_SRC

	 modify to meet your need.



3> In os/linux/config.mk 

	define the GCC and LD of the target machine

	define the compiler flags CFLAGS

	modify to meet your need.

	** Build for being controlled by NetworkManager

	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.

	** Build for being controlled by WpaSupplicant with Ralink Driver

	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.

4> $make									# compile driver source code

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    # !!!check if it is a binary file before loading !!!  

6> load driver
Build Instructions:

---

