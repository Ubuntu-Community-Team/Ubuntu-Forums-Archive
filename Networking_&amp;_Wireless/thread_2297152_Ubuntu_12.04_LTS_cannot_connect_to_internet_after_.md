---
title: "Ubuntu 12.04 LTS cannot connect to internet after installation"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by sofia6 on 2015-10-01
Hello all!
I am new to Ubuntu and I have tried different things but nothing works for me. I installed Ubuntu 12.04 LTS 32-bit on my windows 8 64-bit desktop. When I boot to windows 8, the wireless works perfectly. However, the internet doesn't work whenever I boot to Ubuntu (I installed ubuntu without internet). 
When I type to the terminal: ```
sudo ifconfig
```

it gives me this: 

```
etho         Link encap:Ethernet  HWaddr 9c:b6:54:f8:af:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160752 (160.7 KB)  TX bytes:160752 (160.7 KB)
```

And when I type in this: ```
sudo lshw -C network
```

It gives:
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: 9c:b6:54:f8:af:44
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7110000-f711ffff

```

I have tried things on many other threads but nothing works for my case. Really don't know what to do now. Any suggestion would be greatly appreciated!

---

### Post by grahammechanical on 2015-10-01
It is my guess that the wireless/WiFi adapter is switched off.

It could be that WiFi is not enabled in Ubuntu. There should be a Networking icon in the top panel that has a drop down menu that will allow you to enable WiFi.

It could be that WiFi has been switched off in Windows. If this machine is a laptop and WiFi is switched off in Windows to save battery power then it does not get switched on when ubuntu loads. Laptops have a keyborad combination that switched the wireless adapter on and off.

You could try running these 2 commands

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

It sounds silly but I think we have to take a wireless adapter down before we can take it up, even if it is already down. No harm in trying anyway.

Regards.

---

### Post by sofia6 on 2015-10-01
It is a hp desktop. I saw the icon top right corner. And "Enable Networking" is checked. 
I typed in 
```
sudo ifconfig wlan0 down
```
It shows that:
```
wlan0: ERROR while getting interface flags: No such device
```

There must be something missing here. 
Thank you!

---

### Post by howefield on 2015-10-01
Thread moved to the "*Networking & Wireless*" forum.

---

