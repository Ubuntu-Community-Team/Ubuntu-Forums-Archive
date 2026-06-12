---
title: "BCM4313 wireless chip driver"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by lion_heart on 2013-11-24
hey guys:
    i still can't believe what happend!
    The other PCs or devices connected to WIFI will lose their connection once my PC connected to the same WIFI AP.
    I don't know why.
    But when i using WIN7 this wouldn't happend!(I have double OS, UBUNTU & WIN7)

could some one help me? Thanks!

---

### Post by Bucky Ball on 2013-11-24
Welcome. Please tell us the release you are using and provide the output of these two commands from a terminal:

```
iwconfig
sudo lshw -C network
```

Also, let us know what you have done to alter network setup on your local machine, if anything, what you have tried to fix it, if anything, and a precise idea of the setup you have with the network. Thanks.

---

### Post by lion_heart on 2013-11-24
Thanks for your reply!
13.04 & 12.04(64) has the same problem.

bloceanc@bloceanc-ThinkPad:~/Downloads$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"happy"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:E6:E4:6E:8A:84   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

bloceanc@bloceanc-ThinkPad:~/Downloads$ sudo lshw -C network
[sudo] password for bloceanc: 
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 08:ed:b9:e2:1b:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:cdd00000-cdd03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:30:8f:b4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:cc404000-cc404fff memory:cc400000-cc403fff
bloceanc@bloceanc-ThinkPad:~/Downloads$ 
bloceanc@bloceanc-ThinkPad:~/Downloads$ 
bloceanc@bloceanc-ThinkPad:~/Downloads$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   14:e6:e4:6e:8a:84   C                     eth1
bloceanc@bloceanc-ThinkPad:~/Downloads$ ^C
bloceanc@bloceanc-ThinkPad:~/Downloads$ 

first i use 13.04 and download boot-repair, i found the problem.
then i changed to 12.04(reinstall linux)! it has the same problem.

nothing else has been done.

thank again!

---

### Post by Bucky Ball on 2013-11-24
So you are now on 12.04? Let's stick to the one release to avoid confusion. ;)

I did notice one thing, although don't know if this would have anything to do with it.

logical name: eth1

The logical name for the wireless generally starts with 'wlan' not 'eth', as in 'logical name: wlan1' (or 0).

---

### Post by lion_heart on 2013-11-24
yes, i'm using 12.04 now.
generally logical name starts with "wlan", but it changed to 'eth' after one reboot.
It did nothing to do with my own connection. Ubuntu can access net but other PCs becoming slowly, very slowly with net.

---

### Post by Bucky Ball on 2013-11-24
Well, that is really peculiar. Is this noticable as soon as you switch on???

Also, was it always like this or was it fine when it was wlan?

---

### Post by lion_heart on 2013-11-24
Well, that is really peculiar. Is this noticable as soon as you switch on???    No, it needs some seconds. after a while, some seconds. the accessing of other device with WIFI will become very slowly.Also, was it always like this or was it fine when it was wlan?    It always like this even installing ubuntu with under WIFI connected!

---

### Post by lion_heart on 2013-11-24
I thougt it maybe can't work fun with my TP-Link(a home gateway router).but it works fun with my WIN7 in the same laptop!

---

### Post by Bucky Ball on 2013-11-24
So, you're saying the other machines disconnect or slow down, as you mentioned both? Is the speed in Ubuntu normal or does that slow and the other machines disconnect/slow down?

When you are booted into Ubuntu please have a look at the network activity in System Monitor. Without Firefox or any other net activity, but connected to the net, does it show any activity? Also, does the same disconnect/slowness happen when you connect with a cable?

---

### Post by lion_heart on 2013-11-24
I tried without data transition, just connecting.it is no help.
But, i did not test with cable, i will test it sometimes.
I found someone had the same problem:   [http://askubuntu.com/questions/357118/wifi-on-one-laptop-makes-connection-on-other-devices-very-slow](http://askubuntu.com/questions/357118/wifi-on-one-laptop-makes-connection-on-other-devices-very-slow)

---

### Post by lion_heart on 2013-11-24
[http://askubuntu.com/questions/281035/laptop-blocking-other-computers-on-home-wifi-routers](http://askubuntu.com/questions/281035/laptop-blocking-other-computers-on-home-wifi-routers)

Another one.


I found some one solved this by using brcmsmac.
But i can't find wifi ap Using this driver.

Signal too weak to connecting even close the router.

---

### Post by chili555 on 2013-11-25
You evidently didn't find the answer yet. Please check here: [http://askubuntu.com/questions/360447/why-my-roommates-connection-to-the-internet-is-lost-when-im-connected-to-our/360586#360586](http://askubuntu.com/questions/360447/why-my-roommates-connection-to-the-internet-is-lost-when-im-connected-to-our/360586#360586)

Please note that in all these cases, the device is the same; 14e4:4727, and the driver is the STA driver: driverversion=6.20.155.1. My answer suggests that the earlier version 5.100.82.112 works better. Will you please test and report?

---

### Post by lion_heart on 2013-11-25
Yes, it works fun till now.
Thanks very much!

---

### Post by chili555 on 2013-11-25
> **lion_heart said:**
> Yes, it works fun till now.
Thanks very much!Awesome! Glad to hear it's working.

---

### Post by Bucky Ball on 2013-11-25
chilli555 to the rescue once again! Glad to hear it is working for you. :)

Please mark thread as solved by following the instructions in my signature.

---

