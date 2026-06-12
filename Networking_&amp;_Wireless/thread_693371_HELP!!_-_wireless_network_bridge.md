---
title: "HELP!! - wireless network bridge"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by lightmastertech on 2008-02-10
I have just switched from XP to Ubuntu Gutsy. On my previous XP install, I had my wireless card and my wired card bridged so i could get network on my Xbox 360. Now, in Ubuntu, I want to do the same thing, but I have tried several methods and after 5 hours of trying, I'm starting to get frustrated. If anyone could help me, it would be greatly appreciated.

Thanks in advance.

---

### Post by jan quark on 2008-02-12
please post the results of the following terminal commands

```
iwconfig
```
```

sudo iwlist scan
```

```
lspci
```

```
lshw -C network
```

---

### Post by Wisp2006 on 2008-02-12
Hy all,

I have a similar issue, the only difference is in Windows the WLAN was linked to wired as "Internet Connection Sharing". Should I post too the result of the same comands?

Thanks.

---

### Post by lightmastertech on 2008-02-12
> **Wisp2006 said:**
> Hy all,

I have a similar issue, the only difference is in Windows the WLAN was linked to wired as "Internet Connection Sharing". Should I post too the result of the same comands?

Thanks.

what you did in Windows is the just a different method than what I did and it achieves the same result. I suppose that you should post the from the commands listed above. When I get home, I will post my results to the commands.

---

### Post by lightmastertech on 2008-02-12
i ran the list of commands that you gave me and this is what i got


terminal commands

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"The Bailey's"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:56:9C:A9   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0







**sudo iwlist scan**

[sudo] password for lightmaster:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:56:9C:A9
                    ESSID:"The Bailey's"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-52 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002620319eb8






**lspci**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
01:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)









**lshw -C network**

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:e3:5a:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0d:61:04:e0:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes





i ran the last command using sudo:

**sudo lshw -C network**

  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1c:10:e3:5a:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0d:61:04:e0:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

---

