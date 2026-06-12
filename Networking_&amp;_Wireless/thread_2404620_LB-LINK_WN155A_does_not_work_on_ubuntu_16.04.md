---
title: "LB-LINK WN155A does not work on ubuntu 16.04"
date: 2018-10-26
forum: Networking &amp; Wireless
---

### Post by shadowdk3 on 2018-10-26
I have a usb wifi LB-Link WN155A, I try many method but still cannot work.

I have two wireless interface, one is PC and other is a usb wifi. PC wifi interface work OK but I cannot make usb wifi work.

For the module, I also try to compile mt and rtl ko, but fail.

Ubuntu 16.04

`uname -r`

```
4.15.0-38-generic
```

`lsusb`
```

    Bus 001 Device 008: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
```

`sudo lshw -numeric -class network`

```
    *-network               
           description: Wireless interface
           product: Intel Corporation [8086:24FD]
           vendor: Intel Corporation [8086]
           physical id: 0
           bus info: pci@0000:3a:00.0
           logical name: wlp58s0
           version: 78
           serial: f8:63:3f:3b:dc:ab
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-36-generic firmware=34.0.1 ip=192.168.10.151 latency=0 link=yes multicast=yes wireless=IEEE 802.11
           resources: irq:131 memory:dc100000-dc101fff
      *-network
           description: Ethernet interface
           product: Ethernet Connection (4) I219-V [8086:15D8]
           vendor: Intel Corporation [8086]
           physical id: 1f.6
           bus info: pci@0000:00:1f.6
           logical name: eno1
           version: 21
           serial: f4:4d:30:6e:78:a9
           capacity: 1Gbit/s
           width: 32 bits
           clock: 33MHz
           capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
           resources: irq:128 memory:dc200000-dc21ffff
      *-network
           description: Wireless interface
           physical id: 2
           bus info: usb@1:1
           logical name: wlxec3dfddbdbdb
           serial: ec:3d:fd:db:db:db
           capabilities: ethernet physical wireless
           configuration: broadcast=yes driver=rtl8192cu driverversion=4.15.0-36-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
```

`ifconfig`

```
    wlp58s0   Link encap:Ethernet  HWaddr f8:63:3f:3b:dc:ab  
          inet addr:192.168.10.151  Bcast:192.168.11.255  Mask:255.255.254.0
          inet6 addr: fe80::757f:9c2b:d5e1:7ff6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14472 errors:0 dropped:2 overruns:0 frame:0
          TX packets:2852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17545226 (17.5 MB)  TX bytes:398195 (398.1 KB)

    wlxec3dfddbdbdb Link encap:Ethernet  HWaddr ec:3d:fd:db:db:db  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I try to download driver (8192cu and 8188eu)

`lsmod`

```
    Module                  Size  Used by
    8188eu                724992  0
    ccm                    20480  6
    nls_iso8859_1          16384  1
    rfcomm                 77824  2
    rtl8xxxu              122880  0
    rtl8192cu              73728  0
    rtl_usb                20480  1 rtl8192cu
    rtl8192c_common        57344  1 rtl8192cu
    rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
    bnep                   20480  2
    arc4                   16384  4
    snd_hda_codec_hdmi     49152  1
    intel_wmi_thunderbolt    16384  0
    wmi_bmof               16384  0
    snd_hda_codec_realtek   106496  1
```

after I build module, I try to use `modprobe`, but it show

    modprobe: FATAL: Module 8188eu.ko not found in directory /lib/modules/4.15.0-36-generic

I also try to modify `/etc/network/interface`. But it still fail.

---

### Post by jeremy31 on 2018-10-26
I would try ```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu-blacklist.conf
```
Reboot

---

### Post by shadowdk3 on 2018-10-28
> **jeremy31 said:**
> I would try ```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu-blacklist.conf
```
Reboot

I try this cmd and still not work

here is the result of `iwcofing`

```

wlxec3dfddbdbdb  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```

and `iwlist scan`
```

wlxec3dfddbdbdb  No scan results
```

I also try `sudo iwlist scan`
```
wlxec3dfddbdbdb  Interface doesn't support scanning : Device or resource busy
```

---

### Post by praseodym on 2018-10-29
8188eu

Do also blacklist this one

---

