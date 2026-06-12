---
title: "wireless woes"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by davbeck on 2006-12-01
I am relitivly new to Ubuntu but, I have been playing around with it quit a bit.
I connect to a Linksys router through a D-Link range extender. I _have_ gotten the wireless networking working perfectly before but, I had to reformat due to some mistakes I made when I first installed Ubuntu and now it doesn't work again. I don't remember what I did to get it working.

I am useing an IBM thinkpad a21 (one of the best laptops ever made) My wireless card says CompUSA on it but all drivers and technical info says it is a realtek.

The connection that I need working is wlan0 but the only one that shows up in network manager is lo. I can view the networks in range and connect to them but nothing changes. I know I have good connection because my windows machine that sits right next to it gets great reception. when I iwconfig it shows that the signal strenght and everything else is 0.](*,) I cannot ping my router.

please help.

---

### Post by Tilex on 2006-12-01
Can you go in Settings->Network to see if your wireless card is activated?  I think it should be called something like "eth1"..

If, when you issue the command "iwconfig" there is only your localhost showing up ('lo'), your card is either not properly detected or not activated at all.

---

### Post by dbott67 on 2006-12-01
Can you post the output of the following commands:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
iwlist scanning
```
```
sudo lshw -C network
```

Thanks,
Dave

---

### Post by davbeck on 2006-12-01
as far as showing up in iwconfig: it does under wlan0 which is what it was called when it was working. it does not, however show up in the network manager that opens when you click the icon in the top left cornner.


here is the commands and their results


david@david-IBM:~$ iwconfig -a
-a        No such device

david@david-IBM:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

david@david-IBM:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:0F:D2:5E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 12ms ago
          Cell 02 - Address: 00:04:E2:B2:E2:F0
                    ESSID:"UUFNNG"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 17ms ago

sit0      Interface doesn't support scanning.

david@david-IBM:~$ sudo lshw -c network
Password:
Hardware Lister (lshw) - B.02.06
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.06)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

I hope this helps

---

### Post by FrodoB on 2006-12-01
You should be able to select wlan0 if you open up that icon.

---

### Post by davbeck on 2006-12-01
that is the thing thoe. it dosen't show up there in the drop down list.

---

### Post by dbott67 on 2006-12-01
> **davbeck said:**
> ```
david@david-IBM:~$ iwconfig -a
-a        No such device

```
 Hi Dave, the above command should be **i[COLOR="Red"]f[/COLOR]config -a**.  The command returns ALL interfaces and current settings:
```
dbott@edgy:/etc$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46738763 (44.5 MiB)  TX bytes:13157194 (12.5 MiB)
          Interrupt:185 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:676 (676.0 b)  TX bytes:676 (676.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

> **davbeck said:**
> ```
david@david-IBM:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

```
Your interfaces file looks good...
> **davbeck said:**
> ```

david@david-IBM:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:0F:D2:5E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 12ms ago
          Cell 02 - Address: 00:04:E2:B2:E2:F0
                    ESSID:"UUFNNG"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 17ms ago

sit0      Interface doesn't support scanning.
```
Your wireless card "sees" a couple of access points...

> **davbeck said:**
> ```
david@david-IBM:~$ sudo lshw -c network 
```

This should be an UPPERCASE C.  The command returns your NIC hardware and driver:
```
dbott@edgy:/etc$ **sudo lshw [COLOR="Red"]-C[/COLOR] network**
Password:
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185

```

-Dave

---

### Post by davbeck on 2006-12-01
david@david-IBM:~$ sudo lshw -c network
Password:
Hardware Lister (lshw) - B.02.06
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.06)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )


david@david-IBM:~$ sudo lshw -c network
Password:
Hardware Lister (lshw) - B.02.06
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.06)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by dbott67 on 2006-12-01
Dave, the c should be CAPITAL C, not lowercase.
```
sudo lshw -**[COLOR="Red"]C[/COLOR]** network
```
Use the copy/paste function if need be.

Also, please post the output of:
```
ifconfig -a
```

-Dave

---

### Post by davbeck on 2006-12-01
david@david-IBM:~$ sudo lshw -C network
Password:
  *-network DISABLED
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:89:34:73
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:f4120000-f4120fff ioport:1800-183f iomemory:f4100000-f411ffff irq:11
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@06:00.0
       logical name: wlan0
       version: 20
       serial: 00:0e:2e:82:41:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b/g link..
       resources: ioport:3000-30ff iomemory:26000000-260003ff irq:11


david@david-IBM:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:A4:89:34:73
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2243 (2.1 KiB)  TX bytes:2243 (2.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:82:41:B0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:1005 dropped:8 overruns:0 frame:0
          TX packets:2316 errors:2263 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8647 (8.4 KiB)  TX bytes:72303 (70.6 KiB)
          Interrupt:11 Memory:d89fe000-d89fe100

---

### Post by davbeck on 2006-12-02
Whatever was wrong with my computer, once I restarted for the fith time it went away and once again it is working perfectly

---

