---
title: "make command not found??? wireless card install problem"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by blackdalek on 2006-09-05
I'm trying to install drivers for a DLink DWL-G510 ver C2 using the instructions here... [http://forums.whirlpool.net.au/index.cfm?a=wiki&tag=rt61](http://forums.whirlpool.net.au/index.cfm?a=wiki&tag=rt61)

I get as far as typing "make all"

and computer responds with "bash: make: command not found"

What am I doing wrong?

---

### Post by majesticturkey on 2006-09-06
you need to install the package build-essential.

sudo apt-get install build-essential

If you can't connect to the internet, it's on the CD.

---

### Post by blackdalek on 2006-09-06
I can get internet access through ethernet, so that's ok.
I got the build-essential package now.
I just noticed on that page with the instructions, it also says I will need "kernel headers" package - Do I have this already or do I need to install that too and how?

---

### Post by blackdalek on 2006-09-06
> **blackdalek said:**
> I can get internet access through ethernet, so that's ok.
I got the build-essential package now.
I just noticed on that page with the instructions, it also says I will need "kernel headers" package - Do I have this already or do I need to install that too and how?

I guess I must still need to install something else because I am getting this error when I try to do "make all" 

```
somename@somename-desktop:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/somename/Desktop/RT61_L inux_STA_Drv1.0.4.0/Module modules
make: *** /lib/modules/2.6.15-26-686/build: No such file or directory.  Stop.
make: *** [all] Error 2
somename@somename-desktop:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$
```

Is this because I don't have "kernel headers" package?
What is the command to install it? - sudo apt-get install kernel-headers perhaps? Will that do it?

---

### Post by blackdalek on 2006-09-06
ok.. someone in IRC showed me how to get kernel headers package installed, now I get a whole bunch of errors from "make all" -
```
somename@somename-desktop:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_main.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_main.c:39:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:39:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ‘STAMlmePeriodicExec’:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:734: warning: unused variable ‘RxSignal’
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ‘AsicSwitchChannel’:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:3671: warning: comparison is always false due to limited range of data type
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:3588: warning: ‘BbpReg’ may be used uninitialized in this function
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ‘AsicAdjustTxPower’:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:4268: warning: ‘BbpR1’ may be used uninitialized in this function
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ‘AsicSetRxAnt’:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5397: warning: ‘R77’ may be used uninitialized in this function
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5421: warning: ‘R77’ may be used uninitialized in this function
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5446: warning: ‘R77’ may be used uninitialized in this function
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c: In function ‘RadarDetectionStop’:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.c:5781: warning: ‘R66’ may be used uninitialized in this function
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/connect.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/connect.c:37:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/sync.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/sync.c:38:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/assoc.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/assoc.c:37:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/auth.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/auth.c:37:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/auth_rsp.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/auth_rsp.c:27:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_data.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_data.c:39:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_init.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_init.c:40:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/sanity.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/sanity.c:38:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_wep.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_wep.c:38:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_info.c:40:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/eeprom.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/eeprom.c:37:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_tkip.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp_tkip.c:38:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/wpa.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/wpa.c:39:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  CC [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/md5.o
In file included from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/mlme.h:43,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rtmp.h:44,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt_config.h:156,
                 from /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/md5.c:20:
/home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/oid.h:109:5: warning: "DBG" is not defined
  LD [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.o
  Building modules, stage 2.
  MODPOST
  CC      /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.mod.o
  LD [M]  /home/somename/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
somename@somename-desktop:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$
```

What now?

---

### Post by blackdalek on 2006-09-06
right, I just ignored all those warnings posted in the previous reply, and went ahead with the rest of the installation instructions. Result - now my computer won't boot at all. It just gets to "configuring network interfaces" during boot, then after a few minutes the screen changes from the grahpical one to the text one still showing "configuring network interfaces" and it just hangs and dies.
I have to physically remove the wifi card from the computer to get it to boot now. Aarrrgh!!

What have I done? have I broken my network setup completely now?

---

### Post by blackdalek on 2006-09-08
I've found out that going into the System>Administration>Networking control panel is what causes the computer to lock up at bootup.
Still no further ahead. I just can't seem to find instructions anywhere  for configuring a RT61 card for WPA-PSK encryption - it seems to me that every "how to" on here for RT61 is specifically for WEP, and every "how to" for WPA-PSK is for chipsets other than RT61.
Is RT61 + WPA simply not supported in Ubuntu? It would appear that way. I'm not going to change my network from WPA to WEP just to suit Ubuntu :(

---

### Post by rangelife on 2006-09-10
I'm seeing a similar problem..

Asus WL-167G usb wifi dongle .. compiling the RT73 drivers suggested.

I already upgraded from Hoary -> Breezy -> Dapper so the system should recognise the device

It recognises it and I can perform a scan but as soon as I start the connection (about when dhclient runs) the whole system hangs.

Anyway.. so I got hold of the drivers source.

I already installed build-essential and every other package I've seen mentioned on this topic


When I build, I see:

robdesktop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module> uname -r
2.6.15-26-386
robdesktop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module> make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/rob/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
robdesktop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module> sudo apt-get install kernel-headers
Reading package lists... Done
Building dependency tree... Done
Package kernel-headers is a virtual package provided by:
  kernel-headers-2.4.27-2-k7-smp 2.4.27-12
  kernel-headers-2.4.27-2-k7 2.4.27-12
  kernel-headers-2.4.27-2-k6 2.4.27-12
  kernel-headers-2.4.27-2-686-smp 2.4.27-12
  kernel-headers-2.4.27-2-686 2.4.27-12
  kernel-headers-2.4.27-2-586tsc 2.4.27-12
  kernel-headers-2.4.27-2-386 2.4.27-12
  kernel-headers-2.4.27-2 2.4.27-12
You should explicitly select one to install.
E: Package kernel-headers has no installation candidate
robdesktop:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module>

 
Is the last thing I did revealing a problem (ie why the discrepancy between 2.4.27-2 and 2.6.15-26)

---

### Post by blackdalek on 2006-09-10
Well, I finally got the wireless card to work (sort of) thanks to some help from people on IRC.

I have a script to make it load and retrieve an IP from the DHCP server on boot up, but this only seems to work about 1 out of every 3 boots - it just can't find the network to get an IP.

And when it does load properly, it has trouble staying connected when idle and I have to reboot the machine to get it to work again if it loses contact. :(

---

