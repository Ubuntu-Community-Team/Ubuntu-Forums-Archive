---
title: "No wifi-adapter found"
date: 2020-05-15
forum: Networking &amp; Wireless
---

### Post by reloadedrule on 2020-05-15
Intel Corporation Centrino Wireless-N 1030 is my wifi hardware. How can i install the driver for this. It shows no wifi-adapter found in Wifi-Settings. # New to Linux. Help

---

### Post by grahammechanical on 2020-05-15
We are going to need more information before we can help you. What version of Ubuntu are you using? Are you using one of the flavors of Ubuntu? It makes a difference regarding the directions we may need to give. Try running the following commands and post the output in quote tags.

```
rfkill list
```

This command should reply

> Soft blocked: no
Hard blocked: no

Soft blocked = yes means you do not have a driver. Hard blocked = yes means the WiFi adapter is switched off. 

```
lshw -C network
```

```
iwconfig
```

Regards.

---

### Post by reloadedrule on 2020-05-15
How do i install driver. Please Help what can i do.. It dell inspiron n4110 my old laptop.
my version is ubuntu 18.04 64-bit LTS

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
```

```
sudo lshw -C network
[sudo] password for dell: 
  *-network DISABLED        
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 34
       serial: bc:77:37:68:3b:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-53-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:36 memory:e0600000-e0601fff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 05
       serial: 14:fe:b5:ad:43:0f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.100.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:e0404000-e0404fff memory:e0400000-e0403fff
```




```
iwconfig
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by slickymaster on 2020-05-15
*Thread moved to **Networking & Wireless**.*

---

### Post by grahammechanical on 2020-05-15
Do not take me for an expert but my guess is that your WiFi adapter is switched of or disconnected or disabled (perhaps in BIOS/UEFI settings utility). Or your router is switched off.

According to lshw

> ```
broadcast=yes driver=iwlwifi driverversion=5.3.0-53-generic
```

So there is a driver but according to rfkill it is blocked in both software and hardware. Now look at what I see from iwconfig on my machine.

> ```
wlx0015af0e9be0  IEEE 802.11  ESSID:"PlusnetWireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:21:E5:81   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:498   Missed beacon:0
```

The ESSID would be the connection to the router. You should have a signal level and a Bit Rate and Tx-Power level. None of which you have.
It may be that you need to press a combination of function (fn) keys to switch the WiFi adapter on. I am blind guessing at possible causes that might lead to solutions.

Edit   It just now occurs to me that if you have Microsoft Windows and have disabled WiFi to save battery power that when Ubuntu loads the WiFi adapter is not switched back on. It has been a while since I studied WiFi problem in Ubuntu. And I am a lot older now. I forget things that I once knew.

Regards.

---

### Post by reloadedrule on 2020-05-16
My router is turned on . I don't have windows installed

---

