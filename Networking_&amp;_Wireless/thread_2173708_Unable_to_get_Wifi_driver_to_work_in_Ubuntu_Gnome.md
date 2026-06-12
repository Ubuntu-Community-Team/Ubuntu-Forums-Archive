---
title: "Unable to get Wifi driver to work in Ubuntu Gnome"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by morrison2 on 2013-09-10
I have a wireless adapter (edimax ew-7733und) that uses the Ralink RT3573 chipset driver. I extracted the file and installed it and gnome still can't detect my wireless adapter. Even though the driver comes with installation instructions I feel as if I'm missing something. I was wondering what I did wrong. Any help?

---

### Post by morrison2 on 2013-09-11
some additional information:

I have done the following in the terminal:

cd Desktop
tar -jxf driver.bz2
make
make install

I don't know if the following instructions are to be done before or after the "make/make install" process. Kind of confused.




Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta

---

### Post by morrison2 on 2013-09-12
Anyone know if the 2d1211rw drive is a lot like the 2d1211 drive? Is there an updated version of the mac80211 zd1211rw?

---

### Post by varunendra on 2013-09-13
Welcome to the forums morrison !

If you are using the driver that came 'With' the adapter, then it is most probably outdated and not compatible with the current kernels.

Please plug in the adapter, and post back the outputs of -
```
lsb_release -d
uname -mr
lsusb
lsmod | egrep 'rt2|rt3'
```

While posting the outputs, please use 'Code' tags to preserve its formatting (follow the link in my signature to see how). Thanks.

---

### Post by morrison2 on 2013-09-13
> **varunendra said:**
> Welcome to the forums morrison !

If you are using the driver that came 'With' the adapter, then it is most probably outdated and not compatible with the current kernels.

Please plug in the adapter, and post back the outputs of -
```
lsb_release -d
uname -mr
lsusb
lsmod | egrep 'rt2|rt3'
```

While posting the outputs, please use 'Code' tags to preserve its formatting (follow the link in my signature to see how). Thanks.


Thank you for your warm welcoming. Yes, you're right. It seems the usb adapter I was using is not compatible with the current gnome kernels. I decided to purchase a Zyxel AG225H and had good luck with it so far, it was recognized instantly without downloading any drivers.


When I typed in the command I received this:

Description: Ubuntu 10.04.3 LTS

3.2.6 i686

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 0586:3413 ZyXEL Communications Corp. ZyAIR AG-225H v2 802.11bg
Bus 003 Device 005: ID 0e0f:0008 VMware, Inc. 
Bus 003 Device 004: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 003 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 003 Device 002: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 154b:005b PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by varunendra on 2013-09-13
So.. did you return the old one? Is the new one working fine? If so, then I guess we have nothing to solve any more :P

By the way -
> **morrison2 said:**
> 
Description: **[COLOR="#FF0000"]Ubuntu 10.04.3 LTS[/COLOR]**

3.2.6 i686

..is a bit outdated too.. You seem to have a newer kernel, but is not "current" actually and you won't get any updates or much support in case of issues. I'd recommend to upgrade to 12.04.3, 64 bit if your system can support it.

If you decide to upgrade, I'd suggest to download the ISO via [torrent]("http://www.ubuntu.com/download/desktop/alternative-downloads") to ensure integrity, and test it in live mode before trying to install, to check if it supports your hardware nicely or not.

With newer kernel and packages, maybe even your earlier one might work out-of-box.

---

### Post by morrison2 on 2013-09-15
:p thank you for the help, varunendra. I'll try that method of installing the upgrade and see if anything turns out well.

---

