---
title: "Cant connect to wireless network Ubuntu 12.04 Acer Aspire one D255"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by exepcis on 2013-12-25
Today I upgraded from Ubuntu 10.04 to 12.04. For a short time my wireless network was visible and usable. After some time the wireless network is not visible and usable anymore. 
The Broadcom STA driver is up and working

Hereunder some info that might help to find a solution

```

eth0      Link encap:Ethernet  HWaddr 4c:0f:6e:55:74:12  
          inet6 addr: fe80::4e0f:6eff:fe55:7412/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:283
          TX packets:0 errors:43 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 1c:75:08:bb:ab:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89320 (89.3 KB)  TX bytes:89320 (89.3 KB)

usb0      Link encap:Ethernet  HWaddr 02:11:f5:37:df:31  
          inet addr:192.168.42.95  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::11:f5ff:fe37:df31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3846 errors:3 dropped:0 overruns:0 frame:3
          TX packets:3970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3670875 (3.6 MB)  TX bytes:793188 (793.1 KB)


```

```

2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: brcmwl-1: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

```

lspci | grep Network
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

```
NetworkManager Tool

State: connected (global)

- Device: usb0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        02:11:F5:37:DF:31

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.95
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129


- Device: eth0 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        4C:0F:6E:55:74:12

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        1C:75:08:BB:AB:F8

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

```

sudo lshw -C network*-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: c1
       serial: 1c:75:08:bb:ab:f8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 4c:0f:6e:55:74:12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:56000000-56003fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:11:f5:37:df:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.95 link=yes multicast=yes

```

---

### Post by praseodym on 2013-12-31
Use the native driver instead:
```

sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot. Errors in the last 6 lines are ok.

---

### Post by exepcis on 2014-01-02
OK thanks propblem solved

---

