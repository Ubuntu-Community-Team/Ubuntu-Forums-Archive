---
title: "How to install wireless linux driver (ENLWI-N)"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by mooncaptain on 2008-08-17
I have downloaded the .zip from the manufacturer's website and README_STA file has instructions for compiling. However the driver has only been tested on Redhat and the target directory for the driver file is /etc/wireless/nameofdriver and the etc/wireless folder doesn't currently exist on my system so I don't know if this is the appropriate location in Ubuntu.

Below are the build instructions from the readme.txt

I haven't any idea if they will work in the Ubuntu environment.

I have already downloaded and installed build-essential and
linux-headers-generic

I haven't done any development on Ubuntu except for editing web pages so any help would be appreciated.

Thanks

mc

Link to Linux driver for the wireless card.

[http://www.encore-usa.com/download/driver/ENLWI-N_ENPWI-N_Linux_Driver.zip](http://www.encore-usa.com/download/driver/ENLWI-N_ENPWI-N_Linux_Driver.zip)

------------------------------------------------------------------Here

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
 
4> $make                                    # compile driver source code 
 
5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat        
    # !!!check if it is a binary file before loading !!!   
     
6> load driver 
    #[kernel 2.4] 
    #    $/sbin/insmod rt2860sta.o 
    #    $/sbin/ifconfig ra0 inet YOUR_IP up 
         
    #[kernel 2.6] 
    #    $/sbin/insmod rt2860sta.ko 
    #    $/sbin/ifconfig ra0 inet YOUR_IP up 
 
7> unload driver     
    $/sbin/ifconfig ra0 down 
    $/sbin/rmmod rt2860sta 
     
=======================================================================

---

### Post by mooncaptain on 2008-08-17
Why the thumbs down icon?

---

### Post by mooncaptain on 2008-08-18
> **mooncaptain said:**
> Why the thumbs down icon?
Ok, I figured out the icon. but I am still stuck with the wireless driver.

---

### Post by mooncaptain on 2008-08-24
1st forget the linux driver - looks difficult and requires compiling and knowing more than an end user should be required to know.

This is how I did it.

1. Run the setup for the PCI card on a windows machine. It doesn't matter if the card is present or not.
2. Locate the ```
"C:\Program Files\None\802.11n PCI Wireless LAN Card\Driver"
``` folder on the the Windows and copy it to a USB.
3. You'll need to install the Windows Wireless Drivers utility on the target system. A discussion for another thread that has been covered else ware plus I forgot how I did it without a network connection. There is a way.
4. Plug the USB into your target system
5. Run the System/Windows Wireless Drivers utility
6. Click Add new Driver and navigate to the folder on the USB driver.
7. Select the .inf file and install.
8. Left mouse click the network icon on the tool bar at top of Ubuntu.
9. Select Wireless

It worked immediately for me.

---

### Post by duckytn on 2008-08-25
> **mooncaptain said:**
> 1st forget the linux driver - looks difficult and requires compiling and knowing more than an end user should be required to know.

This is how I did it.

1. Run the setup for the PCI card on a windows machine. It doesn't matter if the card is present or not.
2. Locate the ```
"C:\Program Files\None\802.11n PCI Wireless LAN Card\Driver"
``` folder on the the Windows and copy it to a USB.
3. You'll need to install the Windows Wireless Drivers utility on the target system. A discussion for another thread that has been covered else ware plus I forgot how I did it without a network connection. There is a way.
4. Plug the USB into your target system
5. Run the System/Windows Wireless Drivers utility
6. Click Add new Driver and navigate to the folder on the USB driver.
7. Select the .inf file and install.
8. Left mouse click the network icon on the tool bar at top of Ubuntu.
9. Select Wireless

It worked immediately for me.

Worked like a charm for me as well. One small note. I simply used the install CD to load the drivers and skipped the loading on a Windows system. I really appreciate your help with this! (even though I did not originally ask).

Cheers!

---

### Post by mooncaptain on 2008-08-26
How did you get the windows setup.exe to run under Ubuntu? I coulnd't make it work.

---

### Post by anand on 2008-09-06
These are the only instructions I've found to get the Linux source driver to work:
[http://ubuntuforums.org/showpost.php?p=5062485&postcount=36](http://ubuntuforums.org/showpost.php?p=5062485&postcount=36)

I guess the disadvantage of that method is that moving around to different APs will be a pain but since I'm using on a stationary computer it doesn't really bother me.

The only additional step I had to take was to put "rt2860sta" in the /etc/modules file so make it automatically load on startup (it wasn't do it before for some reason).

I never had a luck with the ndiswrapper method.  I could list the APs but could never actually attach to mine as it always rejected my WEP passphrase.  I saw some posts showing others having the same problem and the workaround was disabling security on your wireless network which I didn't want to do.

---

### Post by umatchan on 2009-01-19
Does this card support 300mbps under ubuntu (8.04 or 8.10)

---

