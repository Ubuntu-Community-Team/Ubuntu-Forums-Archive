---
title: "WUSB54G (Ver.1) no signal on wireless points?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by odox on 2007-03-19
I've been trying to get the wireless working on edgy for a while now.

At first I thought it was a driver problem, but edgy seems to pick up the wireless usb as soon as it's plugged in and uses the default driver.

However, using network manager Applet 0.6.3 - it's detecting all the wireless points around the house but showing no signal on any of them! I can't connect either, just seems to loop.

Any ideas?

Thanks. (p.s bit of a newb, got everything working but this now!)

---

### Post by handaxe on 2007-03-19
```
sudo lshw -C network
```
```
 sudo ifconfig
```
```
 sudo iwconfig
```

outputs please

HA

---

### Post by odox on 2007-03-19
*-network               
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0f:66:0f:b6:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
-------------------------------------------------------------------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:13:D4:F5:88:D5  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fef5:88d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1796942 (1.7 MiB)  TX bytes:345163 (337.0 KiB)
          Interrupt:58 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:0F:66:0F:B6:A7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452 (452.0 b)  TX bytes:452 (452.0 b)

--------------------------------------------------------------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel=4  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Thanks for taking the time..

---

### Post by handaxe on 2007-03-19
There does not appear to be driver loaded for your wireless card.

```
lsusb
```

please.

And what in case it does not show, what make (details)

HA

---

### Post by odox on 2007-03-19
Bus 002 Device 003: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0204:6025  
Bus 001 Device 002: ID 5041:2234 Linksys (?) WUSB54G 802.11g Adapter
Bus 001 Device 001: ID 0000:0000

---

### Post by handaxe on 2007-03-19
Hi,

The driver definitely is the issue. I don't have time to research this as there seems to be two options:

one is to use a native linux driver and the other is to use a "wrapper" called ndiswrapper around the windows driver.

I suggest the following: go to [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)
 and use the "search this forum" function with Linksys WUSB54.

There will be a lot to read :-) but aim for threads mentioning Edgy.

Hope this helps,

HA

PS I do wonder why the built in edgy driver for this wireless did not load...

---

### Post by odox on 2007-03-19
Thanks for your help so far HA, i've attempted to use ndiswrapper to install the drivers but this doesn't seem to have made any difference.


I've tried searching the forum for someone using this type of USB wireless connection on edgy but have found nothing!

I'd be happy to try the "native linux driver" but i've no idea how. 

Can anyone help?

Thanks

---

### Post by div3rg3nt on 2007-03-26
You may just want to manually specify the access point in the settings for the wireless adapter. That is how I was able to get mine to work since I am unable to detect any wireless access points, even though the access point is in my line of sight.

---

### Post by handaxe on 2007-03-26
Hi Odox,

Firstly, I was probably off the mark when I assessed your data as indicating that a driver was not loaded. The "sudo lshw" command shows loaded drivers, except it seems in the case of usb wireless or at least the wusb54 flavours. And so we learn..(can anyone confirm this?).

ndiswrapper -l (I think that's the command) should show if driver and hardware are there;

also "dmesg | grep ndis".

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L) item 7 suggests ndiswrapper should work just fine.

Alternatively, there is the islsm (or native) driver. Edgy has this and is the one you should be blacklisting under ndiswrapper as it is the one that should be loading for your device. This driver requires a firmware and Edgy has this (search your system for isl38 and it will pop up.  No need to worry about this as it should load automatically (I think....(oh dear :roll: !). 

So, if ndiswrapper is **out** of the equation, ```
sudo depmod -a
sudo modprobe islsm_usb
``` should load the drivers and create the interface.

Use ```
dmesg | grep isl
``` to ckeck if the drive loaded, then the sudo iwconfig igconfig stuff

Feeling adventurous? [http://www.prism54.org/newdrivers.html](http://www.prism54.org/newdrivers.html) and [http://jbnote.free.fr/prism54usb/index.html](http://jbnote.free.fr/prism54usb/index.html) are where you get the latest versions of the prism54 (your chipset) drivers.

 Your type of card seems quite problematic on Edgy, as many write with issues.

Below are the most relevant links I could find:

[http://ubuntuforums.org/showthread.php?t=296959&highlight=wusb54g+edgy](http://ubuntuforums.org/showthread.php?t=296959&highlight=wusb54g+edgy)
[http://www.ubuntuforums.org/showthread.php?t=385559&highlight=wusb54g+edgy](http://www.ubuntuforums.org/showthread.php?t=385559&highlight=wusb54g+edgy)
[http://ubuntuforums.org/showthread.php?t=375218&highlight=wusb54g+edgy](http://ubuntuforums.org/showthread.php?t=375218&highlight=wusb54g+edgy)
[http://ubuntuforums.org/showthread.php?t=216031&highlight=usb+wireless](http://ubuntuforums.org/showthread.php?t=216031&highlight=usb+wireless)

Good luck!!

HA

---

