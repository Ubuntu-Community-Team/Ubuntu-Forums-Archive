---
title: "USB Modem Connection Ubuntu 12.04"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by florisrei on 2013-09-24
Hi I use vodafone K3805-Z 3G modem in Windows and it work fine.  when I try the same modem in Ubuntu it seems to connect but I cannot get e-mails or surf the net.

Please see attached files for more information.

Please help.

Reimerd

---

### Post by varunendra on 2013-09-25
While running the configuration wizard for your connection, did you choose correct plan?
Have you confirmed the APN is correct?
Have you tried changing the network "Type" from "Any" to a fixed one (whatever signal you normally get)?

In the "IPv4" settings of your connection, you may try changing the Method from "Automatic (PPP)" to "Automatic (PPP) address only" to change your DNS from the automatically assigned one to "8.8.8.8, 8.8.4.4" - which are Google's open DNS servers.

For convenience of others, I'm posting **your above attached configuration details** in a more appropriate manner here, hopefully, it will get you quicker help -

**Contents of USB Modem.doc :**
```
reimerd@reimerd-Dell-System-XPS-L502X:~$ sudo lshw -c network 
[sudo] password for reimerd: 
  *-network DISABLED      
       description: Wireless interface 
       product: Centrino Wireless-N 1030 [Rainbow Peak] 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 34 
       serial: bc:77:37:4b:32:aa 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-53-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:52 memory:f1b00000-f1b01fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 06 
       serial: 14:fe:b5:ab:ca:fc 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:50 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff 
  *-network 
       description: Ethernet interface 
       physical id: 2 
       logical name: usb0 
       serial: 02:57:9a:d9:51:b4 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=121.72.188.199 link=yes multicast=yes 


reimerd@reimerd-Dell-System-XPS-L502X:~$ sudo lspci -nm | grep 0200 
06:00.0 "0200" "10ec" "8168" -r06 "1028" "050e" 


reimerd@reimerd-Dell-System-XPS-L502X:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 usb0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0 

eimerd@reimerd-Dell-System-XPS-L502X:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 14:fe:b5:ab:ca:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:50 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2313 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2313 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:173270 (173.2 KB)  TX bytes:173270 (173.2 KB) 

usb0      Link encap:Ethernet  HWaddr 02:57:9a:d9:51:b4  
          inet addr:121.72.188.199  Bcast:121.72.188.199  Mask:255.255.255.255 
          inet6 addr: fe80::57:9aff:fed9:51b4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2414 (2.4 KB)  TX bytes:58815 (58.8 KB) 
```
**Image (cropped) from Ubuntu USB Modem_1.odt :**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246497[/IMG]

**Image (cropped) from Ubuntu USB Modem_2.odt :**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246498[/IMG]

---

### Post by florisrei on 2013-09-26
Hi I tried all of that but still no surfing - any other ideas?

Regards

---

### Post by varunendra on 2013-09-26
Not really. If all the settings are same as the working ones in windows, I can't think why they won't work in Ubuntu. A few more things -

* Have you asked your service provider's customer care? Tell them it shows connected, but can't get a gateway IP (it's 0.0.0.0, which is weird)

* Under the "PPP settings" tab (the first screenshot), there is a button "Configure Methods...". If you click it, there are several checkboxes and a comment -
> In most cases, the ppp servers will support all authentication methods. If connections fail, try disabling support for some methods
By default all methods are enabled. Try doing what the comment above suggests. That is, try only one at a time, or disabling one or two at a time. Of course this may take many tries on different combinations. I would start with only PAP/CHAP/MSCHAP (or only one of them).

* Perhaps this one would be a far cry (if the problem is at authentication level, this one makes no sense at all) - When you are connected in Windows, please run the following command (in cmd prompt) -
```
ipconfig
```
..and post back the whole output. We are interested in the gateway IP only. Once we have it, we can try to force it in Ubuntu.

Given the quality of support in customer care numbers, I'm not very hopeful with that one, but maybe they can give some useful info we can use for troubleshooting.

---

### Post by florisrei on 2013-09-26
Hi tried a few permutations no surfing or e-mail

windows IPCONFIG

```

Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Reimerd>ipconfig

Windows IP Configuration


Mobile Broadband adapter Mobile Broadband Connection 3:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 121.74.190.6
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 121.74.190.7

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Orcon

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{43C4D339-5A8A-472A-9857-4B51A844B54E}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2002:794a:be06::794a:be06
   Default Gateway . . . . . . . . . : 2002:c058:6301::624

Tunnel adapter Local Area Connection* 11:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:953c:2018:6e2:86b5:41f9
   Link-local IPv6 Address . . . . . : fe80::2018:6e2:86b5:41f9%21
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.Orcon:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{C9753F4A-3C34-4E87-ADB3-DAF162A1AF91}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{F74C1206-59C6-4B48-9167-9372AF257853}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{F9281080-71FF-49F3-B89A-E2172FAF88AB}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :


Tunnel adapter isatap.{CA412DED-247D-4DA9-B388-83EE8DE9479F}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

C:\Users\Reimerd>

```

Second time
```

C:\Users\Reimerd>


Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Reimerd>ipconfig

Windows IP Configuration


Mobile Broadband adapter Mobile Broadband Connection 3:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 121.74.138.170
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 121.74.138.171

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Orcon

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{43C4D339-5A8A-472A-9857-4B51A844B54E}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2002:794a:8aaa::794a:8aaa
   Default Gateway . . . . . . . . . : 2002:c058:6301::624

Tunnel adapter Local Area Connection* 11:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::c07:3362:86b5:7555%21
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.Orcon:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{C9753F4A-3C34-4E87-ADB3-DAF162A1AF91}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{F74C1206-59C6-4B48-9167-9372AF257853}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{F9281080-71FF-49F3-B89A-E2172FAF88AB}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{CA412DED-247D-4DA9-B388-83EE8DE9479F}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

C:\Users\Reimerd>


```

---

### Post by varunendra on 2013-09-26
A far cry indeed, as suspected -
> **florisrei said:**
> ```

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : **121.74.190.6**
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : [COLOR="#FF0000"]121.74.190.7[/COLOR]
....
....
   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : **121.74.138.170**
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : [COLOR="#FF0000"]121.74.138.171[/COLOR]

```

The screenshot in Ubuntu and these two attempts in Windows have all different IPs, which is common in such services. Accordingly, the gateway is changing as well and there seems to be no fixed pattern for either the IP or the gateway. So almost no hope there. The best you can do with these results is to keep a list of IPs on different pattern and respective gateways.

For example, if you get an IP of the pattern "**121.74.190.*<any number>***", the respective gateway "**121.74.190.7**" should always work (provided a firewall is not blocking the connection at the ISPs end).
As such, you can try in Ubuntu (in the above example case) -
```
sudo route del default gw
sudo route add default gw 121.74.190.7
```
Of course this is very tedious (keeping a list of different patterns and waiting to get a matching one), impractical and above all - not guaranteed to work. This shouldn't be needed in the first place.

I can think of only two more things that you can change in your system -

**1)** The driver, if it is not the default one. To make sure of that, please post the outputs of -
```
lsusb
nm-tool
```

**2)** Try setting the IPv6 'Method' to "Ignore" in Network Manager settings for the connection.

Since you are getting an IP, it indicates the initial connection succeeds (your connection is 'registered'), but not getting a gateway IP indicates a problem most probably (but not necessarily) at ISP's side.

Have you talked to the customer care yet?

---

### Post by florisrei on 2013-10-01
Hi,

This is a mobile broadband from a different network provider and is working fine - I can connect and surf.

Can you find anything between the two that will lead us anywhere?

```

   lshw -c network  reimerd@reimerd-Dell-System-XPS-L502X:~$ sudo lshw -c network 
 [sudo] password for reimerd:  
   *-network DISABLED       
        description: Wireless interface 
        product: Centrino Wireless-N 1030 [Rainbow Peak] 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: wlan0 
        version: 34 
        serial: bc:77:37:4b:32:aa 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-53-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:52 memory:f1b00000-f1b01fff 
   *-network 
        description: Ethernet interface 
        product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:06:00.0 
        logical name: eth0 
        version: 06 
        serial: 14:fe:b5:ab:ca:fc 
        size: 10Mbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
        resources: irq:50 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff



```


```

   eimerd@reimerd-Dell-System-XPS-L502X:~$ sudo lspci -nm | grep 0200  
 06:00.0 "0200" "10ec" "8168" -r06 "1028" "050e" 



```

```

   reimerd@reimerd-Dell-System-XPS-L502X:~$ route -n 
 Kernel IP routing table 
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
 0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0 
 10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0 
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0 



```


```

   reimerd@reimerd-Dell-System-XPS-L502X:~$ ifconfig 
 eth0      Link encap:Ethernet  HWaddr 14:fe:b5:ab:ca:fc   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:50 Base address:0x4000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:753 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:753 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:104637 (104.6 KB)  TX bytes:104637 (104.6 KB) 
  
 ppp0      Link encap:Point-to-Point Protocol   
           inet addr:100.101.160.18  P-t-P:10.64.64.64  Mask:255.255.255.255 
           UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1 
           RX packets:6376 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4785 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:3  
           RX bytes:5397309 (5.3 MB)  TX bytes:703749 (703.7 KB) 



```


```

   reimerd@reimerd-Dell-System-XPS-L502X:~$ lsusb 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc.  
 Bus 002 Device 003: ID 8086:0189 Intel Corp.  
 Bus 002 Device 007: ID 12d1:1c05 Huawei Technologies Co., Ltd.  



```

```

   reimerd@reimerd-Dell-System-XPS-L502X:~$ nm-tool 
  
 NetworkManager Tool 
  
 State: connected (global) 
  
 - Device: ttyUSB0  [2 Degrees] ------------------------------------------------- 
   Type:              Mobile Broadband (GSM) 
   Driver:            option1 
   State:             connected 
   Default:           yes 
  
   Capabilities: 
  
   IPv4 Settings: 
     Address:         100.101.160.18 
     Prefix:          32 (255.255.255.255) 
     Gateway:         10.64.64.64 
  
     DNS:             118.148.1.10 
     DNS:             118.148.1.20 
  
  
 - Device: eth0 ----------------------------------------------------------------- 
   Type:              Wired 
   Driver:            r8169 
   State:             unavailable 
   Default:           no 
   HW Address:        14:FE:B5:AB:CA:FC 
  
   Capabilities: 
     Carrier Detect:  yes 
  
   Wired Properties 
     Carrier:         off 
  
  
 - Device: wlan0 ---------------------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            iwlwifi 
   State:             unavailable 
   Default:           no 
   HW Address:        BC:77:37:4B:32:AA 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  



```

[ATTACH=CONFIG]246646[/ATTACH]

[ATTACH=CONFIG]246646[/ATTACH]

Reimerd

---

### Post by varunendra on 2013-10-02
> **florisrei said:**
> Can you find anything between the two that will lead us anywhere?

Is it the same USB modem with a different SIM card? If yes, then clearly it was a problem with either the basic configuration (apn, dial no, network type, or authentication method), or something at your earlier ISP's side.

If it is a different USB modem as well, it might help to look at lsusb and nm-tool commands with that one plugged in (and connected as much as if it can).

Just FYI, the only helpful outputs are **lsusb** and **nm-tool**. Most of the rest of commands you have been using are either useless or the useful part of their output is included in these two. If something significant came up, we may ask you for more outputs as required.

---

