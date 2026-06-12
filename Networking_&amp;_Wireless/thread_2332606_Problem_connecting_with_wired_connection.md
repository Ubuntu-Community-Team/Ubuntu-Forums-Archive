---
title: "Problem connecting with wired connection"
date: 2016-08-02
forum: Networking &amp; Wireless
---

### Post by viet.le175 on 2016-08-02
Once again here's another problem my linux decided to break down.


My wifi is working but when it comes to being wired in...not so much.


I tried a lot of solutions but none worked...


It was working this morning and now it is not.


Heres a list of stuff. Why am I not connecting to my wired connection?


ifconfig


```
    eth0      Link encap:Ethernet  HWaddr 80:fa:5b:2b:96:84  
              inet6 addr: fe80::82fa:5bff:fe2b:9684/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:73 errors:0 dropped:0 overruns:0 frame:0
              TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:6555 (6.5 KB)  TX bytes:25744 (25.7 KB)
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:833 errors:0 dropped:0 overruns:0 frame:0
              TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:79645 (79.6 KB)  TX bytes:79645 (79.6 KB)
    
    wlan0     Link encap:Ethernet  HWaddr a4:34:d9:64:d9:a8  
              inet addr:192.168.2.36  Bcast:192.168.3.255  Mask:255.255.252.0
              inet6 addr: fe80::a634:d9ff:fe64:d9a8/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1816 errors:0 dropped:0 overruns:0 frame:0
              TX packets:1529 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:1526261 (1.5 MB)  TX bytes:293164 (293.1 KB)

```

/etc/NetworkManager/NetworkManager.conf


```
[main]


    plugins=ifupdown,keyfile,ofono
    dns=dnsmasq
    
    [ifupdown]
    managed=true

```

/etc/network/interfaces

```
    # interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback

```



nm-tool


```
    - Device: wlan0  [staybridge] --------------------------------------------------
      Type:              802.11 WiFi
      Driver:            iwlwifi
      State:             connected
      Default:           yes
      HW Address:        A4:34:D9:64:D9:A8
    
      Capabilities:
        Speed:           1 Mb/s
    
      Wireless Properties
        WEP Encryption:  yes
        WPA Encryption:  yes
        WPA2 Encryption: yes
    
      Wireless Access Points (* = current AP)
        PC2:             Infra, C8:D7:19:48:70:C0, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
        staybridge:      Infra, 00:02:6F:CB:F5:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 72
        staybridge:      Infra, 00:02:6F:BF:2C:70, Freq 2417 MHz, Rate 54 Mb/s, Strength 60
        staybridge:      Infra, 00:02:6F:BF:2C:84, Freq 2442 MHz, Rate 54 Mb/s, Strength 54
        CableWiFi:       Infra, 50:1C:BF:49:7B:2C, Freq 5805 MHz, Rate 54 Mb/s, Strength 35
        staybridge:      Infra, 00:02:6F:B7:31:F8, Freq 2427 MHz, Rate 54 Mb/s, Strength 40
        staybridge:      Infra, 00:02:6F:B7:32:00, Freq 2447 MHz, Rate 54 Mb/s, Strength 35
        EnGeniusBF2C78:  Infra, 00:02:6F:BF:2C:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 56
        PC:              Infra, C4:3D:C7:8E:82:88, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA2
        PC2:             Infra, C8:D7:19:48:70:C1, Freq 5180 MHz, Rate 54 Mb/s, Strength 35 WPA2
        staybridge:      Infra, 00:02:6F:E9:DB:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 62
        staybridge:      Infra, 00:02:6F:BF:2C:60, Freq 2432 MHz, Rate 54 Mb/s, Strength 49
        xfinitywifi:     Infra, 50:1C:BF:49:7B:2E, Freq 5805 MHz, Rate 54 Mb/s, Strength 35
        staybridge:      Infra, 00:02:6F:B7:32:04, Freq 2447 MHz, Rate 54 Mb/s, Strength 35
        CableWiFi:       Infra, 18:9C:5D:8E:9C:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
        *staybridge:     Infra, 00:02:6F:E9:DB:B0, Freq 2462 MHz, Rate 54 Mb/s, Strength 69
        VAIO-UD56UU:     Infra, D0:AE:EC:A9:A4:8A, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
        optimumwifi:     Infra, 50:1C:BF:49:7B:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
        optimumwifi:     Infra, F0:29:29:C3:4A:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
        TWCWiFi:         Infra, 50:1C:BF:49:7B:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
        xfinitywifi:     Infra, D0:C7:89:3B:B8:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    
      IPv4 Settings:
        Address:         192.168.2.36
        Prefix:          22 (255.255.252.0)
        Gateway:         192.168.3.251
    
        DNS:             8.8.8.8
        DNS:             8.8.4.4
    
    
    - Device: eth0 -----------------------------------------------------------------
      Type:              Wired
      Driver:            r8169
      State:             disconnected
      Default:           no
      HW Address:        80:FA:5B:2B:96:84
    
      Capabilities:
        Carrier Detect:  yes
        Speed:           1000 Mb/s
    
      Wired Properties
        Carrier:         on

```

sudo lshw -C network


```
      *-network               
           description: Ethernet interface
           product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0.1
           bus info: pci@0000:01:00.1
           logical name: eth0
           version: 12
           serial: 80:fa:5b:2b:96:84
           size: 1Gbit/s
           capacity: 1Gbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
           resources: irq:126 ioport:e000(size=256) memory:df214000-df214fff memory:df210000-df213fff
      *-network
           description: Wireless interface
           product: Wireless 8260
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: wlan0
           version: 3a
           serial: a4:34:d9:64:d9:a8
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-42-generic firmware=25.30.13.0 ip=192.168.2.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
           resources: irq:129 memory:df100000-df101fff

```

UPDATE


I tried adding these lines of codes inside /etc/network/interfaces and no changes
```


    auto eth0
    iface eth0 inet dhcp

```

---

### Post by howefield on 2016-08-02
Duplicate thread closed.

---

