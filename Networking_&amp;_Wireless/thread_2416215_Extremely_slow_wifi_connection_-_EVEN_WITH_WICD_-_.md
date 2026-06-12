---
title: "Extremely slow wifi connection - EVEN WITH WICD - using realtek usb adapter."
date: 2019-04-07
forum: Networking &amp; Wireless
---

### Post by kostard on 2019-04-07
Hi.
I'm new in Ubuntu, so maybe I don't see some obvious solutions, but I'm already 3 days trying to fix it... Once I have even reinstalled the ubuntu because of some problems (removed network-manager, wifi driver and some other stuff trying to fix the problem, so the ubuntu was fully disconnected from the web ...)... This time I know more how to work with this, but I can't fix the problem yet.... I have installed the wicd again, but got no effect + the connection was being interrupted all the time, so I removed it. So I just don't know what to do next... I want to use ubuntu for programming, but with this connection I can't do anything serious... So please help. I'll post all the outputs you want...
I have installed Ubuntu 18.10 as dual-boot with my Windows 10 (where I get good wifi speed).
I yes, previous time (before reinstalling) when I installed wicd, I got more than 20x increase in wifi speed and that was awesome, but after some time I got same speed and was not finding any way to get that speed again.... I'm totally stuck in this and don't know what to do...
Here is the output of lshw -C network.
```
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: f8:32:e4:a2:97:76
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:4
       logical name: wlxe84e06388a31
       serial: e8:4e:06:38:8a:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.18.0-17-generic firmware=N/A ip=192.168.31.154 link=yes multicast=yes wireless=IEEE 802.11

```

---

### Post by chili555 on 2019-04-08
Please run and post:```
lsusb
lsmod | grep rtl8
```Thanks.

---

### Post by kostard on 2019-04-10
Here are outputs...
```
~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 003: ID 0c45:7603 Microdia 
Bus 003 Device 002: ID 0000:3821  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
~$ lsmod | grep rtl8
rtl8xxxu              122880  0
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        57344  1 rtl8192cu
rtlwifi                90112  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211              794624  4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu


```

---

### Post by kostard on 2019-04-10
And yes.... I have found a temporary solution, which gives me ~40x increase in the wifi internet speed for ~4 days each time...
Here are the steps...
So first of all, I have installed 'fixed' RTL8192 driver from [https://github.com/myersg86/rtl8192cu-fixes](https://github.com/myersg86/rtl8192cu-fixes), but it wasn't working - I was not able to connect with wifi - was getting 'bad password' with wicd. But after changing back to the [COLOR=#000000][FONT=&amp]rtl8xxxu and removing blacklist file of the 'fixed' driver from modprobe.d I was getting much better network... But after some restarts, I have to repeat all these steps... 
So here are steps to get the speed increase.
[/FONT][/COLOR]1 - sudo su
2 - cd Downloads
3 - git clone [https://github.com/myersg86/rtl8192cu-fixes](https://github.com/myersg86/rtl8192cu-fixes)
4 - rmmod rtl8xxxu
5 - rmmod rtl8192cu
6 - cp Downloads/rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
7 - modprobe 8192cu
[Maybe you have to run wicd here, more testing needed for this]
8 - rmmod 8192cu
9 - rm /etc/modprobe.d/blacklist-native-rtl8192.conf
10 - modprobe rtl8xxxu
[connect with wicd]
Done! I get ~40x speed increase.

---

### Post by chili555 on 2019-04-10
> **kostard said:**
> And yes.... I have found a temporary solution, which gives me ~40x increase in the wifi internet speed for ~4 days each time...
Here are the steps...
So first of all, I have installed 'fixed' RTL8192 driver from [https://github.com/myersg86/rtl8192cu-fixes](https://github.com/myersg86/rtl8192cu-fixes), but it wasn't working - I was not able to connect with wifi - was getting 'bad password' with wicd. But after changing back to the [COLOR=#000000][FONT=&amp]rtl8xxxu and removing blacklist file of the 'fixed' driver from modprobe.d I was getting much better network... But after some restarts, I have to repeat all these steps... 
So here are steps to get the speed increase.
[/FONT][/COLOR]1 - sudo su
2 - cd Downloads
3 - git clone [https://github.com/myersg86/rtl8192cu-fixes](https://github.com/myersg86/rtl8192cu-fixes)
4 - rmmod rtl8xxxu
5 - rmmod rtl8192cu
6 - cp Downloads/rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
7 - modprobe 8192cu
[Maybe you have to run wicd here, more testing needed for this]
8 - rmmod 8192cu
9 - rm /etc/modprobe.d/blacklist-native-rtl8192.conf
10 - modprobe rtl8xxxu
[connect with wicd]
Done! I get ~40x speed increase.Wow! That's a lot of work! I am wondering why you downloaded and built a github version of 8192cu just so you can remove it with rmmod.

I suggest that you simply blacklist it and let the correct driver rtl8xxxu do its usual great job.

```
sudo -i
echo "blacklist 8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```

Done.

PS- You don't need Wicd at all. You simply need the correct driver and not two possibly conflicting drivers.

---

### Post by kostard on 2019-04-11
Hmm... As I see I didn't write enough clear... Look I have installed the other driver because I WAS GETTING slow connection starting from ubuntu installation (I have installed it twice and was getting the same problem)... I tried using wicd, but it didn't give any effect... So I digged deeper and found this solution... Yes the 8192cu driver is not working as expected, but it is giving me a was to temporarily solve the problem...
You know I just thought, that maybe the [COLOR=#000000]*rtl8192cu *[/COLOR]driver is giving some problems, so next time I get slow internet connection I'll try just to stop that... And maybe that will work because you are right, I can't understand what effect can have just turning on and off the driver...

---

### Post by chili555 on 2019-04-11
Your writing is very clear to me. You built a different, possibly better, possibly not 8192cu driver. Having done do, you blacklisted the original rtl8192cu so you could use the 8192cu driver. Then you UNloaded it with rmmod. That left only rtl8xxxu, the driver that most of us think is the correct driver.> I can't understand what effect can have just turning on and off the driver...The effect it has is that without your action, either rmmod or blacklist, two conflicting drivers load. Unloading the incorrect driver allows the correct driver, rtl8xxxu, to work properly.>  And maybe that will work because you are rightI've only worked on 15-20 similar cases; I suspect I'm right.

For example: [https://askubuntu.com/questions/947648/edimax-usb-wifi-ew-7811un-not-connecting-on-17-04/947652#947652](https://askubuntu.com/questions/947648/edimax-usb-wifi-ew-7811un-not-connecting-on-17-04/947652#947652)

---

### Post by kostard on 2019-04-11
OK, thank you for your response! I'll check and post information about my experience as I get the problem!

---

