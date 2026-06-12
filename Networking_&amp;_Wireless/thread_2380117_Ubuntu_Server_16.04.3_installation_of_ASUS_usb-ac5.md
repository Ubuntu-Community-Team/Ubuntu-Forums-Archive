---
title: "Ubuntu Server 16.04.3 installation of ASUS usb-ac51 wifi dongle"
date: 2017-12-13
forum: Networking &amp; Wireless
---

### Post by phahh3 on 2017-12-13
hi there

I am pretty new to this, i have no experience at all in installing drivers in linux manually through terminal, normally i just use its own auto-detection of hardware.
But I happen to own this fine old pc with only a normal LAN card installed so I bought this wifi dongle: ASUS usb-ac51, i downloaded their linux driver, but then I had to give up.

So far I have done this (I have done 1 to 14 but don't understand the Build instructions in 15 and below):

Installation ASUS USB-AC51 wifi dongle:

At external pc:
 1) Downloaded latest driver: [http://dlcdnet.asus.com/pub/ASUS/wireless/USB-AC51/UT_USB_AC51_1016.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/USB-AC51/UT_USB_AC51_1016.zip)
 2) Unzipped UT_USB_AC51_1016.zip
 3) Located Linux driver in /UT_USB_AC51_1016/Linux
 4) Copied files to usbkey in dir /asus

At server pc:
 5) Insert usbkey
 6) Login as root with command: sudo -s
 7) List installed drives with command: lsblk
 8) Locate usbkey (usally called something like /dev/sdb1)
 9) Create mount dir for usbkey with command: mkdir /media/usb
10) Mount usbkey with command: mount /dev/sdb1 /media/usb
11) Install driver dependencies and wifitools with these commands:
    apt-get install build-essential
    apt-get install linux-headers-generic
    apt-get install wireless-tools
    apt-get install wpa_supplicant
12) Change to asus dir at usbkey with command: cd /media/usb/asus
13) Untar driverpackage to subdir with command: tar -xvf mt7610u_wifi_sta_v3001_dpo_20130725.tar
14) Change to driver subdir with command: cd mt7610u_wifi_sta_v3001_dpo_20130725
15) Follow Build Instructions below

========================================
Build Instructions:  

========================================


1> In Makefile
     
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     
     define the linux kernel source include file path LINUX_SRC
     
     modify to meet your need.


2> In os/linux/config.mk 
    
     define the GCC and LD of the target machine
    
     define the compiler flags CFLAGS
    
     modify to meet your need.
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
              
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
     ** Build for being controlled by WpaSupplicant with Ralink Driver
       
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

3> $make            
    
     # compile driver source code, need administrator.
    
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
     
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

4> $make install
     #install driver
     #copy RT2870STA.dat to /etc/Wireless/RT2870STA/RT2870STA.dat

5>$vi /etc/rc.d/rc.local
     #input "ifconfig ra0 up"

     ** Ubuntu 13.04 don't have this file.
    $reboot

6> unload driver    
    
     $ifconfig ra0 down

     $make uninstall
     $reboot


Note: If you want to change os/linux/config.mk setting, please remove driver and  reinstall.

========================================
Build Instructions (Workaround):  

========================================

A lot of people are having trouble trying to use the ASUS AC51 on the latest versions of Ubuntu. 
The code that I'll paste below, will fix your AC51 so you can use it on Ubuntu or the other distributions of Linux. 
You wont get 5GHZ but it will work.

    mkdir ~/src
    cd ~/src
    git clone [https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git](https://github.com/Myria-de/mt7610u_wifi_sta_v3002_dpo_20130916.git)
    cd mt7610u_wifi_sta_v3002_dpo_20130916
    make clean
    make
    sudo make install
    reboot

---

Please help me? Google is NOT my friend in this, I have tried for hours!

---

### Post by howefield on 2017-12-13
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by chili555 on 2017-12-13
You will never get this circa-2013 driver to compile properly in any recent Ubuntu kernel. Please see: [https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504](https://askubuntu.com/questions/975464/mt7610u-unable-to-install-wifi-driver/975504#975504) as well as: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u) at post #18.> The most salient point, in my opinion, is that praseodym, Jeremy, Hadaka, Pilot6, wildmanne and I have all worked on these mt7610u chipsets for years. With the available drivers and a newer kernel version; that is, not yet end-of-life, I have not seen ANY case where it actually connects and pulls web pages.

I suggest that you get a different device.

---

