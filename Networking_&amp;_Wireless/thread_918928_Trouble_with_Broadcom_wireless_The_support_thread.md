---
title: "Trouble with Broadcom wireless? The support thread"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by Halbarad on 2008-09-13
There is a thread about Broadcom which is not for support, as the users have been recently reminded. This might make sense or not -- having all in the same thread would perhaps be more convenient, but there are several styles of debugging.
The [COLOR="Blue"]purpose of the present thread[/COLOR] is merely to host **[SIZE="3"][COLOR="Blue"]all[/COLOR][/SIZE]** the questions, replies and open problems which people who still have some kind of trouble with their Broadcom wireless would like to discuss.

Thus, I begin with a reply to Sam Lars (Hi, Sam!)
> will this also be included in Intrepid? I loaded Intrepid, and it didn't "just work." I had to load Ndiswrapper. Maybe I missed something?

If you mean the new Broadcom wl driver, it is "installed and currently in use" in my updated version of Intrepid alpha5, but the wireless is dead.

```
~$ uname -r
2.6.27-3-generic

~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:4d:e6:84
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.200 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:4a:b3:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Something is clearly wrong with the way Linux sees my hardware, since I have only one wired and one wireless. And the driver should be wl, not b43-whatever. Let's hope this is going to be fixed soon in Intrepid...
EDIT: My Broadcom 4311 worked under Hardy 8.04, after applying Superm1's fix. The system recognized a single wireless, with the driver wl.

---

### Post by jrwagz on 2009-06-06
> **Halbarad said:**
> There is a thread about Broadcom which is not for support, as the users have been recently reminded. This might make sense or not -- having all in the same thread would perhaps be more convenient, but there are several styles of debugging.
The [COLOR=Blue]purpose of the present thread[/COLOR] is merely to host **[SIZE=3][COLOR=Blue]all[/COLOR][/SIZE]** the questions, replies and open problems which people who still have some kind of trouble with their Broadcom wireless would like to discuss.

Hi I am having issues installing my Broadcom driver.  I have been trying to follow the instructions provided here [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) however I get the follow error when trying to build the LKM

```
root@justin-laptop:/home/justin/hybrid_wl# ls
hybrid-portsrc-x86_32-v5_10_91_9.tar.gz  lib  Makefile  src
root@justin-laptop:/home/justin/hybrid_wl# make -C /lib/modules/2.6.28-11-generic/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
root@justin-laptop:/home/justin/hybrid_wl# 
```Any and all help is appreciated.  I am very new to Ubuntu and might be making some idiotic mistake, but I just don't know what it is!  THANKS!

---

### Post by snowpine on 2009-06-06
Try changing

make -C /lib/modules/2.6.28-11-generic/build M='pwd'

to

make -C /lib/modules/2.6.28-11-generic/build M=`pwd`

In the future, copy & paste will prevent this kind of error.

---

### Post by jrwagz on 2009-06-08
> **snowpine said:**
> Try changing

make -C /lib/modules/2.6.28-11-generic/build M='pwd'

to

make -C /lib/modules/2.6.28-11-generic/build M=`pwd`

In the future, copy & paste will prevent this kind of error.
Thanks!  Like I said I am a beginner and I figured it was something like that!  Now I am getting stuck on this part of the instructions from Broadcom

> 2.  Replacing existing driver with wl.ko just build in step 5 above.
      (most likely path to find wl.ko is: /lib/modules/<kernel_version>/kernel/driver/net/wireless
       or /lib/modules/<kernel_version>/kernel.net/update/)
3.  depmod
4.  modprobe wl

Could you please shed some light for me?

Here  is what I tried:
```
root@justin-laptop:/home/justin# ls
Desktop    examples.desktop  Music     Public     Videos
Documents  hybrid_wl         Pictures  Templates
root@justin-laptop:/home/justin# cd hybrid_wl
root@justin-laptop:/home/justin/hybrid_wl# ls
built-in.o                               Module.markers  wl.ko
hybrid-portsrc-x86_32-v5_10_91_9.tar.gz  modules.order   wl.mod.c
lib                                      Module.symvers  wl.mod.o
Makefile                                 src             wl.o
root@justin-laptop:/home/justin/hybrid_wl# depmod
root@justin-laptop:/home/justin/hybrid_wl# modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@justin-laptop:/home/justin/hybrid_wl# 
```

---

