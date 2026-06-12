---
title: "Ethernet looks like connected but no internet"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by sridhar8 on 2016-04-06
I have ubuntu14.04 version on my laptop. All of a sudden internet went down and I don't know what exactly happening. So I tried deleting that connection and creating a new ethernet connection and now its completely gone. It is not even detecting a connection.

```
ifconfig:
eth0      Link encap:Ethernet  HWaddr 9c:b6:54:c5:fc:fc  
          inet6 addr: fe80::9eb6:54ff:fec5:fcfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1382695 (1.3 MB)  TX bytes:62192 (62.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:386059 (386.0 KB)  TX bytes:386059 (386.0 KB)


wlan0     Link encap:Ethernet  HWaddr 80:56:f2:3c:49:00  
          inet addr:10.84.62.217  Bcast:10.84.63.255  Mask:255.255.248.0
          inet6 addr: fe80::8256:f2ff:fe3c:4900/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7220333 (7.2 MB)  TX bytes:1623524 (1.6 MB)

iwconfig:
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"csu-eid"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:1E:25:AB:41   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:22   Missed beacon:0

nm-tool:
NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        9C:B6:54:C5:FC:FC


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on




- Device: wlan0  [csu-eid] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        80:56:F2:3C:49:00


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    range:           Infra, C0:C1:C0:E2:59:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    eng_labs:        Infra, 00:1A:1E:25:AB:44, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    mecsoff:         Infra, 64:66:B3:50:06:69, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    rangeq:          Infra, C8:B3:73:28:D8:4E, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    LYimac:          Infra, 88:63:DF:C6:0B:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Bob's Wi-Fi Network: Infra, 70:56:81:C9:91:AB, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    csu-guest:       Infra, 00:1A:1E:25:AB:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    Norm's Wi-Fi Network: Infra, 6C:70:9F:E4:EA:D2, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    eduroam:         Infra, 6C:F3:7F:F2:2E:00, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:46:FB:C2, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    SETUP:           Ad-Hoc, 66:2A:2F:53:7C:99, Freq 2462 MHz, Rate 11 Mb/s, Strength 34
    eduroam:         Infra, 00:1A:1E:28:67:22, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    csu-eid:         Infra, 18:64:72:46:FB:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    csu-guest:       Infra, 18:64:72:46:FB:C0, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    csu-guest:       Infra, 00:1A:1E:28:4F:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    eng_labs:        Infra, 00:1A:1E:28:4F:24, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    csu-guest:       Infra, 6C:F3:7F:F2:2E:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    *csu-eid:        Infra, 00:1A:1E:25:AB:41, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:46:C9:C2, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    csu-eid:         Infra, 00:1A:1E:28:67:21, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    csu-guest:       Infra, 00:1A:1E:28:67:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 100


  IPv4 Settings:
    Address:         10.84.62.217
    Prefix:          21 (255.255.248.0)
    Gateway:         10.84.56.1


    DNS:             129.82.103.91
    DNS:             129.82.103.93
```

```

lshw -C network:
  *-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 80:56:f2:3c:49:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-85-generic firmware=N/A ip=10.84.62.217 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:4000(size=256) memory:c2600000-c2603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 0c
       serial: 9c:b6:54:c5:fc:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:2000(size=256) memory:c2500000-c2500fff memory:c2400000-c2403fff
```

---

### Post by Bucky Ball on 2016-04-06
Please run the wireless script in my signature and post the output between code tags. Also, give the output of this between code tags, please (see green link in my signature at the bottom of this post):

```
sudo lshw -C network
```

---

### Post by sridhar8 on 2016-04-06
Thanks for the help. I am new to this ubuntu forum I didn't know this. I will stick to the formatting style. 
I restarted my computer this morning and it connected again.  This is the is the output 

```
  *-network                      description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 80:56:f2:3c:49:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=3.13.0-85-generic firmware=N/A ip=10.84.62.217 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:4000(size=256) memory:c2600000-c2603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 0c
       serial: 9c:b6:54:c5:fc:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=129.82.225.80 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:2000(size=256) memory:c2500000-c2500fff memory:c2400000-c2403fff
```

---

### Post by Bucky Ball on 2016-04-06
You have marked this thread as solved. Is it? If so, convention is to get back to helpers and let them and the community know how you fixed. Please share. ;)

---

