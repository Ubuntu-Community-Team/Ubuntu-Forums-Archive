---
title: "[SOLVED] Unable to get Broadcom 1390 WLAN working"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by rouge568 on 2007-07-24
I have a Dell e1505 with a Broadcom 1390 WLAN wireless card. I have gone through other threads in the forum, and installed ndiswrapper and the driver. Unfortunately, under "windows wireless drivers", it says that there is no hardware detected. Any advice?

---

### Post by spd106 on 2007-07-25
The command line utility is far more accurate than the windows wireless driver app (ndisgtk). So try this command instead
```
ndiswrapper -l
```
If it says that the hardware and driver are present but still doesn't work then please post the output of this command.
```
ndiswrapper -v
```


The version of ndisgtk currently in universe (v0.6) is a little buggy, so it doesn't always report the hardware or driver present even though it is. I've started the process of getting v0.7 backported from Gutsy, you can either wait for it to enter the backports repo or download it now from the link on launchpad [https://bugs.launchpad.net/feisty-backports/+bug/124444](https://bugs.launchpad.net/feisty-backports/+bug/124444)

---

### Post by Jamie Jackson on 2007-07-25
> **rouge568 said:**
> I have a Dell e1505 with a Broadcom 1390 WLAN wireless card. I have gone through other threads in the forum, and installed ndiswrapper and the driver. Unfortunately, under "windows wireless drivers", it says that there is no hardware detected. Any advice?

Here's the [easy way]("http://ubuntuforums.org/showthread.php?p=2994162").

---

### Post by rouge568 on 2007-07-26
```
scott@scott-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
scott@scott-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 
 
```
I backported the file, and it now says that the hardware is detected. However, the wifi light isn't on and I still can't reach any wireless networks. Please help.

---

### Post by gangolli on 2007-07-26
If you are trying to use the ndiswrapper driver and bcmwl5, you want to make sure you don't get the bcm43xx driver instead.

Do you have a

```
blacklist bcm43xx
``` 

line in /etc/modprobe.d/blacklist ?

To check you can do

> lshw -C network

See if configuration lists ndiswrapper or ndiswrapper+bcmwl5 as the driver.  If instead you see bcm43xx, this is the problem.  In any case I would add the blacklist entry to be sure.

---

### Post by rouge568 on 2007-07-26
I have blacklisted bcm43xx mulitple times, and it does not show as a driver.

---

### Post by gangolli on 2007-07-26
OK.  What happens now when you do

```

iwconfig

```

By the way, can you post the actual output of the

```
lshw -C network
``` 

command?

---

### Post by rouge568 on 2007-07-26
```

scott@scott-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

scott@scott-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:fc:2c:f4:55
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ecffc000-ecffffff irq:16
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:70:1b:81
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=66.63.103.116 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ecbfe000-ecbfffff irq:22

```

---

### Post by gangolli on 2007-07-26
This looks fine.  You are getting the right driver.  You are not receiving a radio signal at all.  Zero.

This suggests that you might have the wireless switch on the laptop off or you might have a BIOS setting where the wireless is not enabled by default.  Check that they are on.

Once you have done that, try this command and post the output.

```

iwlist eth1 scanning

```


Also, I would suggest adding an alias for wlan0 to get some default behaviors to work easily.

Put this in the file **/etc/modprobe.d/ndiswrapper** (not a shell command).
```

alias wlan0 ndiswrapper

```

---

### Post by rouge568 on 2007-07-26
I checked the file, and "alias wlan0 ndiswrapper" was in there. The weird thing is that right after I closed that, my network manager flashed a notice that it had found a network. Huzzah! Thank you very much: I have found this community to be one of the most helpful and knowledgeable on the web. I really appreciate your guidance.

---

### Post by gangolli on 2007-07-26
Cool.  I'm a bit troubled because I don't have an explanation for your final little miracle. It's possible that if you ran the suggested iwlist scan command got your radio enabled, but it hadn't been before. I'll watch this thread a while longer in case you have troubles on reboot.

---

### Post by rouge568 on 2007-07-26
Rebooted a couple times: Still golden, which is *tres* cool. I'll pm you if anything comes up.

---

