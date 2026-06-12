---
title: "Wired Connection on Ubuntu 12.04 stopped working after an update!"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by book_life on 2013-12-14
Here is the thing! am on day 5 of no wired internet connection. I have spent the last 4 days searching through every forum and Q&A sites, until i finally decided to post this, so I have done my homework. Before I take my laptop to maintenance shop for hardware failures i want to check with you guys first.


**Problem Description:**
  Like the question says my wired connection stopped working suddenly after an update. I am using ubuntu 12.04 LTS. Network Manager says **Wired Networks disconnected**. Wireless is working perfectly. And also it doesn't work on Windows 7 too, it says cable unplugged. I have tried the cable on other computer and it works perfectly.


**nm-tool** *output*:


    ```
NetworkManager Tool
    
    State: connected (global)
    
    - Device: wlan0  [Connectify-me] -----------------------------------------------
      Type:              802.11 WiFi
      Driver:            iwlwifi
      State:             connected
      Default:           yes
      HW Address:        9C:4E:36:29:F7:D4
    
      Capabilities:
        Speed:           58 Mb/s
    
      Wireless Properties
        WEP Encryption:  yes
        WPA Encryption:  yes
        WPA2 Encryption: yes
    
      Wireless Access Points (* = current AP)
        TP-LINK_8AB114:  Infra, A0:F3:C1:8A:B1:14, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2
        ZTE_HG_0:        Infra, 00:1D:0F:BF:BE:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 47
        ZTE_HG_0:        Infra, 00:21:27:C1:19D:9, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
        *Connectify-me:  Infra, E8:39:DF:3E:AF:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA2
    
      IPv4 Settings:
        Address:         192.168.241.104
        Prefix:          24 (255.255.255.0)
        Gateway:         192.168.241.1
    
        DNS:             192.168.241.1
    
    
    - Device: eth0 -----------------------------------------------------------------
      Type:              Wired
      Driver:            atl1c
      State:             unavailable
      Default:           no
      HW Address:        00:1E:DE:F7:A6:C9
    
      Capabilities:
        Carrier Detect:  yes
    
      Wired Properties
        Carrier:         off

```

**sudo lshw -C network ***output:*


      ```
*-network               
           description: Ethernet interface
           product: AR8152 v2.0 Fast Ethernet
           vendor: Qualcomm Atheros
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eth0
           version: c1
           serial: 00:1e:de:f7:a6:c9
           capacity: 100Mbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
           resources: irq:48 memory:f7e00000-f7e3ffff ioport:e000(size=128)
      *-network
           description: Wireless interface
           product: Centrino Wireless-N 2200
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: wlan0
           version: c4
           serial: 9c:4e:36:29:f7:d4
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-57-generic firmware=18.168.6.1 ip=192.168.241.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
    resources: irq:46 memory:f7d00000-f7d01fff
```


**ifconfig eth0 ***output:*

    ```
eth0      Link encap:Ethernet  HWaddr 00:1e:de:f7:a6:c9  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
              Interrupt:48 

```

So there you have it guys! Let me know if you need additional information. So Please help me!!!

---

### Post by book_life on 2013-12-14
waiting patiently!

---

### Post by asus-user on 2013-12-14
> **book_life said:**
> 
**Problem Description:**
  Like the question says my wired connection stopped working suddenly after an update. I am using ubuntu 12.04 LTS. Network Manager says **Wired Networks disconnected**. Wireless is working perfectly. And also it doesn't work on Windows 7 too, it says cable unplugged. I have tried the cable on other computer and it works perfectly.


Usually when this happens it means that it doesn't have anything to do with the your OS or updates. Check your bios settings and better restore them to default, if it didn't work, it's probably a hardware problem.

---

### Post by book_life on 2013-12-14
But I didn't touch the bios settings. And I don't think it is a hardware problem. Windows 7 says the device is working properly. If you have any suggestions?

---

### Post by asus-user on 2013-12-14
> **book_life said:**
> Here is the thing! am on day 5 of no wired internet connection. I have spent the last 4 days searching through every forum and Q&A sites, until i finally decided to post this, so I have done my homework. Before I take my laptop to maintenance shop for hardware failures i want to check with you guys first.   **Problem Description:**   Like the question says my wired connection stopped working suddenly after an update. I am using ubuntu 12.04 LTS. Network Manager says **Wired Networks disconnected**. Wireless is working perfectly. And also it doesn't work on Windows 7 too, it says cable unplugged. I have tried the cable on other computer and it works perfectly.   **nm-tool** *output*:       ```
NetworkManager Tool          State: connected (global)          - Device: wlan0  [Connectify-me] -----------------------------------------------       Type:              802.11 WiFi       Driver:            iwlwifi       State:             connected       Default:           yes       HW Address:        9C:4E:36:29:F7:D4            Capabilities:         Speed:           58 Mb/s            Wireless Properties         WEP Encryption:  yes         WPA Encryption:  yes         WPA2 Encryption: yes            Wireless Access Points (* = current AP)         TP-LINK_8AB114:  Infra, A0:F3:C1:8A:B1:14, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2         ZTE_HG_0:        Infra, 00:1D:0F:BF:BE:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 47         ZTE_HG_0:        Infra, 00:21:27:C1:19D:9, Freq 2437 MHz, Rate 54 Mb/s, Strength 39         *Connectify-me:  Infra, E8:39:DF:3E:AF:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA2            IPv4 Settings:         Address:         192.168.241.104         Prefix:          24 (255.255.255.0)         Gateway:         192.168.241.1              DNS:             192.168.241.1               - Device: eth0 -----------------------------------------------------------------       Type:              Wired       Driver:            atl1c       State:             unavailable       Default:           no       HW Address:        00:1E:DE:F7:A6:C9            Capabilities:         Carrier Detect:  yes            Wired Properties         Carrier:         off 
```  **sudo lshw -C network ***output:*         ```
*-network                           description: Ethernet interface            product: AR8152 v2.0 Fast Ethernet            vendor: Qualcomm Atheros            physical id: 0            bus info: pci@0000:01:00.0            logical name: eth0            version: c1            serial: 00:1e:de:f7:a6:c9            capacity: 100Mbit/s            width: 64 bits            clock: 33MHz            capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation            configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair            resources: irq:48 memory:f7e00000-f7e3ffff ioport:e000(size=128)       *-network            description: Wireless interface            product: Centrino Wireless-N 2200            vendor: Intel Corporation            physical id: 0            bus info: pci@0000:02:00.0            logical name: wlan0            version: c4            serial: 9c:4e:36:29:f7:d4            width: 64 bits            clock: 33MHz            capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless            configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-57-generic firmware=18.168.6.1 ip=192.168.241.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn     resources: irq:46 memory:f7d00000-f7d01fff
```   **ifconfig eth0 ***output:*      ```
eth0      Link encap:Ethernet  HWaddr 00:1e:de:f7:a6:c9                 UP BROADCAST MULTICAST  MTU:1500  Metric:1               RX packets:0 errors:0 dropped:0 overruns:0 frame:0               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0               collisions:0 txqueuelen:1000                RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)               Interrupt:48  
```  So there you have it guys! Let me know if you need additional information. So Please help me!!!  Strangely enough, I got the exact same commands output where my wired connection works just fine.

---

