---
title: "wireless drivers"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Dontais on 2008-06-10
I have been trying to install some drivers for a realtek l8185 wireless nic card. I went into the dictionary and tried the insall instructions: 

```

< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.
```

And it keeps coming back cannot be found for device.

---

### Post by chili555 on 2008-06-10
Did *./makedrv* run without any errors?

---

### Post by Dontais on 2008-06-10
I am not familiar with linux to much but here is what I recived when I ran the [./makedvr  ]("http://aa.1asphost.com/Dontais/makedvr.txt")

---

### Post by chili555 on 2008-06-10
> make[2]: *** [/home/james/Desktop/rtl8185/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/james/Desktop/rtl8185/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2When a 'make' or in your case, a 'makedrv' ends in errors, there is no need to proceed. You must correct the errors first in order to build a usable driver for your card.

You might have better luck here: [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page) especially see this: > If you run kernel 2.6.24 use this one : [http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html](http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html) (mirrored here : [http://kjo.herbesfolles.org/docs/rtl818x-mod2.6.24.tar.bz2](http://kjo.herbesfolles.org/docs/rtl818x-mod2.6.24.tar.bz2)) 

I got that one to compile with a couple of harmless warnings and no errors. However, since I do not have the RTL8185 device, I don't know if it works.

---

