---
title: "Installing/Compling Wifi drivers"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by faustt on 2010-08-20
Still pretty new to linux. I've been using it as my primary OS for about 6 months. I can usually figure stuff out on my own, but this has me a little stumped.

I got a new wifi card. the chipset is RT3090BC4. I have the drivers, they're decompressed, the readme kinda loses me though.

```

2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

```
I understand I need to edit the make file. mode = sta and target both are already correct. LINUX_SRC: I'm guessing needs to point to the source of my kernel? Wheres the source usually located?  Does this mean I have to recompile it after each kernel update as well?
```

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

```

This might as well be written in greek =D. Completely lost at this point.
```

4> $make			
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c


```

make. got it.

```


5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       


```

copy compiled driver to /etc/wireless directory, got it. 
```
   
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

```
do I really have to manually load it at each bootup? If the driver is installed can I just use the GUI network manager?

I'm back in windows until I can figure this out. Any help would be great. 

Thanks!

---

### Post by Gone fishing on 2010-08-20
I believe your wireless card will work with the karmic driver on this page (deb package)

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

have a look at:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

Post edit:

Also have a look at [http://ubuntuforums.org/showthread.php?t=1274886&highlight=RT3090&page=8](http://ubuntuforums.org/showthread.php?t=1274886&highlight=RT3090&page=8)

---

