---
title: "Auto Ethernet not connecting"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-02-22
I have an Asus 1005PE with Ubuntu 9.10 x64. Every time I try to connect to the wired connection, being Auto Ethernet, it fails. And it doesn't show the network i want to connect to only Auto Ethernet

---

### Post by theweasel2345 on 2010-02-22
bump

---

### Post by theweasel2345 on 2010-02-22
I have a Asus 1005PE connected to a Dell router by an Ethernet cable. When I plug it in to my computer and try to connect to "Auto Ethernet" the computer fails to connect. The WiFi is working but just not the Auto Ethernet Connection
Thanks for the Help

---

### Post by overdrank on 2010-02-22
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Iowan on 2010-02-22
From a terminal, check/post results of **sudo lshw -C network** - that should provide information on the interface. It's probably a safe bet that **ifconfig -a** will show no IP address.

---

### Post by theweasel2345 on 2010-02-23
Both Commands
michael@michael-laptop:/$ sudo lshw -C network
[sudo] password for michael: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:e5:b1:32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.200 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:55:16:42
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
michael@michael-laptop:/$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:55:16:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

eth0:avahi Link encap:Ethernet  HWaddr e0:cb:4e:55:16:42  
          inet addr:169.254.5.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:e5:b1:32  
          inet addr:192.168.2.200  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fee5:b132/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3548898 (3.5 MB)  TX bytes:271937 (271.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-E5-B1-32-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by abdusamed on 2010-04-11
Yea..same problem.. it did work using 32bit.. but on 64 bit.. nothing happening.. it doesn't even connect. I'm running realteak ethernet controller.. When i did something link check for error.. or create error report, this is what i got. It though detected the right hardware but for some reason it wouldn't connect.. plz help

```
Checkbox Report**Checkbox Report**

 **Table Of Contents**

 
[LIST=1]
[*][Summary]("http://ubuntuforums.org/#summary")
[*]Hardware
[LIST]
[*][udev]("http://ubuntuforums.org/#udev")
[*][dmi]("http://ubuntuforums.org/#dmi")
[*][sysfs-attributes]("http://ubuntuforums.org/#sysfs-attributes")
[*][Processors]("http://ubuntuforums.org/#processors")
[/LIST]
 
[*]Software
[LIST]
[*][Packages]("http://ubuntuforums.org/#packages")
[*][LSB]("http://ubuntuforums.org/#lsb_release")
[/LIST]
 
[*][Questions]("http://ubuntuforums.org/#questions")
[*][Contextual Information]("http://ubuntuforums.org/#context")
[LIST]
[*][cat /proc/asound/card*/codec#*]("http://ubuntuforums.org/#id0x00007f9b3e0e9fc0")
[*][cat /proc/cpuinfo]("http://ubuntuforums.org/#id0x00007f9b42637080")
[*][dmidecode]("http://ubuntuforums.org/#id0x00007f9b42637100")
[*][lspci -vvnn]("http://ubuntuforums.org/#id0x00007f9b3e0e9f80")
[*][find /etc/modprobe.* -name \*.conf | xargs  cat]("http://ubuntuforums.org/#id0x00007f9b426371c0")
[*][cat /etc/modules]("http://ubuntuforums.org/#id0x00007f9b42637240")
[*][find /etc/sysctl.* -name \*.conf | xargs  cat]("http://ubuntuforums.org/#id0x00007f9b426372c0")
[/LIST]
[/LIST]
 **Summary**

 This report was created using checkbox-gtk 0.8.5 on 2010-04-11T05:09:40, on  Ubuntu 9.10 (amd64).
 You can view other reports for this system [here]("https://launchpad.net/+hwdb/+fingerprint/b1865df84255b8716d3bcc269ff410d1").
 **udev**

P: /devices/LNXSYSTM:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00
E: MODALIAS=acpi:LNXSYSTM:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:02
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXCPU:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:03
E: DRIVER=processor
E: MODALIAS=acpi:LNXCPU:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXPWRBN:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
E: DRIVER=button
E: MODALIAS=acpi:LNXPWRBN:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
E: PRODUCT=19/0/1/0
E: NAME="Power Button"
E: PHYS="LNXPWRBN/button/input0"
E: EV==3
E: KEY==10000000000000 0
E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0
N: input/event0
S: char/13:64
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0
E: MAJOR=13
E: MINOR=64
E: DEVNAME=/dev/input/event0
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:64

P: /devices/LNXSYSTM:00/LNXTHERM:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00
E: MODALIAS=acpi:LNXTHERM:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00
E: DRIVER=pci_root
E: MODALIAS=acpi:PNP0A08:PNP0A03:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:01
E: MODALIAS=acpi:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03
E: DRIVER=video
E: MODALIAS=acpi:LNXVIDEO:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:04
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:05
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:06
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/device:07
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/input/input5
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/input/input5
E: PRODUCT=19/0/6/0
E: NAME="Video Bus"
E: PHYS="/video/input0"
E: EV==3
E: KEY==3f000b00000000 0 0 0
E: MODALIAS=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/input/input5/event5
N: input/event5
S: char/13:69
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/input/input5/event5
E: MAJOR=13
E: MINOR=69
E: DEVNAME=/dev/input/event5
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:69

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
E: MODALIAS=acpi:LNXVIDEO:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0c
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0c
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0d
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:0d
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/device:0f
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/device:0f
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/device:10
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/device:10
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/ACPI0003:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/ACPI0003:00
E: DRIVER=ac
E: MODALIAS=acpi:ACPI0003:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/ACPI0003:00/power_supply/ACAD
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/ACPI0003:00/power_supply/ACAD
E: POWER_SUPPLY_NAME=ACAD
E: POWER_SUPPLY_TYPE=Mains
E: POWER_SUPPLY_ONLINE=1
E: SUBSYSTEM=power_supply

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0000:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0000:00
E: MODALIAS=acpi:PNP0000:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0100:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0100:00
E: MODALIAS=acpi:PNP0100:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0103:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0103:00
E: MODALIAS=acpi:PNP0103:PNP0C01:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0200:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0200:00
E: MODALIAS=acpi:PNP0200:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0303:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0303:00
E: MODALIAS=acpi:PNP0303:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0B00:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0B00:00
E: MODALIAS=acpi:PNP0B00:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C02:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C02:00
E: MODALIAS=acpi:PNP0C02:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C04:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C04:00
E: MODALIAS=acpi:PNP0C04:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00
E: DRIVER=ec
E: MODALIAS=acpi:PNP0C09:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:00
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:01
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:02
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:03
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:04
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:05
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:06
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C32:07
E: MODALIAS=acpi:PNP0C32:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/TOS6205:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/TOS6205:00
E: MODALIAS=acpi:TOS6205:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C0A:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C0A:00
E: DRIVER=battery
E: MODALIAS=acpi:PNP0C0A:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C0A:00/power_supply/BAT1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C0A:00/power_supply/BAT1
E: POWER_SUPPLY_NAME=BAT1
E: POWER_SUPPLY_TYPE=Battery
E: POWER_SUPPLY_STATUS=Charging
E: POWER_SUPPLY_PRESENT=1
E: POWER_SUPPLY_TECHNOLOGY=Li-ion
E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
E: POWER_SUPPLY_VOLTAGE_NOW=11100000
E: POWER_SUPPLY_CURRENT_NOW=0
E: POWER_SUPPLY_CHARGE_FULL_DESIGN=4000000
E: POWER_SUPPLY_CHARGE_FULL=4000000
E: POWER_SUPPLY_CHARGE_NOW=1440000
E: POWER_SUPPLY_MODEL_NAME=PA3534U 
E: POWER_SUPPLY_MANUFACTURER=TOSHIBA
E: POWER_SUPPLY_SERIAL_NUMBER=3658Q
E: SUBSYSTEM=power_supply

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0F13:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0F13:00
E: MODALIAS=acpi:PNP0F13:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:12
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:12
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1c
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1c
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1c/device:1d
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1c/device:1d
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/device:1f
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/device:1f
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:20
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:20
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:20/device:21
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:20/device:21
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/device:23
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/device:23
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:24
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:24
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:24/device:25
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:24/device:25
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:26
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:26
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:26/device:27
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:26/device:27
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2a
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2a
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00
E: DRIVER=button
E: MODALIAS=acpi:PNP0C0C:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
E: PRODUCT=19/0/1/0
E: NAME="Power Button"
E: PHYS="PNP0C0C/button/input0"
E: EV==3
E: KEY==10000000000000 0
E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
N: input/event2
S: char/13:66
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
E: MAJOR=13
E: MINOR=66
E: DEVNAME=/dev/input/event2
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:66

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00
E: DRIVER=button
E: MODALIAS=acpi:PNP0C0D:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
E: PRODUCT=19/0/5/0
E: NAME="Lid Switch"
E: PHYS="PNP0C0D/button/input0"
E: EV==21
E: SW==1
E: MODALIAS=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
E: SUBSYSTEM=input

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
N: input/event1
S: char/13:65
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
E: MAJOR=13
E: MINOR=65
E: DEVNAME=/dev/input/event1
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:65

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:00
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:01
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:01
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:02
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:02
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:03
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:03
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:04
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:04
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:05
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:05
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:06
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:06
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/PNP0C0F:07
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0F:07
E: DRIVER=pci_link
E: MODALIAS=acpi:PNP0C0F:
E: SUBSYSTEM=acpi

P: /devices/LNXSYSTM:00/device:00/TOS1900:00
E: UDEV_LOG=3
E: DEVPATH=/devices/LNXSYSTM:00/device:00/TOS1900:00
E: MODALIAS=acpi:TOS1900:
E: SUBSYSTEM=acpi

P: /devices/pci0000:00/0000:00:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:00.0
E: PCI_CLASS=60000
E: PCI_ID=8086:2A40
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:00.0
E: MODALIAS=pci:v00008086d00002A40sv00001179sd0000FF00bc06sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:01.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0
E: DRIVER=pcieport-driver
E: PCI_CLASS=60400
E: PCI_ID=8086:2A41
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:01.0
E: MODALIAS=pci:v00008086d00002A41sv00000000sd00000000bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie01
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie04
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie04
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie08
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:00:01.0:pcie08
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:01:00.0
E: PCI_CLASS=30000
E: PCI_ID=10DE:062A
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:01:00.0
E: MODALIAS=pci:v000010DEd0000062Asv00001179sd0000FF00bc03sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:01.0/pci_bus/0000:01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/pci_bus/0000:01
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1a.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2937
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1a.0
E: MODALIAS=pci:v00008086d00002937sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.0/usb3
N: bus/usb/003/001
S: char/189:256
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3
E: MAJOR=189
E: MINOR=256
E: DEVNAME=/dev/bus/usb/003/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/003/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=003
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.0
E: ID_SERIAL_SHORT=0000:00:1a.0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:256

P: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/003/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.0/usbmon/usbmon3
N: usbmon3
S: char/253:3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usbmon/usbmon3
E: MAJOR=253
E: MINOR=3
E: DEVNAME=/dev/usbmon3
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:3

P: /devices/pci0000:00/0000:00:1a.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2938
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1a.1
E: MODALIAS=pci:v00008086d00002938sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.1/usb4
N: bus/usb/004/001
S: char/189:384
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4
E: MAJOR=189
E: MINOR=384
E: DEVNAME=/dev/bus/usb/004/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/004/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=004
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.1
E: ID_SERIAL_SHORT=0000:00:1a.1
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:384

P: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/004/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.1/usbmon/usbmon4
N: usbmon4
S: char/253:4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usbmon/usbmon4
E: MAJOR=253
E: MINOR=4
E: DEVNAME=/dev/usbmon4
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:4

P: /devices/pci0000:00/0000:00:1a.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.2
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2939
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1a.2
E: MODALIAS=pci:v00008086d00002939sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.2/usb5
N: bus/usb/005/001
S: char/189:512
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5
E: MAJOR=189
E: MINOR=512
E: DEVNAME=/dev/bus/usb/005/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/005/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=005
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1a.2
E: ID_SERIAL_SHORT=0000:00:1a.2
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:512

P: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/005/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.2/usbmon/usbmon5
N: usbmon5
S: char/253:5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.2/usbmon/usbmon5
E: MAJOR=253
E: MINOR=5
E: DEVNAME=/dev/usbmon5
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:5

P: /devices/pci0000:00/0000:00:1a.7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7
E: DRIVER=ehci_hcd
E: PCI_CLASS=C0320
E: PCI_ID=8086:293C
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1a.7
E: MODALIAS=pci:v00008086d0000293Csv00001179sd0000FF00bc0Csc03i20
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1a.7/usb1
N: bus/usb/001/001
S: char/189:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1
E: MAJOR=189
E: MINOR=0
E: DEVNAME=/dev/bus/usb/001/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/001/001
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: BUSNUM=001
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_ehci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20ehci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=EHCI_Host_Controller
E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
E: ID_MODEL_ID=0002
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1a.7
E: ID_SERIAL_SHORT=0000:00:1a.7
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:0

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/001/001
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6
N: bus/usb/001/002
S: char/189:1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6
E: MAJOR=189
E: MINOR=1
E: DEVNAME=/dev/bus/usb/001/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/001/002
E: PRODUCT=4f2/b008/335
E: TYPE=239/2/1
E: BUSNUM=001
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=Chicony_Electronics_Co.__Ltd.
E: ID_VENDOR_ENC=Chicony\x20Electronics\x20Co.\x2c\x20Ltd.
E: ID_VENDOR_ID=04f2
E: ID_MODEL=Chicony_USB_2.0_Camera
E: ID_MODEL_ENC=Chicony\x20USB\x202.0\x20Camera
E: ID_MODEL_ID=b008
E: ID_REVISION=0335
E: ID_SERIAL=Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001
E: ID_SERIAL_SHORT=SN0001
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:
E: DEVLINKS=/dev/char/189:1

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
E: DEVTYPE=usb_interface
E: DRIVER=uvcvideo
E: DEVICE=/proc/bus/usb/001/002
E: PRODUCT=4f2/b008/335
E: TYPE=239/2/1
E: INTERFACE=14/1/0
E: MODALIAS=usb:v04F2pB008d0335dcEFdsc02dp01ic0Eisc01ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7
E: PRODUCT=3/4f2/b008/335
E: NAME="Chicony USB 2.0 Camera"
E: PHYS="usb-0000:00:1a.7-6/button"
E: EV==3
E: KEY==100000 0 0 0
E: MODALIAS=input:b0003v04F2pB008e0335-e0,1,kD4,ramlsfw
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7/event7
N: input/event7
S: char/13:71
S: input/by-id/usb-Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001-event-if00
S: input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7/event7
E: MAJOR=13
E: MINOR=71
E: DEVNAME=/dev/input/event7
E: SUBSYSTEM=input
E: ID_VENDOR=Chicony_Electronics_Co.__Ltd.
E: ID_VENDOR_ENC=Chicony\x20Electronics\x20Co.\x2c\x20Ltd.
E: ID_VENDOR_ID=04f2
E: ID_MODEL=Chicony_USB_2.0_Camera
E: ID_MODEL_ENC=Chicony\x20USB\x202.0\x20Camera
E: ID_MODEL_ID=b008
E: ID_REVISION=0335
E: ID_SERIAL=Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001
E: ID_SERIAL_SHORT=SN0001
E: ID_TYPE=video
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=uvcvideo
E: ID_PATH=pci-0000:00:1a.7-usb-0:6:1.0
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:71 /dev/input/by-id/usb-Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001-event-if00 /dev/input/by-path/pci-0000:00:1a.7-usb-0:6:1.0-event

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/video4linux/video0
N: video0
S: char/81:0
S: v4l/by-id/usb-Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001-video-index0
S: v4l/by-path/pci-0000:00:1a.7-usb-0:6:1.0-video-index0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/video4linux/video0
E: MAJOR=81
E: MINOR=0
E: DEVNAME=/dev/video0
E: SUBSYSTEM=video4linux
E: ID_V4L_VERSION=2
E: ID_V4L_PRODUCT=Chicony USB 2.0 Camera
E: ID_V4L_CAPABILITIES=:capture:
E: ID_VENDOR=Chicony_Electronics_Co.__Ltd.
E: ID_VENDOR_ENC=Chicony\x20Electronics\x20Co.\x2c\x20Ltd.
E: ID_VENDOR_ID=04f2
E: ID_MODEL=Chicony_USB_2.0_Camera
E: ID_MODEL_ENC=Chicony\x20USB\x202.0\x20Camera
E: ID_MODEL_ID=b008
E: ID_REVISION=0335
E: ID_SERIAL=Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001
E: ID_SERIAL_SHORT=SN0001
E: ID_TYPE=video
E: ID_BUS=usb
E: ID_USB_INTERFACES=:0e0100:0e0200:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=uvcvideo
E: ID_PATH=pci-0000:00:1a.7-usb-0:6:1.0
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Chicony_Electronics_Co.__Ltd._Chicony_USB_2.0_Camera_SN0001-video-index0 /dev/v4l/by-path/pci-0000:00:1a.7-usb-0:6:1.0-video-index0

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
E: DEVTYPE=usb_interface
E: DRIVER=uvcvideo
E: DEVICE=/proc/bus/usb/001/002
E: PRODUCT=4f2/b008/335
E: TYPE=239/2/1
E: INTERFACE=14/2/0
E: MODALIAS=usb:v04F2pB008d0335dcEFdsc02dp01ic0Eisc02ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1a.7/usbmon/usbmon1
N: usbmon1
S: char/253:1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.7/usbmon/usbmon1
E: MAJOR=253
E: MINOR=1
E: DEVNAME=/dev/usbmon1
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:1

P: /devices/pci0000:00/0000:00:1b.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
E: DRIVER=HDA Intel
E: PCI_CLASS=40300
E: PCI_ID=8086:293E
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1b.0
E: MODALIAS=pci:v00008086d0000293Esv00001179sd0000FF00bc04sc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1b.0/input/input10
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/input/input10
E: PRODUCT=1/10ec/272/1
E: NAME="HDA Digital PCBeep"
E: PHYS="card0/codec#0/beep0"
E: EV==40001
E: SND==6
E: MODALIAS=input:b0001v10ECp0272e0001-e0,12,kramls1,2,fw
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1b.0/input/input10/event10
N: input/event10
S: char/13:74
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/input/input10/event10
E: MAJOR=13
E: MINOR=74
E: DEVNAME=/dev/input/event10
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:74

P: /devices/pci0000:00/0000:00:1b.0/sound/card0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
E: SUBSYSTEM=sound
E: SOUND_INITIALIZED=1
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_MODEL_FROM_DATABASE=82801I (ICH9 Family) HD Audio Controller
E: ID_BUS=pci
E: ID_VENDOR_ID=0x8086
E: ID_MODEL_ID=0x293e
E: ID_PATH=pci-0000:00:1b.0
E: SOUND_FORM_FACTOR=internal

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/adsp
N: adsp
S: char/14:12
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/adsp
E: MAJOR=14
E: MINOR=12
E: DEVNAME=/dev/adsp
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:12

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/audio
N: audio
S: char/14:4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/audio
E: MAJOR=14
E: MINOR=4
E: DEVNAME=/dev/audio
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:4

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
N: dsp
S: char/14:3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
E: MAJOR=14
E: MINOR=3
E: DEVNAME=/dev/dsp
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:3

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
N: snd/hwC0D0
S: char/116:8
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
E: MAJOR=116
E: MINOR=8
E: DEVNAME=/dev/snd/hwC0D0
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:8

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
N: snd/hwC0D1
S: char/116:7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
E: MAJOR=116
E: MINOR=7
E: DEVNAME=/dev/snd/hwC0D1
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:7

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
N: mixer
S: char/14:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
E: MAJOR=14
E: MINOR=0
E: DEVNAME=/dev/mixer
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:0

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
N: snd/pcmC0D0c
S: char/116:6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
E: MAJOR=116
E: MINOR=6
E: DEVNAME=/dev/snd/pcmC0D0c
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:6

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
N: snd/pcmC0D0p
S: char/116:5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
E: MAJOR=116
E: MINOR=5
E: DEVNAME=/dev/snd/pcmC0D0p
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:5

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
N: snd/pcmC0D1p
S: char/116:4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
E: MAJOR=116
E: MINOR=4
E: DEVNAME=/dev/snd/pcmC0D1p
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:4

P: /devices/pci0000:00/0000:00:1c.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
E: DRIVER=pcieport-driver
E: PCI_CLASS=60400
E: PCI_ID=8086:2940
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:1c.0
E: MODALIAS=pci:v00008086d00002940sv00000000sd00000000bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie04
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie04
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:02
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:02
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1c.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2
E: DRIVER=pcieport-driver
E: PCI_CLASS=60400
E: PCI_ID=8086:2944
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:1c.2
E: MODALIAS=pci:v00008086d00002944sv00000000sd00000000bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie01
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie04
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie04
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie08
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:00:1c.2:pcie08
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.2/0000:0e:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0
E: DRIVER=r8169
E: PCI_CLASS=20000
E: PCI_ID=10EC:8168
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:0e:00.0
E: MODALIAS=pci:v000010ECd00008168sv00001179sd0000FF00bc02sc00i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/eth0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/0000:0e:00.0/net/eth0
E: INTERFACE=eth0
E: IFINDEX=2
E: SUBSYSTEM=net
E: ID_VENDOR_FROM_DATABASE=Realtek Semiconductor Co., Ltd.
E: ID_MODEL_FROM_DATABASE=RTL8111/8168B PCI Express Gigabit Ethernet controller
E: ID_BUS=pci
E: ID_VENDOR_ID=0x10ec
E: ID_MODEL_ID=0x8168

P: /devices/pci0000:00/0000:00:1c.2/pci_bus/0000:0e
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.2/pci_bus/0000:0e
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1c.3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3
E: DRIVER=pcieport-driver
E: PCI_CLASS=60400
E: PCI_ID=8086:2946
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:1c.3
E: MODALIAS=pci:v00008086d00002946sv00000000sd00000000bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie01
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie04
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie04
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie08
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:00:1c.3:pcie08
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:14:00.0
E: DRIVER=iwlagn
E: PCI_CLASS=28000
E: PCI_ID=8086:4232
E: PCI_SUBSYS_ID=8086:1201
E: PCI_SLOT_NAME=0000:14:00.0
E: MODALIAS=pci:v00008086d00004232sv00008086sd00001201bc02sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0
E: SUBSYSTEM=ieee80211

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0/rfkill0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0/rfkill0
E: RFKILL_NAME=phy0
E: RFKILL_TYPE=wlan
E: RFKILL_STATE=2
E: SUBSYSTEM=rfkill

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0/net/wlan0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/net/wlan0
E: INTERFACE=wlan0
E: IFINDEX=4
E: SUBSYSTEM=net
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_MODEL_FROM_DATABASE=Wireless WiFi Link 5100
E: ID_BUS=pci
E: ID_VENDOR_ID=0x8086
E: ID_MODEL_ID=0x4232

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0/net/wmaster0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/net/wmaster0
E: INTERFACE=wmaster0
E: IFINDEX=3
E: SUBSYSTEM=net

P: /devices/pci0000:00/0000:00:1c.3/pci_bus/0000:14
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.3/pci_bus/0000:14
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1c.5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5
E: DRIVER=pcieport-driver
E: PCI_CLASS=60400
E: PCI_ID=8086:294A
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:1c.5
E: MODALIAS=pci:v00008086d0000294Asv00000000sd00000000bc06sc04i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie01
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie04
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie04
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie08
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:00:1c.5:pcie08
E: SUBSYSTEM=pci_express

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.0
E: DRIVER=ohci1394
E: PCI_CLASS=C0010
E: PCI_ID=197B:2380
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:20:00.0
E: MODALIAS=pci:v0000197Bd00002380sv00001179sd0000FF00bc0Csc00i10
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0
E: DRIVER=nodemgr
E: SUBSYSTEM=ieee1394

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/00023f88d44028fa
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/00023f88d44028fa
E: SUBSYSTEM=ieee1394

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/00023f88d44028fa/ieee1394_node/00023f88d44028fa
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/00023f88d44028fa/ieee1394_node/00023f88d44028fa
E: SUBSYSTEM=ieee1394_node

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/ieee1394_host/fw-host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.0/fw-host0/ieee1394_host/fw-host0
E: SUBSYSTEM=ieee1394_host

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.1
E: DRIVER=sdhci-pci
E: PCI_CLASS=88000
E: PCI_ID=197B:2382
E: PCI_SUBSYS_ID=1179:FF02
E: PCI_SLOT_NAME=0000:20:00.1
E: MODALIAS=pci:v0000197Bd00002382sv00001179sd0000FF02bc08sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.1/leds/mmc0::
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.1/leds/mmc0::
E: SUBSYSTEM=leds

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.1/mmc_host/mmc0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.1/mmc_host/mmc0
E: SUBSYSTEM=mmc_host

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.2
E: PCI_CLASS=80501
E: PCI_ID=197B:2381
E: PCI_SUBSYS_ID=1179:FF02
E: PCI_SLOT_NAME=0000:20:00.2
E: MODALIAS=pci:v0000197Bd00002381sv00001179sd0000FF02bc08sc05i01
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.3
E: DRIVER=jmb38x_ms
E: PCI_CLASS=88000
E: PCI_ID=197B:2383
E: PCI_SUBSYS_ID=1179:FF02
E: PCI_SLOT_NAME=0000:20:00.3
E: MODALIAS=pci:v0000197Bd00002383sv00001179sd0000FF02bc08sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.3/memstick_host/memstick0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.3/memstick_host/memstick0
E: SUBSYSTEM=memstick_host

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/0000:20:00.4
E: PCI_CLASS=88000
E: PCI_ID=197B:2384
E: PCI_SUBSYS_ID=1179:FF02
E: PCI_SLOT_NAME=0000:20:00.4
E: MODALIAS=pci:v0000197Bd00002384sv00001179sd0000FF02bc08sc80i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1c.5/pci_bus/0000:20
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1c.5/pci_bus/0000:20
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1d.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2934
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1d.0
E: MODALIAS=pci:v00008086d00002934sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1d.0/usb6
N: bus/usb/006/001
S: char/189:640
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6
E: MAJOR=189
E: MINOR=640
E: DEVNAME=/dev/bus/usb/006/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/006/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=006
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.0
E: ID_SERIAL_SHORT=0000:00:1d.0
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:640

P: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/006/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon6
N: usbmon6
S: char/253:6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon6
E: MAJOR=253
E: MINOR=6
E: DEVNAME=/dev/usbmon6
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:6

P: /devices/pci0000:00/0000:00:1d.1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2935
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1d.1
E: MODALIAS=pci:v00008086d00002935sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1d.1/usb7
N: bus/usb/007/001
S: char/189:768
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7
E: MAJOR=189
E: MINOR=768
E: DEVNAME=/dev/bus/usb/007/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/007/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=007
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.1
E: ID_SERIAL_SHORT=0000:00:1d.1
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:768

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/007/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1
N: bus/usb/007/002
S: char/189:769
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1
E: MAJOR=189
E: MINOR=769
E: DEVNAME=/dev/bus/usb/007/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/007/002
E: PRODUCT=9da/a/14
E: TYPE=0/0/0
E: BUSNUM=007
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=A4Tech
E: ID_VENDOR_ENC=A4Tech
E: ID_VENDOR_ID=09da
E: ID_MODEL=USB_Mouse
E: ID_MODEL_ENC=USB\x20Mouse
E: ID_MODEL_ID=000a
E: ID_REVISION=0014
E: ID_SERIAL=A4Tech_USB_Mouse
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:
E: DEVLINKS=/dev/char/189:769

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
E: DEVTYPE=usb_interface
E: DRIVER=usbhid
E: DEVICE=/proc/bus/usb/007/002
E: PRODUCT=9da/a/14
E: TYPE=0/0/0
E: INTERFACE=3/1/2
E: MODALIAS=usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:09DA:000A.0001
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:09DA:000A.0001
E: DRIVER=a4tech
E: HID_ID=0003:000009DA:0000000A
E: HID_NAME=A4Tech USB Mouse
E: HID_PHYS=usb-0000:00:1d.1-1/input0
E: MODALIAS=hid:b0003v000009DAp0000000A
E: SUBSYSTEM=hid

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:09DA:000A.0001/hidraw/hidraw0
N: hidraw0
S: char/252:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:09DA:000A.0001/hidraw/hidraw0
E: MAJOR=252
E: MINOR=0
E: DEVNAME=/dev/hidraw0
E: SUBSYSTEM=hidraw
E: DEVLINKS=/dev/char/252:0

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
E: PRODUCT=3/9da/a/110
E: NAME="A4Tech USB Mouse"
E: PHYS="usb-0000:00:1d.1-1/input0"
E: UNIQ=""
E: EV==17
E: KEY==ff0000 0 0 0 0
E: REL==343
E: MSC==10
E: MODALIAS=input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw
E: SUBSYSTEM=input

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6/event6
N: input/event6
S: char/13:70
S: input/by-id/usb-A4Tech_USB_Mouse-event-mouse
S: input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6/event6
E: MAJOR=13
E: MINOR=70
E: DEVNAME=/dev/input/event6
E: SUBSYSTEM=input
E: ID_VENDOR=A4Tech
E: ID_VENDOR_ENC=A4Tech
E: ID_VENDOR_ID=09da
E: ID_MODEL=USB_Mouse
E: ID_MODEL_ENC=USB\x20Mouse
E: ID_MODEL_ID=000a
E: ID_REVISION=0014
E: ID_SERIAL=A4Tech_USB_Mouse
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_CLASS=mouse
E: ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:70 /dev/input/by-id/usb-A4Tech_USB_Mouse-event-mouse /dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-event-mouse

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6/mouse1
N: input/mouse1
S: char/13:33
S: input/by-id/usb-A4Tech_USB_Mouse-mouse
S: input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6/mouse1
E: MAJOR=13
E: MINOR=33
E: DEVNAME=/dev/input/mouse1
E: SUBSYSTEM=input
E: ID_VENDOR=A4Tech
E: ID_VENDOR_ENC=A4Tech
E: ID_VENDOR_ID=09da
E: ID_MODEL=USB_Mouse
E: ID_MODEL_ENC=USB\x20Mouse
E: ID_MODEL_ID=000a
E: ID_REVISION=0014
E: ID_SERIAL=A4Tech_USB_Mouse
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_CLASS=mouse
E: ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0
E: DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-A4Tech_USB_Mouse-mouse /dev/input/by-path/pci-0000:00:1d.1-usb-0:1:1.0-mouse

P: /devices/pci0000:00/0000:00:1d.1/usbmon/usbmon7
N: usbmon7
S: char/253:7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon7
E: MAJOR=253
E: MINOR=7
E: DEVNAME=/dev/usbmon7
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:7

P: /devices/pci0000:00/0000:00:1d.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2
E: DRIVER=uhci_hcd
E: PCI_CLASS=C0300
E: PCI_ID=8086:2936
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1d.2
E: MODALIAS=pci:v00008086d00002936sv00001179sd0000FF00bc0Csc03i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1d.2/usb8
N: bus/usb/008/001
S: char/189:896
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8
E: MAJOR=189
E: MINOR=896
E: DEVNAME=/dev/bus/usb/008/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/008/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: BUSNUM=008
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_uhci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20uhci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=UHCI_Host_Controller
E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
E: ID_MODEL_ID=0001
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.2
E: ID_SERIAL_SHORT=0000:00:1d.2
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:896

P: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/008/001
E: PRODUCT=1d6b/1/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.2/usbmon/usbmon8
N: usbmon8
S: char/253:8
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon8
E: MAJOR=253
E: MINOR=8
E: DEVNAME=/dev/usbmon8
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:8

P: /devices/pci0000:00/0000:00:1d.7
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7
E: DRIVER=ehci_hcd
E: PCI_CLASS=C0320
E: PCI_ID=8086:293A
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1d.7
E: MODALIAS=pci:v00008086d0000293Asv00001179sd0000FF00bc0Csc03i20
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1d.7/usb2
N: bus/usb/002/001
S: char/189:128
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2
E: MAJOR=189
E: MINOR=128
E: DEVNAME=/dev/bus/usb/002/001
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/002/001
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: BUSNUM=002
E: DEVNUM=001
E: SUBSYSTEM=usb
E: ID_VENDOR=Linux_2.6.31-14-generic_ehci_hcd
E: ID_VENDOR_ENC=Linux\x202.6.31-14-generic\x20ehci_hcd
E: ID_VENDOR_ID=1d6b
E: ID_MODEL=EHCI_Host_Controller
E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
E: ID_MODEL_ID=0002
E: ID_REVISION=0206
E: ID_SERIAL=Linux_2.6.31-14-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1d.7
E: ID_SERIAL_SHORT=0000:00:1d.7
E: ID_BUS=usb
E: ID_USB_INTERFACES=:090000:
E: DEVLINKS=/dev/char/189:128

P: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
E: DEVTYPE=usb_interface
E: DRIVER=hub
E: DEVICE=/proc/bus/usb/002/001
E: PRODUCT=1d6b/2/206
E: TYPE=9/0/0
E: INTERFACE=9/0/0
E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
E: SUBSYSTEM=usb

P: /devices/pci0000:00/0000:00:1d.7/usbmon/usbmon2
N: usbmon2
S: char/253:2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon2
E: MAJOR=253
E: MINOR=2
E: DEVNAME=/dev/usbmon2
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:2

P: /devices/pci0000:00/0000:00:1e.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1e.0
E: PCI_CLASS=60401
E: PCI_ID=8086:2448
E: PCI_SUBSYS_ID=0000:0000
E: PCI_SLOT_NAME=0000:00:1e.0
E: MODALIAS=pci:v00008086d00002448sv00000000sd00000000bc06sc04i01
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1e.0/pci_bus/0000:26
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:26
E: SUBSYSTEM=pci_bus

P: /devices/pci0000:00/0000:00:1f.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
E: PCI_CLASS=60100
E: PCI_ID=8086:2919
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1f.0
E: MODALIAS=pci:v00008086d00002919sv00001179sd0000FF00bc06sc01i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1f.2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
E: DRIVER=ahci
E: PCI_CLASS=10601
E: PCI_ID=8086:2929
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1f.2
E: MODALIAS=pci:v00008086d00002929sv00001179sd0000FF00bc01sc06i01
E: SUBSYSTEM=pci

P: /devices/pci0000:00/0000:00:1f.2/host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
E: DEVTYPE=scsi_target
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
E: DEVTYPE=scsi_device
E: DRIVER=sd
E: MODALIAS=scsi:t-0x00
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
N: sda
W: 51
S: block/8:0
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
E: MAJOR=8
E: MINOR=0
E: DEVNAME=/dev/sda
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: DKD_MEDIA_AVAILABLE=1
E: DKD_PARTITION_TABLE=1
E: DKD_PARTITION_TABLE_SCHEME=mbr
E: DKD_ATA_SMART_IS_AVAILABLE=1
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:0 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
N: sda1
W: 54
S: block/8:1
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part1
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part1
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
S: disk/by-uuid/8A6A61446A612E5F
S: disk/by-label/WinRE
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
E: MAJOR=8
E: MINOR=1
E: DEVNAME=/dev/sda1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=8A6A61446A612E5F
E: ID_FS_UUID_ENC=8A6A61446A612E5F
E: ID_FS_LABEL=WinRE
E: ID_FS_LABEL_ENC=WinRE
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=1
E: DKD_PARTITION_TYPE=0x27
E: DKD_PARTITION_SIZE=1572864000
E: DKD_PRESENTATION_HIDE=1
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:1 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part1 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 /dev/disk/by-uuid/8A6A61446A612E5F /dev/disk/by-label/WinRE

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
N: sda2
W: 55
S: block/8:2
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part2
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part2
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
S: disk/by-uuid/42B25C12B25C0CB3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
E: MAJOR=8
E: MINOR=2
E: DEVNAME=/dev/sda2
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=42B25C12B25C0CB3
E: ID_FS_UUID_ENC=42B25C12B25C0CB3
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=2
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=47879354880
E: DKD_PARTITION_FLAGS=boot
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:2 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part2 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2 /dev/disk/by-uuid/42B25C12B25C0CB3

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3
N: sda3
W: 57
S: block/8:3
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part3
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part3
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3
S: disk/by-uuid/EEAA66C9AA668E41
S: disk/by-label/Data
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3
E: MAJOR=8
E: MINOR=3
E: DEVNAME=/dev/sda3
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=EEAA66C9AA668E41
E: ID_FS_UUID_ENC=EEAA66C9AA668E41
E: ID_FS_LABEL=Data
E: ID_FS_LABEL_ENC=Data
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=3
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=11386310144
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:3 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part3 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part3 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3 /dev/disk/by-uuid/EEAA66C9AA668E41 /dev/disk/by-label/Data

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
N: sda4
W: 53
S: block/8:4
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part4
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part4
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
E: MAJOR=8
E: MINOR=4
E: DEVNAME=/dev/sda4
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=4
E: DKD_PARTITION_TYPE=0x0f
E: DKD_PARTITION_SIZE=339243448320
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:4 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part4 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part4 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
N: sda5
W: 52
S: block/8:5
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part5
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part5
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
S: disk/by-uuid/4b8d5ab3-212f-4ddc-82cb-af40bd702180
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda5
E: MAJOR=8
E: MINOR=5
E: DEVNAME=/dev/sda5
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=4b8d5ab3-212f-4ddc-82cb-af40bd702180
E: ID_FS_UUID_ENC=4b8d5ab3-212f-4ddc-82cb-af40bd702180
E: ID_FS_VERSION=1.0
E: ID_FS_TYPE=ext4
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=5
E: DKD_PARTITION_TYPE=0x83
E: DKD_PARTITION_SIZE=6613092864
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:5 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part5 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5 /dev/disk/by-uuid/4b8d5ab3-212f-4ddc-82cb-af40bd702180

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
N: sda6
W: 58
S: block/8:6
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part6
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part6
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6
S: disk/by-uuid/01CAD81B83BC41F0
S: disk/by-label/OverloAd
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda6
E: MAJOR=8
E: MINOR=6
E: DEVNAME=/dev/sda6
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=01CAD81B83BC41F0
E: ID_FS_UUID_ENC=01CAD81B83BC41F0
E: ID_FS_LABEL=OverloAd
E: ID_FS_LABEL_ENC=OverloAd
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=6
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=145554522624
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:6 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part6 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part6 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part6 /dev/disk/by-uuid/01CAD81B83BC41F0 /dev/disk/by-label/OverloAd

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda7
N: sda7
W: 56
S: block/8:7
S: disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part7
S: disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part7
S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part7
S: disk/by-uuid/01CAD8ACA9A50820
S: disk/by-label/FlowMore
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda7
E: MAJOR=8
E: MINOR=7
E: DEVNAME=/dev/sda7
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK4058GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK4058GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=FF011M
E: ID_SERIAL=TOSHIBA_MK4058GSX_Y8UBP1H0T
E: ID_SERIAL_SHORT=Y8UBP1H0T
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK4058G_Y8UBP1H0T
E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
E: ID_FS_UUID=01CAD8ACA9A50820
E: ID_FS_UUID_ENC=01CAD8ACA9A50820
E: ID_FS_LABEL=FlowMore
E: ID_FS_LABEL_ENC=FlowMore
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=7
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=187075736064
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:7 /dev/disk/by-id/ata-TOSHIBA_MK4058GSX_Y8UBP1H0T-part7 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK4058G_Y8UBP1H0T-part7 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part7 /dev/disk/by-uuid/01CAD8ACA9A50820 /dev/disk/by-label/FlowMore

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
E: SUBSYSTEM=scsi_device

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
E: SUBSYSTEM=scsi_disk

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
N: sg0
S: char/21:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
E: MAJOR=21
E: MINOR=0
E: DEVNAME=/dev/sg0
E: SUBSYSTEM=scsi_generic
E: DEVLINKS=/dev/char/21:0

P: /devices/pci0000:00/0000:00:1f.2/host1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0
E: DEVTYPE=scsi_target
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
E: DEVTYPE=scsi_device
E: DRIVER=sd
E: MODALIAS=scsi:t-0x00
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb
N: sdb
W: 48
S: block/8:16
S: disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT
S: disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT
S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb
E: MAJOR=8
E: MINOR=16
E: DEVNAME=/dev/sdb
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK3252GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK3252GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=LV010M
E: ID_SERIAL=TOSHIBA_MK3252GSX_Y8I9COUQT
E: ID_SERIAL_SHORT=Y8I9COUQT
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK3252G_Y8I9COUQT
E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
E: DKD_MEDIA_AVAILABLE=1
E: DKD_PARTITION_TABLE=1
E: DKD_PARTITION_TABLE_SCHEME=mbr
E: DKD_ATA_SMART_IS_AVAILABLE=1
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:16 /dev/disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT /dev/disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb/sdb1
N: sdb1
W: 49
S: block/8:17
S: disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT-part1
S: disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT-part1
S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb/sdb1
E: MAJOR=8
E: MINOR=17
E: DEVNAME=/dev/sdb1
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK3252GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK3252GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=LV010M
E: ID_SERIAL=TOSHIBA_MK3252GSX_Y8I9COUQT
E: ID_SERIAL_SHORT=Y8I9COUQT
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK3252G_Y8I9COUQT
E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=1
E: DKD_PARTITION_TYPE=0x0f
E: DKD_PARTITION_SIZE=320071532544
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:17 /dev/disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT-part1 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb/sdb5
N: sdb5
W: 50
S: block/8:21
S: disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT-part5
S: disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT-part5
S: disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5
S: disk/by-uuid/E26090D36090B031
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb/sdb5
E: MAJOR=8
E: MINOR=21
E: DEVNAME=/dev/sdb5
E: DEVTYPE=partition
E: SUBSYSTEM=block
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=TOSHIBA_MK3252GSX
E: ID_MODEL_ENC=TOSHIBA\x20MK3252GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=LV010M
E: ID_SERIAL=TOSHIBA_MK3252GSX_Y8I9COUQT
E: ID_SERIAL_SHORT=Y8I9COUQT
E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK3252G_Y8I9COUQT
E: ID_PATH=pci-0000:00:1f.2-scsi-1:0:0:0
E: ID_FS_UUID=E26090D36090B031
E: ID_FS_UUID_ENC=E26090D36090B031
E: ID_FS_TYPE=ntfs
E: ID_FS_USAGE=filesystem
E: DKD_PARTITION=1
E: DKD_PARTITION_SCHEME=mbr
E: DKD_PARTITION_NUMBER=5
E: DKD_PARTITION_TYPE=0x07
E: DKD_PARTITION_SIZE=320070483968
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/8:21 /dev/disk/by-id/ata-TOSHIBA_MK3252GSX_Y8I9COUQT-part5 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK3252G_Y8I9COUQT-part5 /dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5 /dev/disk/by-uuid/E26090D36090B031

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_device/1:0:0:0
E: SUBSYSTEM=scsi_device

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_disk/1:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_disk/1:0:0:0
E: SUBSYSTEM=scsi_disk

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
N: sg1
S: char/21:1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/scsi_generic/sg1
E: MAJOR=21
E: MINOR=1
E: DEVNAME=/dev/sg1
E: SUBSYSTEM=scsi_generic
E: DEVLINKS=/dev/char/21:1

P: /devices/pci0000:00/0000:00:1f.2/host2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/scsi_host/host4
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0
E: DEVTYPE=scsi_target
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
E: DEVTYPE=scsi_device
E: DRIVER=sr
E: MODALIAS=scsi:t-0x05
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0
N: sr0
S: block/11:0
S: scd0
S: disk/by-path/pci-0000:00:1f.2-scsi-4:0:0:0
S: cdrom
S: cdrw
S: dvd
S: dvdrw
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0
E: MAJOR=11
E: MINOR=0
E: DEVNAME=/dev/sr0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_CDROM=1
E: ID_CDROM_CD_R=1
E: ID_CDROM_CD_RW=1
E: ID_CDROM_DVD=1
E: ID_CDROM_DVD_R=1
E: ID_CDROM_DVD_RAM=1
E: ID_CDROM_MRW=1
E: ID_CDROM_MRW_W=1
E: ID_VENDOR=PIONEER
E: ID_VENDOR_ENC=PIONEER\x20
E: ID_MODEL=DVD-RW_DVRTD08A
E: ID_MODEL_ENC=DVD-RW\x20\x20DVRTD08A
E: ID_REVISION=1.54
E: ID_TYPE=cd
E: ID_BUS=scsi
E: ID_PATH=pci-0000:00:1f.2-scsi-4:0:0:0
E: ACL_MANAGE=1
E: GENERATED=1
E: DKD_PRESENTATION_NOPOLICY=0
E: DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.2-scsi-4:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0
E: SUBSYSTEM=scsi_device

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/scsi_generic/sg2
N: sg2
S: char/21:2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/scsi_generic/sg2
E: MAJOR=21
E: MINOR=2
E: DEVNAME=/dev/sg2
E: SUBSYSTEM=scsi_generic
E: DEVLINKS=/dev/char/21:2

P: /devices/pci0000:00/0000:00:1f.2/host5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5
E: DEVTYPE=scsi_host
E: SUBSYSTEM=scsi

P: /devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host5/scsi_host/host5
E: SUBSYSTEM=scsi_host

P: /devices/pci0000:00/0000:00:1f.3
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
E: PCI_CLASS=C0500
E: PCI_ID=8086:2930
E: PCI_SUBSYS_ID=1179:FF00
E: PCI_SLOT_NAME=0000:00:1f.3
E: MODALIAS=pci:v00008086d00002930sv00001179sd0000FF00bc0Csc05i00
E: SUBSYSTEM=pci

P: /devices/pci0000:00/pci_bus/0000:00
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
E: SUBSYSTEM=pci_bus

P: /devices/platform/Fixed MDIO bus.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/Fixed MDIO bus.0
E: MODALIAS=platform:Fixed MDIO bus
E: SUBSYSTEM=platform

P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
E: SUBSYSTEM=mdio_bus

P: /devices/platform/i8042
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042
E: DRIVER=i8042
E: MODALIAS=platform:i8042
E: SUBSYSTEM=platform

P: /devices/platform/i8042/serio0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0
E: DRIVER=atkbd
E: SERIO_TYPE=06
E: SERIO_PROTO=00
E: SERIO_ID=00
E: SERIO_EXTRA=00
E: MODALIAS=serio:ty06pr00id00ex00
E: SUBSYSTEM=serio

P: /devices/platform/i8042/serio0/input/input4
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0/input/input4
E: PRODUCT=11/1/1/ab41
E: NAME="AT Translated Set 2 keyboard"
E: PHYS="isa0060/serio0/input0"
E: EV==120013
E: KEY==402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
E: MSC==10
E: LED==7
E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw
E: SUBSYSTEM=input

P: /devices/platform/i8042/serio0/input/input4/event4
N: input/event4
S: char/13:68
S: input/by-path/platform-i8042-serio-0-event-kbd
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio0/input/input4/event4
E: MAJOR=13
E: MINOR=68
E: DEVNAME=/dev/input/event4
E: SUBSYSTEM=input
E: ID_CLASS=kbd
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-0
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:68 /dev/input/by-path/platform-i8042-serio-0-event-kbd

P: /devices/platform/i8042/serio1
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1
E: DRIVER=psmouse
E: SERIO_TYPE=01
E: SERIO_PROTO=00
E: SERIO_ID=00
E: SERIO_EXTRA=00
E: MODALIAS=serio:ty01pr00id00ex00
E: SUBSYSTEM=serio

P: /devices/platform/i8042/serio1/input/input8
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input8
E: PRODUCT=11/2/8/0
E: NAME="PS/2 Mouse"
E: PHYS="isa0060/serio1/input1"
E: EV==7
E: KEY==70000 0 0 0 0
E: REL==3
E: MODALIAS=input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw
E: SUBSYSTEM=input

P: /devices/platform/i8042/serio1/input/input8/event8
N: input/event8
S: char/13:72
S: input/by-path/platform-i8042-serio-1-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input8/event8
E: MAJOR=13
E: MINOR=72
E: DEVNAME=/dev/input/event8
E: SUBSYSTEM=input
E: ID_CLASS=mouse
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:72 /dev/input/by-path/platform-i8042-serio-1-event-mouse

P: /devices/platform/i8042/serio1/input/input8/mouse2
N: input/mouse2
S: char/13:34
S: input/by-path/platform-i8042-serio-1-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input8/mouse2
E: MAJOR=13
E: MINOR=34
E: DEVNAME=/dev/input/mouse2
E: SUBSYSTEM=input
E: ID_CLASS=mouse
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DEVLINKS=/dev/char/13:34 /dev/input/by-path/platform-i8042-serio-1-mouse

P: /devices/platform/i8042/serio1/input/input9
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input9
E: PRODUCT=11/2/8/7321
E: NAME="AlpsPS/2 ALPS GlidePoint"
E: PHYS="isa0060/serio1/input0"
E: EV==f
E: KEY==420 70000 0 0 0 0
E: REL==3
E: ABS==1000003
E: MODALIAS=input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw
E: SUBSYSTEM=input

P: /devices/platform/i8042/serio1/input/input9/event9
N: input/event9
S: char/13:73
S: input/by-path/platform-i8042-serio-1-event-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input9/event9
E: MAJOR=13
E: MINOR=73
E: DEVNAME=/dev/input/event9
E: SUBSYSTEM=input
E: ID_CLASS=mouse
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:73 /dev/input/by-path/platform-i8042-serio-1-event-mouse

P: /devices/platform/i8042/serio1/input/input9/mouse3
N: input/mouse3
S: char/13:35
S: input/by-path/platform-i8042-serio-1-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/i8042/serio1/input/input9/mouse3
E: MAJOR=13
E: MINOR=35
E: DEVNAME=/dev/input/mouse3
E: SUBSYSTEM=input
E: ID_CLASS=mouse
E: ID_SERIAL=noserial
E: ID_PATH=platform-i8042-serio-1
E: DEVLINKS=/dev/char/13:35 /dev/input/by-path/platform-i8042-serio-1-mouse

P: /devices/platform/pcspkr
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/pcspkr
E: MODALIAS=platform:pcspkr
E: SUBSYSTEM=platform

P: /devices/platform/regulatory.0
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/regulatory.0
E: MODALIAS=platform:regulatory
E: SUBSYSTEM=platform

P: /devices/platform/serial8250
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250
E: DRIVER=serial8250
E: MODALIAS=platform:serial8250
E: SUBSYSTEM=platform

P: /devices/platform/serial8250/tty/ttyS0
N: ttyS0
S: char/4:64
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:64

P: /devices/platform/serial8250/tty/ttyS1
N: ttyS1
S: char/4:65
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
E: MAJOR=4
E: MINOR=65
E: DEVNAME=/dev/ttyS1
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:65

P: /devices/platform/serial8250/tty/ttyS2
N: ttyS2
S: char/4:66
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
E: MAJOR=4
E: MINOR=66
E: DEVNAME=/dev/ttyS2
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:66

P: /devices/platform/serial8250/tty/ttyS3
N: ttyS3
S: char/4:67
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
E: MAJOR=4
E: MINOR=67
E: DEVNAME=/dev/ttyS3
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:67

P: /devices/pnp0/00:00
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:00
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:01
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:01
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:02
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:02
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:03
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:03
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:04
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:04
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:05
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:05
E: DRIVER=rtc_cmos
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:05/rtc/rtc0
N: rtc0
S: char/254:0
S: rtc
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:05/rtc/rtc0
E: MAJOR=254
E: MINOR=0
E: DEVNAME=/dev/rtc0
E: SUBSYSTEM=rtc
E: DEVLINKS=/dev/char/254:0 /dev/rtc

P: /devices/pnp0/00:06
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:06
E: DRIVER=i8042 kbd
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:07
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:07
E: DRIVER=i8042 aux
E: SUBSYSTEM=pnp

P: /devices/pnp0/00:08
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:08
E: DRIVER=system
E: SUBSYSTEM=pnp

P: /devices/virtual/backlight/acpi_video0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/backlight/acpi_video0
E: SUBSYSTEM=backlight

P: /devices/virtual/bdi/0:22
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/0:22
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/11:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/11:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:1
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:10
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:11
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:12
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:13
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:14
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:15
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:2
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:3
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:4
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:5
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:6
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:7
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:8
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/1:9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/1:9
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:1
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:2
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:3
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:4
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:5
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:6
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/7:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/7:7
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:0
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:16
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:16
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:2-fuseblk
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:2-fuseblk
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:21-fuseblk
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:21-fuseblk
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/8:3-fuseblk
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/8:3-fuseblk
E: SUBSYSTEM=bdi

P: /devices/virtual/bdi/default
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/bdi/default
E: SUBSYSTEM=bdi

P: /devices/virtual/block/loop0
N: loop0
W: 38
S: block/7:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop0
E: MAJOR=7
E: MINOR=0
E: DEVNAME=/dev/loop0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:0

P: /devices/virtual/block/loop1
N: loop1
W: 29
S: block/7:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop1
E: MAJOR=7
E: MINOR=1
E: DEVNAME=/dev/loop1
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:1

P: /devices/virtual/block/loop2
N: loop2
W: 27
S: block/7:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop2
E: MAJOR=7
E: MINOR=2
E: DEVNAME=/dev/loop2
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:2

P: /devices/virtual/block/loop3
N: loop3
W: 33
S: block/7:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop3
E: MAJOR=7
E: MINOR=3
E: DEVNAME=/dev/loop3
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:3

P: /devices/virtual/block/loop4
N: loop4
W: 44
S: block/7:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop4
E: MAJOR=7
E: MINOR=4
E: DEVNAME=/dev/loop4
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:4

P: /devices/virtual/block/loop5
N: loop5
W: 45
S: block/7:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop5
E: MAJOR=7
E: MINOR=5
E: DEVNAME=/dev/loop5
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:5

P: /devices/virtual/block/loop6
N: loop6
W: 35
S: block/7:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop6
E: MAJOR=7
E: MINOR=6
E: DEVNAME=/dev/loop6
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:6

P: /devices/virtual/block/loop7
N: loop7
W: 46
S: block/7:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/loop7
E: MAJOR=7
E: MINOR=7
E: DEVNAME=/dev/loop7
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/7:7

P: /devices/virtual/block/ram0
N: ram0
W: 43
S: block/1:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram0
E: MAJOR=1
E: MINOR=0
E: DEVNAME=/dev/ram0
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:0

P: /devices/virtual/block/ram1
N: ram1
W: 41
S: block/1:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram1
E: MAJOR=1
E: MINOR=1
E: DEVNAME=/dev/ram1
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:1

P: /devices/virtual/block/ram10
N: ram10
W: 25
S: block/1:10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram10
E: MAJOR=1
E: MINOR=10
E: DEVNAME=/dev/ram10
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:10

P: /devices/virtual/block/ram11
N: ram11
W: 26
S: block/1:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram11
E: MAJOR=1
E: MINOR=11
E: DEVNAME=/dev/ram11
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:11

P: /devices/virtual/block/ram12
N: ram12
W: 37
S: block/1:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram12
E: MAJOR=1
E: MINOR=12
E: DEVNAME=/dev/ram12
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:12

P: /devices/virtual/block/ram13
N: ram13
W: 24
S: block/1:13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram13
E: MAJOR=1
E: MINOR=13
E: DEVNAME=/dev/ram13
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:13

P: /devices/virtual/block/ram14
N: ram14
W: 23
S: block/1:14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram14
E: MAJOR=1
E: MINOR=14
E: DEVNAME=/dev/ram14
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:14

P: /devices/virtual/block/ram15
N: ram15
W: 40
S: block/1:15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram15
E: MAJOR=1
E: MINOR=15
E: DEVNAME=/dev/ram15
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:15

P: /devices/virtual/block/ram2
N: ram2
W: 42
S: block/1:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram2
E: MAJOR=1
E: MINOR=2
E: DEVNAME=/dev/ram2
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:2

P: /devices/virtual/block/ram3
N: ram3
W: 36
S: block/1:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram3
E: MAJOR=1
E: MINOR=3
E: DEVNAME=/dev/ram3
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:3

P: /devices/virtual/block/ram4
N: ram4
W: 21
S: block/1:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram4
E: MAJOR=1
E: MINOR=4
E: DEVNAME=/dev/ram4
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:4

P: /devices/virtual/block/ram5
N: ram5
W: 39
S: block/1:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram5
E: MAJOR=1
E: MINOR=5
E: DEVNAME=/dev/ram5
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:5

P: /devices/virtual/block/ram6
N: ram6
W: 31
S: block/1:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram6
E: MAJOR=1
E: MINOR=6
E: DEVNAME=/dev/ram6
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:6

P: /devices/virtual/block/ram7
N: ram7
W: 34
S: block/1:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram7
E: MAJOR=1
E: MINOR=7
E: DEVNAME=/dev/ram7
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:7

P: /devices/virtual/block/ram8
N: ram8
W: 30
S: block/1:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram8
E: MAJOR=1
E: MINOR=8
E: DEVNAME=/dev/ram8
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:8

P: /devices/virtual/block/ram9
N: ram9
W: 28
S: block/1:9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/ram9
E: MAJOR=1
E: MINOR=9
E: DEVNAME=/dev/ram9
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DEVLINKS=/dev/block/1:9

P: /devices/virtual/dmi/id
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/dmi/id
E: MODALIAS=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
E: SUBSYSTEM=dmi

P: /devices/virtual/input/input3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input3
E: PRODUCT=17/1/1/100
E: NAME="Macintosh mouse button emulation"
E: EV==7
E: KEY==70000 0 0 0 0
E: REL==3
E: MODALIAS=input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw
E: SUBSYSTEM=input

P: /devices/virtual/input/input3/event3
N: input/event3
S: char/13:67
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input3/event3
E: MAJOR=13
E: MINOR=67
E: DEVNAME=/dev/input/event3
E: SUBSYSTEM=input
E: DMI_VENDOR=TOSHIBA
E: DEVLINKS=/dev/char/13:67

P: /devices/virtual/input/input3/mouse0
N: input/mouse0
S: char/13:32
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/input3/mouse0
E: MAJOR=13
E: MINOR=32
E: DEVNAME=/dev/input/mouse0
E: SUBSYSTEM=input
E: DEVLINKS=/dev/char/13:32

P: /devices/virtual/input/mice
N: input/mice
S: char/13:63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/input/mice
E: MAJOR=13
E: MINOR=63
E: DEVNAME=/dev/input/mice
E: SUBSYSTEM=input
E: DEVLINKS=/dev/char/13:63

P: /devices/virtual/mem/full
N: full
S: char/1:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/full
E: MAJOR=1
E: MINOR=7
E: DEVNAME=/dev/full
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:7

P: /devices/virtual/mem/kmsg
N: kmsg
S: char/1:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/kmsg
E: MAJOR=1
E: MINOR=11
E: DEVNAME=/dev/kmsg
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:11

P: /devices/virtual/mem/mem
N: mem
S: char/1:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/mem
E: MAJOR=1
E: MINOR=1
E: DEVNAME=/dev/mem
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:1

P: /devices/virtual/mem/null
N: null
S: char/1:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/null
E: MAJOR=1
E: MINOR=3
E: DEVNAME=/dev/null
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:3

P: /devices/virtual/mem/oldmem
N: oldmem
S: char/1:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/oldmem
E: MAJOR=1
E: MINOR=12
E: DEVNAME=/dev/oldmem
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:12

P: /devices/virtual/mem/port
N: port
S: char/1:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/port
E: MAJOR=1
E: MINOR=4
E: DEVNAME=/dev/port
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:4

P: /devices/virtual/mem/random
N: random
S: char/1:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/random
E: MAJOR=1
E: MINOR=8
E: DEVNAME=/dev/random
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:8

P: /devices/virtual/mem/urandom
N: urandom
S: char/1:9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/urandom
E: MAJOR=1
E: MINOR=9
E: DEVNAME=/dev/urandom
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:9

P: /devices/virtual/mem/zero
N: zero
S: char/1:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/mem/zero
E: MAJOR=1
E: MINOR=5
E: DEVNAME=/dev/zero
E: SUBSYSTEM=mem
E: DEVLINKS=/dev/char/1:5

P: /devices/virtual/misc/binder
N: binder
S: char/10:59
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/binder
E: MAJOR=10
E: MINOR=59
E: DEVNAME=/dev/binder
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:59

P: /devices/virtual/misc/cpu_dma_latency
N: cpu_dma_latency
S: char/10:58
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
E: MAJOR=10
E: MINOR=58
E: DEVNAME=/dev/cpu_dma_latency
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:58

P: /devices/virtual/misc/device-mapper
N: mapper/control
S: char/10:60
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/device-mapper
E: MAJOR=10
E: MINOR=60
E: DEVNAME=/dev/mapper/control
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:60

P: /devices/virtual/misc/ecryptfs
N: ecryptfs
S: char/10:62
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/ecryptfs
E: MAJOR=10
E: MINOR=62
E: DEVNAME=/dev/ecryptfs
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:62

P: /devices/virtual/misc/fuse
N: fuse
S: char/10:229
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/fuse
E: MAJOR=10
E: MINOR=229
E: DEVNAME=/dev/fuse
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:229

P: /devices/virtual/misc/hpet
N: hpet
S: char/10:228
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/hpet
E: MAJOR=10
E: MINOR=228
E: DEVNAME=/dev/hpet
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:228

P: /devices/virtual/misc/mcelog
N: mcelog
S: char/10:227
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/mcelog
E: MAJOR=10
E: MINOR=227
E: DEVNAME=/dev/mcelog
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:227

P: /devices/virtual/misc/network_latency
N: network_latency
S: char/10:57
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/network_latency
E: MAJOR=10
E: MINOR=57
E: DEVNAME=/dev/network_latency
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:57

P: /devices/virtual/misc/network_throughput
N: network_throughput
S: char/10:56
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/network_throughput
E: MAJOR=10
E: MINOR=56
E: DEVNAME=/dev/network_throughput
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:56

P: /devices/virtual/misc/pktcdvd!control
N: pktcdvd/control
S: char/10:61
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/pktcdvd!control
E: MAJOR=10
E: MINOR=61
E: DEVNAME=/dev/pktcdvd/control
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:61

P: /devices/virtual/misc/psaux
N: psaux
S: char/10:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/psaux
E: MAJOR=10
E: MINOR=1
E: DEVNAME=/dev/psaux
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:1

P: /devices/virtual/misc/rfkill
N: rfkill
S: char/10:63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/rfkill
E: MAJOR=10
E: MINOR=63
E: DEVNAME=/dev/rfkill
E: SUBSYSTEM=misc
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/10:63

P: /devices/virtual/misc/snapshot
N: snapshot
S: char/10:231
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/misc/snapshot
E: MAJOR=10
E: MINOR=231
E: DEVNAME=/dev/snapshot
E: SUBSYSTEM=misc
E: DEVLINKS=/dev/char/10:231

P: /devices/virtual/net/lo
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/net/lo
E: INTERFACE=lo
E: IFINDEX=1
E: SUBSYSTEM=net

P: /devices/virtual/ppp/ppp
N: ppp
S: char/108:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/ppp/ppp
E: MAJOR=108
E: MINOR=0
E: DEVNAME=/dev/ppp
E: SUBSYSTEM=ppp
E: DEVLINKS=/dev/char/108:0

P: /devices/virtual/sound/seq
N: snd/seq
S: char/116:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/seq
E: MAJOR=116
E: MINOR=3
E: DEVNAME=/dev/snd/seq
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:3

P: /devices/virtual/sound/sequencer
N: sequencer
S: char/14:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/sequencer
E: MAJOR=14
E: MINOR=1
E: DEVNAME=/dev/sequencer
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:1

P: /devices/virtual/sound/sequencer2
N: sequencer2
S: char/14:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/sequencer2
E: MAJOR=14
E: MINOR=8
E: DEVNAME=/dev/sequencer2
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/14:8

P: /devices/virtual/sound/timer
N: snd/timer
S: char/116:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/sound/timer
E: MAJOR=116
E: MINOR=2
E: DEVNAME=/dev/snd/timer
E: SUBSYSTEM=sound
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:2

P: /devices/virtual/thermal/cooling_device0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device0
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device1
E: SUBSYSTEM=thermal

P: /devices/virtual/thermal/cooling_device2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/thermal/cooling_device2
E: SUBSYSTEM=thermal

P: /devices/virtual/tty/console
N: console
S: char/5:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/console
E: MAJOR=5
E: MINOR=1
E: DEVNAME=/dev/console
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:1

P: /devices/virtual/tty/ptmx
N: ptmx
S: char/5:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/ptmx
E: MAJOR=5
E: MINOR=2
E: DEVNAME=/dev/ptmx
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:2

P: /devices/virtual/tty/tty
N: tty
S: char/5:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty
E: MAJOR=5
E: MINOR=0
E: DEVNAME=/dev/tty
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:0

P: /devices/virtual/tty/tty0
N: tty0
S: char/4:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty0
E: MAJOR=4
E: MINOR=0
E: DEVNAME=/dev/tty0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:0

P: /devices/virtual/tty/tty1
N: tty1
S: char/4:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty1
E: MAJOR=4
E: MINOR=1
E: DEVNAME=/dev/tty1
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:1

P: /devices/virtual/tty/tty10
N: tty10
S: char/4:10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty10
E: MAJOR=4
E: MINOR=10
E: DEVNAME=/dev/tty10
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:10

P: /devices/virtual/tty/tty11
N: tty11
S: char/4:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty11
E: MAJOR=4
E: MINOR=11
E: DEVNAME=/dev/tty11
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:11

P: /devices/virtual/tty/tty12
N: tty12
S: char/4:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty12
E: MAJOR=4
E: MINOR=12
E: DEVNAME=/dev/tty12
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:12

P: /devices/virtual/tty/tty13
N: tty13
S: char/4:13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty13
E: MAJOR=4
E: MINOR=13
E: DEVNAME=/dev/tty13
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:13

P: /devices/virtual/tty/tty14
N: tty14
S: char/4:14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty14
E: MAJOR=4
E: MINOR=14
E: DEVNAME=/dev/tty14
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:14

P: /devices/virtual/tty/tty15
N: tty15
S: char/4:15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty15
E: MAJOR=4
E: MINOR=15
E: DEVNAME=/dev/tty15
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:15

P: /devices/virtual/tty/tty16
N: tty16
S: char/4:16
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty16
E: MAJOR=4
E: MINOR=16
E: DEVNAME=/dev/tty16
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:16

P: /devices/virtual/tty/tty17
N: tty17
S: char/4:17
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty17
E: MAJOR=4
E: MINOR=17
E: DEVNAME=/dev/tty17
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:17

P: /devices/virtual/tty/tty18
N: tty18
S: char/4:18
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty18
E: MAJOR=4
E: MINOR=18
E: DEVNAME=/dev/tty18
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:18

P: /devices/virtual/tty/tty19
N: tty19
S: char/4:19
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty19
E: MAJOR=4
E: MINOR=19
E: DEVNAME=/dev/tty19
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:19

P: /devices/virtual/tty/tty2
N: tty2
S: char/4:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty2
E: MAJOR=4
E: MINOR=2
E: DEVNAME=/dev/tty2
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:2

P: /devices/virtual/tty/tty20
N: tty20
S: char/4:20
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty20
E: MAJOR=4
E: MINOR=20
E: DEVNAME=/dev/tty20
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:20

P: /devices/virtual/tty/tty21
N: tty21
S: char/4:21
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty21
E: MAJOR=4
E: MINOR=21
E: DEVNAME=/dev/tty21
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:21

P: /devices/virtual/tty/tty22
N: tty22
S: char/4:22
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty22
E: MAJOR=4
E: MINOR=22
E: DEVNAME=/dev/tty22
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:22

P: /devices/virtual/tty/tty23
N: tty23
S: char/4:23
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty23
E: MAJOR=4
E: MINOR=23
E: DEVNAME=/dev/tty23
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:23

P: /devices/virtual/tty/tty24
N: tty24
S: char/4:24
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty24
E: MAJOR=4
E: MINOR=24
E: DEVNAME=/dev/tty24
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:24

P: /devices/virtual/tty/tty25
N: tty25
S: char/4:25
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty25
E: MAJOR=4
E: MINOR=25
E: DEVNAME=/dev/tty25
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:25

P: /devices/virtual/tty/tty26
N: tty26
S: char/4:26
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty26
E: MAJOR=4
E: MINOR=26
E: DEVNAME=/dev/tty26
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:26

P: /devices/virtual/tty/tty27
N: tty27
S: char/4:27
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty27
E: MAJOR=4
E: MINOR=27
E: DEVNAME=/dev/tty27
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:27

P: /devices/virtual/tty/tty28
N: tty28
S: char/4:28
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty28
E: MAJOR=4
E: MINOR=28
E: DEVNAME=/dev/tty28
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:28

P: /devices/virtual/tty/tty29
N: tty29
S: char/4:29
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty29
E: MAJOR=4
E: MINOR=29
E: DEVNAME=/dev/tty29
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:29

P: /devices/virtual/tty/tty3
N: tty3
S: char/4:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty3
E: MAJOR=4
E: MINOR=3
E: DEVNAME=/dev/tty3
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:3

P: /devices/virtual/tty/tty30
N: tty30
S: char/4:30
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty30
E: MAJOR=4
E: MINOR=30
E: DEVNAME=/dev/tty30
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:30

P: /devices/virtual/tty/tty31
N: tty31
S: char/4:31
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty31
E: MAJOR=4
E: MINOR=31
E: DEVNAME=/dev/tty31
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:31

P: /devices/virtual/tty/tty32
N: tty32
S: char/4:32
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty32
E: MAJOR=4
E: MINOR=32
E: DEVNAME=/dev/tty32
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:32

P: /devices/virtual/tty/tty33
N: tty33
S: char/4:33
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty33
E: MAJOR=4
E: MINOR=33
E: DEVNAME=/dev/tty33
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:33

P: /devices/virtual/tty/tty34
N: tty34
S: char/4:34
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty34
E: MAJOR=4
E: MINOR=34
E: DEVNAME=/dev/tty34
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:34

P: /devices/virtual/tty/tty35
N: tty35
S: char/4:35
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty35
E: MAJOR=4
E: MINOR=35
E: DEVNAME=/dev/tty35
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:35

P: /devices/virtual/tty/tty36
N: tty36
S: char/4:36
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty36
E: MAJOR=4
E: MINOR=36
E: DEVNAME=/dev/tty36
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:36

P: /devices/virtual/tty/tty37
N: tty37
S: char/4:37
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty37
E: MAJOR=4
E: MINOR=37
E: DEVNAME=/dev/tty37
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:37

P: /devices/virtual/tty/tty38
N: tty38
S: char/4:38
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty38
E: MAJOR=4
E: MINOR=38
E: DEVNAME=/dev/tty38
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:38

P: /devices/virtual/tty/tty39
N: tty39
S: char/4:39
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty39
E: MAJOR=4
E: MINOR=39
E: DEVNAME=/dev/tty39
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:39

P: /devices/virtual/tty/tty4
N: tty4
S: char/4:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty4
E: MAJOR=4
E: MINOR=4
E: DEVNAME=/dev/tty4
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:4

P: /devices/virtual/tty/tty40
N: tty40
S: char/4:40
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty40
E: MAJOR=4
E: MINOR=40
E: DEVNAME=/dev/tty40
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:40

P: /devices/virtual/tty/tty41
N: tty41
S: char/4:41
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty41
E: MAJOR=4
E: MINOR=41
E: DEVNAME=/dev/tty41
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:41

P: /devices/virtual/tty/tty42
N: tty42
S: char/4:42
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty42
E: MAJOR=4
E: MINOR=42
E: DEVNAME=/dev/tty42
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:42

P: /devices/virtual/tty/tty43
N: tty43
S: char/4:43
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty43
E: MAJOR=4
E: MINOR=43
E: DEVNAME=/dev/tty43
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:43

P: /devices/virtual/tty/tty44
N: tty44
S: char/4:44
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty44
E: MAJOR=4
E: MINOR=44
E: DEVNAME=/dev/tty44
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:44

P: /devices/virtual/tty/tty45
N: tty45
S: char/4:45
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty45
E: MAJOR=4
E: MINOR=45
E: DEVNAME=/dev/tty45
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:45

P: /devices/virtual/tty/tty46
N: tty46
S: char/4:46
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty46
E: MAJOR=4
E: MINOR=46
E: DEVNAME=/dev/tty46
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:46

P: /devices/virtual/tty/tty47
N: tty47
S: char/4:47
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty47
E: MAJOR=4
E: MINOR=47
E: DEVNAME=/dev/tty47
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:47

P: /devices/virtual/tty/tty48
N: tty48
S: char/4:48
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty48
E: MAJOR=4
E: MINOR=48
E: DEVNAME=/dev/tty48
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:48

P: /devices/virtual/tty/tty49
N: tty49
S: char/4:49
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty49
E: MAJOR=4
E: MINOR=49
E: DEVNAME=/dev/tty49
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:49

P: /devices/virtual/tty/tty5
N: tty5
S: char/4:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty5
E: MAJOR=4
E: MINOR=5
E: DEVNAME=/dev/tty5
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:5

P: /devices/virtual/tty/tty50
N: tty50
S: char/4:50
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty50
E: MAJOR=4
E: MINOR=50
E: DEVNAME=/dev/tty50
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:50

P: /devices/virtual/tty/tty51
N: tty51
S: char/4:51
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty51
E: MAJOR=4
E: MINOR=51
E: DEVNAME=/dev/tty51
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:51

P: /devices/virtual/tty/tty52
N: tty52
S: char/4:52
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty52
E: MAJOR=4
E: MINOR=52
E: DEVNAME=/dev/tty52
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:52

P: /devices/virtual/tty/tty53
N: tty53
S: char/4:53
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty53
E: MAJOR=4
E: MINOR=53
E: DEVNAME=/dev/tty53
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:53

P: /devices/virtual/tty/tty54
N: tty54
S: char/4:54
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty54
E: MAJOR=4
E: MINOR=54
E: DEVNAME=/dev/tty54
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:54

P: /devices/virtual/tty/tty55
N: tty55
S: char/4:55
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty55
E: MAJOR=4
E: MINOR=55
E: DEVNAME=/dev/tty55
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:55

P: /devices/virtual/tty/tty56
N: tty56
S: char/4:56
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty56
E: MAJOR=4
E: MINOR=56
E: DEVNAME=/dev/tty56
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:56

P: /devices/virtual/tty/tty57
N: tty57
S: char/4:57
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty57
E: MAJOR=4
E: MINOR=57
E: DEVNAME=/dev/tty57
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:57

P: /devices/virtual/tty/tty58
N: tty58
S: char/4:58
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty58
E: MAJOR=4
E: MINOR=58
E: DEVNAME=/dev/tty58
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:58

P: /devices/virtual/tty/tty59
N: tty59
S: char/4:59
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty59
E: MAJOR=4
E: MINOR=59
E: DEVNAME=/dev/tty59
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:59

P: /devices/virtual/tty/tty6
N: tty6
S: char/4:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty6
E: MAJOR=4
E: MINOR=6
E: DEVNAME=/dev/tty6
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:6

P: /devices/virtual/tty/tty60
N: tty60
S: char/4:60
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty60
E: MAJOR=4
E: MINOR=60
E: DEVNAME=/dev/tty60
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:60

P: /devices/virtual/tty/tty61
N: tty61
S: char/4:61
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty61
E: MAJOR=4
E: MINOR=61
E: DEVNAME=/dev/tty61
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:61

P: /devices/virtual/tty/tty62
N: tty62
S: char/4:62
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty62
E: MAJOR=4
E: MINOR=62
E: DEVNAME=/dev/tty62
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:62

P: /devices/virtual/tty/tty63
N: tty63
S: char/4:63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty63
E: MAJOR=4
E: MINOR=63
E: DEVNAME=/dev/tty63
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:63

P: /devices/virtual/tty/tty7
N: tty7
S: char/4:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty7
E: MAJOR=4
E: MINOR=7
E: DEVNAME=/dev/tty7
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:7

P: /devices/virtual/tty/tty8
N: tty8
S: char/4:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty8
E: MAJOR=4
E: MINOR=8
E: DEVNAME=/dev/tty8
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:8

P: /devices/virtual/tty/tty9
N: tty9
S: char/4:9
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty9
E: MAJOR=4
E: MINOR=9
E: DEVNAME=/dev/tty9
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:9

P: /devices/virtual/usbmon/usbmon0
N: usbmon0
S: char/253:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/usbmon/usbmon0
E: MAJOR=253
E: MINOR=0
E: DEVNAME=/dev/usbmon0
E: SUBSYSTEM=usbmon
E: DEVLINKS=/dev/char/253:0

P: /devices/virtual/vc/vcs
N: vcs
S: char/7:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs
E: MAJOR=7
E: MINOR=0
E: DEVNAME=/dev/vcs
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:0

P: /devices/virtual/vc/vcs1
N: vcs1
S: char/7:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs1
E: MAJOR=7
E: MINOR=1
E: DEVNAME=/dev/vcs1
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:1

P: /devices/virtual/vc/vcs2
N: vcs2
S: char/7:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs2
E: MAJOR=7
E: MINOR=2
E: DEVNAME=/dev/vcs2
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:2

P: /devices/virtual/vc/vcs3
N: vcs3
S: char/7:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs3
E: MAJOR=7
E: MINOR=3
E: DEVNAME=/dev/vcs3
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:3

P: /devices/virtual/vc/vcs4
N: vcs4
S: char/7:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs4
E: MAJOR=7
E: MINOR=4
E: DEVNAME=/dev/vcs4
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:4

P: /devices/virtual/vc/vcs5
N: vcs5
S: char/7:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs5
E: MAJOR=7
E: MINOR=5
E: DEVNAME=/dev/vcs5
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:5

P: /devices/virtual/vc/vcs6
N: vcs6
S: char/7:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs6
E: MAJOR=7
E: MINOR=6
E: DEVNAME=/dev/vcs6
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:6

P: /devices/virtual/vc/vcs7
N: vcs7
S: char/7:7
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs7
E: MAJOR=7
E: MINOR=7
E: DEVNAME=/dev/vcs7
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:7

P: /devices/virtual/vc/vcs8
N: vcs8
S: char/7:8
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcs8
E: MAJOR=7
E: MINOR=8
E: DEVNAME=/dev/vcs8
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:8

P: /devices/virtual/vc/vcsa
N: vcsa
S: char/7:128
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa
E: MAJOR=7
E: MINOR=128
E: DEVNAME=/dev/vcsa
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:128

P: /devices/virtual/vc/vcsa1
N: vcsa1
S: char/7:129
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa1
E: MAJOR=7
E: MINOR=129
E: DEVNAME=/dev/vcsa1
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:129

P: /devices/virtual/vc/vcsa2
N: vcsa2
S: char/7:130
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa2
E: MAJOR=7
E: MINOR=130
E: DEVNAME=/dev/vcsa2
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:130

P: /devices/virtual/vc/vcsa3
N: vcsa3
S: char/7:131
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa3
E: MAJOR=7
E: MINOR=131
E: DEVNAME=/dev/vcsa3
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:131

P: /devices/virtual/vc/vcsa4
N: vcsa4
S: char/7:132
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa4
E: MAJOR=7
E: MINOR=132
E: DEVNAME=/dev/vcsa4
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:132

P: /devices/virtual/vc/vcsa5
N: vcsa5
S: char/7:133
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa5
E: MAJOR=7
E: MINOR=133
E: DEVNAME=/dev/vcsa5
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:133

P: /devices/virtual/vc/vcsa6
N: vcsa6
S: char/7:134
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa6
E: MAJOR=7
E: MINOR=134
E: DEVNAME=/dev/vcsa6
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:134

P: /devices/virtual/vc/vcsa7
N: vcsa7
S: char/7:135
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa7
E: MAJOR=7
E: MINOR=135
E: DEVNAME=/dev/vcsa7
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:135

P: /devices/virtual/vc/vcsa8
N: vcsa8
S: char/7:136
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vc/vcsa8
E: MAJOR=7
E: MINOR=136
E: DEVNAME=/dev/vcsa8
E: SUBSYSTEM=vc
E: DEVLINKS=/dev/char/7:136

P: /devices/virtual/video_output/acpi_video0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/video_output/acpi_video0
E: SUBSYSTEM=video_output

P: /devices/virtual/vtconsole/vtcon0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/vtconsole/vtcon0
E: SUBSYSTEM=vtconsole

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
N: snd/controlC0
S: char/116:9
S: snd/by-path/pci-0000:00:1b.0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
E: MAJOR=116
E: MINOR=9
E: DEVNAME=/dev/snd/controlC0
E: SUBSYSTEM=sound
E: ID_PATH=pci-0000:00:1b.0
E: ACL_MANAGE=1
E: DEVLINKS=/dev/char/116:9 /dev/snd/by-path/pci-0000:00:1b.0


**dmi**

/sys/class/dmi/id/uevent:MODALIAS=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
/sys/class/dmi/id/bios_vendor:TOSHIBA
/sys/class/dmi/id/bios_version:V2.20
/sys/class/dmi/id/bios_date:06/04/2009
/sys/class/dmi/id/sys_vendor:TOSHIBA
/sys/class/dmi/id/product_name:Qosmio F50
/sys/class/dmi/id/product_version:PQF55E-046012AR
/sys/class/dmi/id/board_vendor:TOSHIBA
/sys/class/dmi/id/board_name:JSKAA
/sys/class/dmi/id/board_version:1.00
/sys/class/dmi/id/chassis_vendor:TOSHIBA
/sys/class/dmi/id/chassis_type:10
/sys/class/dmi/id/chassis_version:N/A         
/sys/class/dmi/id/chassis_asset_tag:*
/sys/class/dmi/id/modalias:dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:

**sysfs-attributes**

P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
A: modalias=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
A: uniq=
A: phys=LNXPWRBN/button/input0
A: name=Power Button

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:03/input/input5
A: modalias=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw
A: uniq=
A: phys=/video/input0
A: name=Video Bus

P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C0A:00/power_supply/BAT1
A: status=Charging
A: type=Battery
A: alarm=0
A: charge_full=4000000
A: voltage_now=11100000
A: current_now=0
A: charge_now=1400000
A: serial_number=3658Q
A: voltage_min_design=11100000
A: manufacturer=TOSHIBA
A: technology=Li-ion
A: model_name=PA3534U
A: present=1
A: charge_full_design=4000000

P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
A: modalias=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
A: uniq=
A: phys=PNP0C0C/button/input0
A: name=Power Button

P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
A: modalias=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
A: uniq=
A: phys=PNP0C0D/button/input0
A: name=Lid Switch

P: /devices/pci0000:00/0000:00:00.0
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002A40sv00001179sd0000FF00bc06sc00i00
A: irq=0
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2a40
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:01.0
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d00002A41sv00000000sd00000000bc06sc04i00
A: irq=24
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2a41
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060400
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
A: subsystem_device=0xff00
A: boot_vga=1
A: vendor=0x10de
A: modalias=pci:v000010DEd0000062Asv00001179sd0000FF00bc03sc00i00
A: irq=11
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x062a
A: resource=0x00000000ce000000 0x00000000ceffffff 0x0000000000020200
A: class=0x030000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1a.0
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002937sv00001179sd0000FF00bc0Csc03i00
A: irq=16
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2937
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1a.0/usb3
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=3
A: serial=0000:00:1a.0
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=22
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1a.1
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002938sv00001179sd0000FF00bc0Csc03i00
A: irq=21
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2938
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1a.1/usb4
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=4
A: serial=0000:00:1a.1
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=22
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1a.2
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002939sv00001179sd0000FF00bc0Csc03i00
A: irq=19
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2939
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1a.2/usb5
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=5
A: serial=0000:00:1a.2
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=23
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1a.7
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d0000293Csv00001179sd0000FF00bc0Csc03i20
A: irq=19
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x293c
A: resource=0x00000000f2504800 0x00000000f2504bff 0x0000000000020200
A: companion=
A: class=0x0c0320
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1a.7/usb1
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0002
A: bNumInterfaces=1
A: busnum=1
A: serial=0000:00:1a.7
A: speed=480
A: version=2.00
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=EHCI Host Controller
A: urbnum=32
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic ehci_hcd
A: bcdDevice=0206
A: maxchild=6

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6
A: idVendor=04f2
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=02
A: bMaxPower=500mA
A: idProduct=b008
A: bNumInterfaces=2
A: busnum=1
A: serial=SN0001
A: speed=480
A: version=2.00
A: authorized=1
A: quirks=0x0
A: bDeviceClass=ef
A: devnum=2
A: product=Chicony USB 2.0 Camera
A: urbnum=17
A: bDeviceProtocol=01
A: bmAttributes=80
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Chicony Electronics Co., Ltd.
A: bcdDevice=0335
A: maxchild=0

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0
A: iad_bInterfaceCount=02
A: iad_bFirstInterface=00
A: bAlternateSetting=0
A: iad_bFunctionSubClass=03
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=01
A: modalias=usb:v04F2pB008d0335dcEFdsc02dp01ic0Eisc01ip00
A: bInterfaceClass=0e
A: bNumEndpoints=01
A: iad_bFunctionProtocol=00
A: interface=Chicony USB 2.0 Camera
A: supports_autosuspend=1
A: iad_bFunctionClass=0e

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7
A: modalias=input:b0003v04F2pB008e0335-e0,1,kD4,ramlsfw
A: uniq=
A: phys=usb-0000:00:1a.7-6/button
A: name=Chicony USB 2.0 Camera

P: /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.1
A: iad_bInterfaceCount=02
A: iad_bFirstInterface=00
A: bAlternateSetting=0
A: iad_bFunctionSubClass=03
A: bInterfaceNumber=01
A: bInterfaceProtocol=00
A: bInterfaceSubClass=02
A: modalias=usb:v04F2pB008d0335dcEFdsc02dp01ic0Eisc02ip00
A: bInterfaceClass=0e
A: bNumEndpoints=00
A: iad_bFunctionProtocol=00
A: supports_autosuspend=1
A: iad_bFunctionClass=0e

P: /devices/pci0000:00/0000:00:1b.0
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d0000293Esv00001179sd0000FF00bc04sc03i00
A: irq=22
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x293e
A: resource=0x00000000f2500000 0x00000000f2503fff 0x0000000000120204
A: class=0x040300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1b.0/input/input10
A: modalias=input:b0001v10ECp0272e0001-e0,12,kramls1,2,fw
A: uniq=
A: phys=card0/codec#0/beep0
A: name=HDA Digital PCBeep

P: /devices/pci0000:00/0000:00:1b.0/sound/card0
A: id=Intel
A: number=0

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/adsp

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/audio

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/dsp

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
A: user_pin_configs=
A: afg=0x1
A: mfg=0x0
A: vendor_id=0x10ec0272
A: subsystem_id=0x1179ff76
A: init_pin_configs=0x11 0x411111f0
A: hints=
A: modelname=
A: revision_id=0x100001
A: vendor_name=Realtek
A: driver_pin_configs=
A: chip_name=ALC272
A: init_verbs=

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D1
A: user_pin_configs=
A: afg=0x0
A: mfg=0x1
A: vendor_id=0x11c11040
A: subsystem_id=0x11790001
A: init_pin_configs=
A: hints=
A: modelname=
A: revision_id=0x100200
A: vendor_name=LSI
A: driver_pin_configs=
A: chip_name=ID 1040
A: init_verbs=

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/mixer

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
A: pcm_class=generic

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
A: pcm_class=generic

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
A: pcm_class=generic

P: /devices/pci0000:00/0000:00:1c.0
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d00002940sv00000000sd00000000bc06sc04i00
A: irq=25
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2940
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060400
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:1c.2
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d00002944sv00000000sd00000000bc06sc04i00
A: irq=26
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2944
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060400
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:1c.2/0000:0e:00.0
A: subsystem_device=0xff00
A: vendor=0x10ec
A: modalias=pci:v000010ECd00008168sv00001179sd0000FF00bc02sc00i00
A: irq=30
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x8168
A: resource=0x0000000000004000 0x00000000000040ff 0x0000000000020101
A: class=0x020000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1c.3
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d00002946sv00000000sd00000000bc06sc04i00
A: irq=27
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2946
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060400
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0
A: subsystem_device=0x1201
A: vendor=0x8086
A: filter_flags=0x0000
A: modalias=pci:v00008086d00004232sv00008086sd00001201bc02sc80i00
A: irq=31
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: version=fw not loaded
A: flags=0x0000
A: tx_power=off
A: numa_node=0
A: device=0x4232
A: resource=0x00000000f2100000 0x00000000f2101fff 0x0000000000120204
A: class=0x028000
A: subsystem_vendor=0x8086

P: /devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0/rfkill0
A: claim=0
A: name=phy0
A: index=0
A: persistent=0
A: state=2
A: type=wlan

P: /devices/pci0000:00/0000:00:1c.5
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d0000294Asv00000000sd00000000bc06sc04i00
A: irq=28
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x294a
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060400
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.0
A: subsystem_device=0xff00
A: vendor=0x197b
A: modalias=pci:v0000197Bd00002380sv00001179sd0000FF00bc0Csc00i10
A: irq=17
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2380
A: resource=0x00000000f2200000 0x00000000f22007ff 0x0000000000020200
A: class=0x0c0010
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.1
A: subsystem_device=0xff02
A: vendor=0x197b
A: modalias=pci:v0000197Bd00002382sv00001179sd0000FF02bc08sc80i00
A: irq=17
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2382
A: resource=0x00000000f2201400 0x00000000f22014ff 0x0000000000020200
A: class=0x088000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.2
A: subsystem_device=0xff02
A: vendor=0x197b
A: modalias=pci:v0000197Bd00002381sv00001179sd0000FF02bc08sc05i01
A: irq=17
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2381
A: resource=0x00000000f2201800 0x00000000f22018ff 0x0000000000020200
A: class=0x080501
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.3
A: subsystem_device=0xff02
A: vendor=0x197b
A: modalias=pci:v0000197Bd00002383sv00001179sd0000FF02bc08sc80i00
A: irq=17
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2383
A: resource=0x00000000f2201c00 0x00000000f2201cff 0x0000000000020200
A: class=0x088000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1c.5/0000:20:00.4
A: subsystem_device=0xff02
A: vendor=0x197b
A: modalias=pci:v0000197Bd00002384sv00001179sd0000FF02bc08sc80i00
A: irq=10
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2384
A: resource=0x00000000f2202000 0x00000000f22020ff 0x0000000000020200
A: class=0x088000
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1d.0
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002934sv00001179sd0000FF00bc0Csc03i00
A: irq=23
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2934
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1d.0/usb6
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=6
A: serial=0000:00:1d.0
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=22
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1d.1
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002935sv00001179sd0000FF00bc0Csc03i00
A: irq=19
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2935
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1d.1/usb7
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=7
A: serial=0000:00:1d.1
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=32
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1
A: idVendor=09da
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=100mA
A: idProduct=000a
A: bNumInterfaces=1
A: busnum=7
A: speed=1.5
A: version=1.10
A: authorized=1
A: quirks=0x0
A: bDeviceClass=00
A: devnum=2
A: product=USB Mouse
A: urbnum=8646
A: bDeviceProtocol=00
A: bmAttributes=a0
A: configuration=
A: bMaxPacketSize0=8
A: manufacturer=A4Tech
A: bcdDevice=0014
A: maxchild=0

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=02
A: bInterfaceSubClass=01
A: modalias=usb:v09DAp000Ad0014dc00dsc00dp00ic03isc01ip02
A: bInterfaceClass=03
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input6
A: modalias=input:b0003v09DAp000Ae0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,6,8,9,am4,lsfw
A: uniq=
A: phys=usb-0000:00:1d.1-1/input0
A: name=A4Tech USB Mouse

P: /devices/pci0000:00/0000:00:1d.2
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002936sv00001179sd0000FF00bc0Csc03i00
A: irq=18
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x2936
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x0c0300
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1d.2/usb8
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0001
A: bNumInterfaces=1
A: busnum=8
A: serial=0000:00:1d.2
A: speed=12
A: version=1.10
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=UHCI Host Controller
A: urbnum=22
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic uhci_hcd
A: bcdDevice=0206
A: maxchild=2

P: /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1d.7
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d0000293Asv00001179sd0000FF00bc0Csc03i20
A: irq=23
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: pools=poolinfo - 0.1
A: numa_node=0
A: device=0x293a
A: resource=0x00000000f2504c00 0x00000000f2504fff 0x0000000000020200
A: companion=
A: class=0x0c0320
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1d.7/usb2
A: idVendor=1d6b
A: bConfigurationValue=1
A: bNumConfigurations=1
A: bDeviceSubClass=00
A: bMaxPower=0mA
A: idProduct=0002
A: bNumInterfaces=1
A: busnum=2
A: serial=0000:00:1d.7
A: speed=480
A: version=2.00
A: authorized=1
A: quirks=0x0
A: authorized_default=1
A: bDeviceClass=09
A: devnum=1
A: product=EHCI Host Controller
A: urbnum=47
A: bDeviceProtocol=00
A: bmAttributes=e0
A: configuration=
A: bMaxPacketSize0=64
A: manufacturer=Linux 2.6.31-14-generic ehci_hcd
A: bcdDevice=0206
A: maxchild=6

P: /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
A: bAlternateSetting=0
A: bInterfaceNumber=00
A: bInterfaceProtocol=00
A: bInterfaceSubClass=00
A: modalias=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
A: bInterfaceClass=09
A: bNumEndpoints=01
A: supports_autosuspend=1

P: /devices/pci0000:00/0000:00:1e.0
A: subsystem_device=0x0000
A: vendor=0x8086
A: modalias=pci:v00008086d00002448sv00000000sd00000000bc06sc04i01
A: irq=0
A: msi_bus=1
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2448
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060401
A: subsystem_vendor=0x0000

P: /devices/pci0000:00/0000:00:1f.0
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002919sv00001179sd0000FF00bc06sc01i00
A: irq=0
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2919
A: resource=0x0000000000000000 0x0000000000000000 0x0000000000000000
A: class=0x060100
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1f.2
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002929sv00001179sd0000FF00bc01sc06i01
A: irq=29
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2929
A: resource=0x00000000000018f0 0x00000000000018f7 0x0000000000020101
A: class=0x010601
A: subsystem_vendor=0x1179

P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
A: iocounterbits=32
A: vendor=ATA
A: modalias=scsi:t-0x00
A: queue_depth=31
A: evt_media_change=0
A: rev=FF01
A: iorequest_cnt=0x1f57
A: iodone_cnt=0x1e8a
A: state=running
A: device_blocked=0
A: timeout=30
A: unload_heads=0
A: ioerr_cnt=0xd
A: model=TOSHIBA MK4058GS
A: type=0
A: queue_type=simple
A: scsi_level=6

P: /devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
A: iocounterbits=32
A: vendor=ATA
A: modalias=scsi:t-0x00
A: queue_depth=31
A: evt_media_change=0
A: rev=LV01
A: iorequest_cnt=0x129
A: iodone_cnt=0x129
A: state=running
A: device_blocked=0
A: timeout=30
A: unload_heads=0
A: ioerr_cnt=0xd
A: model=TOSHIBA MK3252GS
A: type=0
A: queue_type=simple
A: scsi_level=6

P: /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
A: iocounterbits=32
A: vendor=PIONEER
A: modalias=scsi:t-0x05
A: queue_depth=1
A: evt_media_change=0
A: rev=1.54
A: iorequest_cnt=0x723
A: iodone_cnt=0x18b
A: state=running
A: device_blocked=0
A: timeout=30
A: ioerr_cnt=0x0
A: model=DVD-RW  DVRTD08A
A: type=5
A: queue_type=none
A: scsi_level=6

P: /devices/pci0000:00/0000:00:1f.3
A: subsystem_device=0xff00
A: vendor=0x8086
A: modalias=pci:v00008086d00002930sv00001179sd0000FF00bc0Csc05i00
A: irq=10
A: msi_bus=
A: local_cpulist=0-1
A: broken_parity_status=0
A: local_cpus=00000000,00000003
A: numa_node=0
A: device=0x2930
A: resource=0x00000000be100000 0x00000000be1000ff 0x0000000000120204
A: class=0x0c0500
A: subsystem_vendor=0x1179

P: /devices/platform/i8042/serio0
A: bind_mode=auto
A: set=2
A: description=i8042 KBD port
A: extra=0
A: modalias=serio:ty06pr00id00ex00
A: softraw=1
A: softrepeat=0
A: err_count=0
A: scroll=0

P: /devices/platform/i8042/serio0/input/input4
A: modalias=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw
A: uniq=
A: phys=isa0060/serio0/input0
A: name=AT Translated Set 2 keyboard

P: /devices/platform/i8042/serio1
A: bind_mode=auto
A: protocol=AlpsPS/2
A: description=i8042 AUX port
A: resetafter=5
A: modalias=serio:ty01pr00id00ex00
A: resync_time=0
A: rate=100
A: resolution=200

P: /devices/platform/i8042/serio1/input/input8
A: modalias=input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw
A: uniq=
A: phys=isa0060/serio1/input1
A: name=PS/2 Mouse

P: /devices/platform/i8042/serio1/input/input9
A: modalias=input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw
A: uniq=
A: phys=isa0060/serio1/input0
A: name=AlpsPS/2 ALPS GlidePoint

P: /devices/pnp0/00:00
A: options=
A: resources=state = active
A: id=PNP0a08

P: /devices/pnp0/00:01
A: options=
A: resources=state = active
A: id=PNP0200

P: /devices/pnp0/00:02
A: options=
A: resources=state = active
A: id=PNP0103

P: /devices/pnp0/00:03
A: options=
A: resources=state = active
A: id=PNP0c04

P: /devices/pnp0/00:04
A: options=
A: resources=state = active
A: id=PNP0c02

P: /devices/pnp0/00:05
A: options=
A: resources=state = active
A: id=PNP0b00

P: /devices/pnp0/00:06
A: options=
A: resources=state = active
A: id=PNP0303

P: /devices/pnp0/00:07
A: options=
A: resources=state = active
A: id=PNP0f13

P: /devices/pnp0/00:08
A: options=
A: resources=state = active
A: id=PNP0c02

P: /devices/virtual/dmi/id
A: sys_vendor=TOSHIBA
A: board_asset_tag=
A: chassis_type=10
A: modalias=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
A: bios_vendor=TOSHIBA
A: product_version=PQF55E-046012AR
A: board_name=JSKAA
A: board_version=1.00
A: bios_date=06/04/2009
A: chassis_asset_tag=*
A: bios_version=V2.20
A: chassis_vendor=TOSHIBA
A: product_name=Qosmio F50
A: chassis_version=N/A
A: board_vendor=TOSHIBA

P: /devices/virtual/dmi/id/bios
A: sys_vendor=TOSHIBA
A: board_asset_tag=
A: chassis_type=10
A: modalias=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
A: bios_vendor=TOSHIBA
A: product_version=PQF55E-046012AR
A: board_name=JSKAA
A: board_version=1.00
A: bios_date=06/04/2009
A: chassis_asset_tag=*
A: bios_version=V2.20
A: chassis_vendor=TOSHIBA
A: product_name=Qosmio F50
A: chassis_version=N/A
A: board_vendor=TOSHIBA

P: /devices/virtual/dmi/id/board
A: sys_vendor=TOSHIBA
A: board_asset_tag=
A: chassis_type=10
A: modalias=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
A: bios_vendor=TOSHIBA
A: product_version=PQF55E-046012AR
A: board_name=JSKAA
A: board_version=1.00
A: bios_date=06/04/2009
A: chassis_asset_tag=*
A: bios_version=V2.20
A: chassis_vendor=TOSHIBA
A: product_name=Qosmio F50
A: chassis_version=N/A
A: board_vendor=TOSHIBA

P: /devices/virtual/dmi/id/chassis
A: sys_vendor=TOSHIBA
A: board_asset_tag=
A: chassis_type=10
A: modalias=dmi:bvnTOSHIBA:bvrV2.20:bd06/04/2009:svnTOSHIBA:pnQosmioF50:pvrPQF55E-046012AR:rvnTOSHIBA:rnJSKAA:rvr1.00:cvnTOSHIBA:ct10:cvrN/A:
A: bios_vendor=TOSHIBA
A: product_version=PQF55E-046012AR
A: board_name=JSKAA
A: board_version=1.00
A: bios_date=06/04/2009
A: chassis_asset_tag=*
A: bios_version=V2.20
A: chassis_vendor=TOSHIBA
A: product_name=Qosmio F50
A: chassis_version=N/A
A: board_vendor=TOSHIBA

P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
**Processors**

 **0**

    Property Value  bogomips 4788   cache 3145728   count 2   model Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz   model_number 6   model_revision 6   model_version 23   other fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm  constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx  est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority    platform x86_64   speed 2401   type GenuineIntel  **1**

    Property Value  bogomips 4788   cache 3145728   count 2   model Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz   model_number 6   model_revision 6   model_version 23   other fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov  pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm  constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx  est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority    platform x86_64   speed 2401   type GenuineIntel  [Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **Packages**

    Name Version  acpi-support 0.129   acpid 1.0.6-9ubuntu8   adduser 3.110ubuntu6   aisleriot 1:2.28.0-0ubuntu1   alacarte 0.12.4-0ubuntu2   alsa-base 1.0.20+dfsg-1ubuntu5   alsa-utils 1.0.20-2ubuntu6   anacron 2.3-13.1ubuntu10   app-install-data 0.9.10.11   app-install-data-partner 12.9.10   apparmor 2.3.1+1403-0ubuntu27   apparmor-utils 2.3.1+1403-0ubuntu27   apport 1.9.3-0ubuntu4   apport-gtk 1.9.3-0ubuntu4   apport-symptoms 0.2   apt 0.7.23.1ubuntu2   apt-transport-https 0.7.23.1ubuntu2   apt-utils 0.7.23.1ubuntu2   apt-xapian-index 0.21ubuntu2   aptdaemon 0.10+bzr264-0ubuntu1   aptitude 0.4.11.11-1ubuntu6   apturl 0.4.1ubuntu2   apturl-common 0.4.1ubuntu2   aspell 0.60.6-2   aspell-en 6.0-0-5.1ubuntu3   at 3.1.11-1ubuntu4   at-spi 1.28.1-0ubuntu1   avahi-autoipd 0.6.25-1ubuntu5   avahi-daemon 0.6.25-1ubuntu5   base-files 5.0.0ubuntu7   base-passwd 3.5.21   bash 4.0-5ubuntu2   bash-completion 1:1.0-3ubuntu2   bc 1.06.94-3.1ubuntu2   bcmwl-modaliases 5.10.91.9+bdcom-0ubuntu4   bind9-host 1:9.6.1.dfsg.P1-3   binfmt-support 1.2.14   binutils 2.20-0ubuntu1   bluetooth 4.51-0ubuntu2   bluez 4.51-0ubuntu2   bluez-alsa 4.51-0ubuntu2   bluez-cups 4.51-0ubuntu2   bluez-gstreamer 4.51-0ubuntu2   bluez-utils 4.51-0ubuntu2   bogofilter 1.2.0-3ubuntu1   bogofilter-bdb 1.2.0-3ubuntu1   bogofilter-common 1.2.0-3ubuntu1   brasero 2.28.1-0ubuntu1   brltty 4.0-7ubuntu2   brltty-x11 4.0-7ubuntu2   bsdmainutils 6.1.10ubuntu4   bsdutils 1:2.16-1ubuntu5   busybox-initramfs 1:1.13.3-1ubuntu7   byobu 2.38-0ubuntu3   bzip2 1.0.5-3   ca-certificates 20090814   capplets-data 1:2.28.1-0ubuntu1   cdparanoia 3.10.2+debian-5   checkbox 0.8.5   checkbox-gtk 0.8.5   cli-common 0.7   command-not-found 0.2.38ubuntu4   command-not-found-data 0.2.38ubuntu4   compiz 1:0.8.4-0ubuntu2   compiz-core 1:0.8.4-0ubuntu2   compiz-fusion-plugins-extra 0.8.4-0ubuntu2   compiz-fusion-plugins-main 0.8.4-0ubuntu1   compiz-gnome 1:0.8.4-0ubuntu2   compiz-plugins 1:0.8.4-0ubuntu2   compiz-wrapper 1:0.8.4-0ubuntu2   compizconfig-backend-gconf 0.8.4-0ubuntu1   computer-janitor 1.13.3-0ubuntu2   computer-janitor-gtk 1.13.3-0ubuntu2   console-setup 1.34ubuntu4   console-terminus 4.28-1   consolekit 0.3.1-0ubuntu2   coreutils 7.4-2ubuntu1   couchdb-bin 0.10.0-0ubuntu3   cpio 2.10-1ubuntu1   cpp 4:4.4.1-1ubuntu2   cpp-4.4 4.4.1-4ubuntu8   cron 3.0pl1-106ubuntu3   cups 1.4.1-5ubuntu2   cups-bsd 1.4.1-5ubuntu2   cups-client 1.4.1-5ubuntu2   cups-common 1.4.1-5ubuntu2   cups-driver-gutenprint 5.2.4-0ubuntu2   dash 0.5.5.1-2ubuntu3   dbus 1.2.16-0ubuntu9   dbus-x11 1.2.16-0ubuntu9   dc 1.06.94-3.1ubuntu2   dcraw 8.86-1   debconf 1.5.27ubuntu2   debconf-i18n 1.5.27ubuntu2   debianutils 2.30ubuntu3   defoma 0.11.10-0.2ubuntu1   desktop-file-utils 0.15-2ubuntu1   desktopcouch 0.5-0ubuntu1   devicekit-disks 007-2ubuntu3   devicekit-power 011-1ubuntu1   dhcp3-client 3.1.2-1ubuntu7   dhcp3-common 3.1.2-1ubuntu7   dictionaries-common 1.2.1ubuntu1   diff 2.8.1-13   dmidecode 2.9-1ubuntu2   dmsetup 2:1.02.27-4ubuntu7   dmz-cursor-theme 0.4.1   dnsmasq-base 2.50-1   dnsutils 1:9.6.1.dfsg.P1-3   doc-base 0.9.3   docbook-xml 4.5-6   dosfstools 3.0.3-1   dpkg 1.15.4ubuntu2   dvd+rw-tools 7.1-4   e2fslibs 1.41.9-1ubuntu3   e2fsprogs 1.41.9-1ubuntu3   ed 1.4-1   eject 2.1.5+deb1+cvs20081104-6   empathy 2.28.1-1ubuntu1   empathy-doc 2.28.1-1ubuntu1   eog 2.28.1-0ubuntu1   erlang-base 1:13.b.1-dfsg-2ubuntu1   erlang-crypto 1:13.b.1-dfsg-2ubuntu1   erlang-inets 1:13.b.1-dfsg-2ubuntu1   erlang-mnesia 1:13.b.1-dfsg-2ubuntu1   erlang-public-key 1:13.b.1-dfsg-2ubuntu1   erlang-runtime-tools 1:13.b.1-dfsg-2ubuntu1   erlang-ssl 1:13.b.1-dfsg-2ubuntu1   erlang-syntax-tools 1:13.b.1-dfsg-2ubuntu1   erlang-xmerl 1:13.b.1-dfsg-2ubuntu1   esound-clients 0.2.41-5   esound-common 0.2.41-5   espeak 1.41.01-0ubuntu1   espeak-data 1.41.01-0ubuntu1   ethtool 6+20090307-1   evince 2.28.1-0ubuntu1   evolution 2.28.1-0ubuntu1   evolution-common 2.28.1-0ubuntu1   evolution-couchdb 0.3.2-0ubuntu2   evolution-data-server 2.28.1-0ubuntu1   evolution-data-server-common 2.28.1-0ubuntu1   evolution-documentation-en 2.28.1-0ubuntu1   evolution-exchange 2.28.1-0ubuntu1   evolution-indicator 0.2.4-0ubuntu2   evolution-plugins 2.28.1-0ubuntu1   evolution-webcal 2.28.0-0ubuntu1   example-content 38   f-spot 0.6.1.3-2   fglrx-modaliases 2:8.660-0ubuntu4   file 5.03-1ubuntu1   file-roller 2.28.1-0ubuntu1   findutils 4.4.2-1   finger 0.17-13   firefox 3.5.3+build1+nobinonly-0ubuntu6   firefox-3.5 3.5.3+build1+nobinonly-0ubuntu6   firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu6   firefox-3.5-gnome-support 3.5.3+build1+nobinonly-0ubuntu6   firefox-gnome-support 3.5.3+build1+nobinonly-0ubuntu6   fontconfig 2.6.0-1ubuntu12   fontconfig-config 2.6.0-1ubuntu12   foo2zjs 20090623-0ubuntu5   foomatic-db 20090825-0ubuntu4   foomatic-db-engine 4.0.3-0ubuntu2   foomatic-filters 4.0.3-0ubuntu2   friendly-recovery 0.2.8.2   ftp 0.17-19   fuse-utils 2.7.4-1.1ubuntu4   gamin 0.1.10-1ubuntu2   gcalctool 5.28.1-0ubuntu1   gcc 4:4.4.1-1ubuntu2   gcc-4.4 4.4.1-4ubuntu8   gcc-4.4-base 4.4.1-4ubuntu8   gconf-defaults-service 2.28.0-0ubuntu2   gconf-editor 2.28.0-0ubuntu1   gconf2 2.28.0-0ubuntu2   gconf2-common 2.28.0-0ubuntu2   gdb 7.0-0ubuntu1   gdebi 0.5.9   gdebi-core 0.5.9   gdm 2.28.1-0ubuntu1   gdm-guest-session 0.14   gedit 2.28.0-0ubuntu2   gedit-common 2.28.0-0ubuntu2   genisoimage 9:1.1.9-1ubuntu2   geoip-database 1.4.6.dfsg-5   gettext-base 0.17-8ubuntu2   ggzcore-bin 0.0.14.1-1ubuntu1   ghostscript 8.70.dfsg.1-0ubuntu3   ghostscript-cups 8.70.dfsg.1-0ubuntu3   ghostscript-x 8.70.dfsg.1-0ubuntu3   gimp 2.6.7-1ubuntu1   gimp-data 2.6.7-1ubuntu1   gksu 2.0.2-2ubuntu1   glchess 1:2.28.0-0ubuntu1   glines 1:2.28.0-0ubuntu1   gnect 1:2.28.0-0ubuntu1   gnibbles 1:2.28.0-0ubuntu1   gnobots2 1:2.28.0-0ubuntu1   gnome-about 1:2.28.1-0ubuntu2   gnome-accessibility-themes 2.28.1-0ubuntu1   gnome-applets 2.28.0-0ubuntu2   gnome-applets-data 2.28.0-0ubuntu2   gnome-blackjack 1:2.28.0-0ubuntu1   gnome-bluetooth 2.28.1-0ubuntu2   gnome-codec-install 0.4.1ubuntu1   gnome-control-center 1:2.28.1-0ubuntu1   gnome-desktop-data 1:2.28.1-0ubuntu2   gnome-disk-utility 2.28.0+git20091012-0ubuntu1   gnome-doc-utils 0.18.0-0ubuntu1   gnome-games 1:2.28.0-0ubuntu1   gnome-games-common 1:2.28.0-0ubuntu1   gnome-icon-theme 2.28.0-0ubuntu1   gnome-keyring 2.28.1-0ubuntu1   gnome-mag 1:0.15.9-0ubuntu1   gnome-mahjongg 1:2.28.0-0ubuntu1   gnome-media 2.28.1-0ubuntu1   gnome-media-common 2.28.1-0ubuntu1   gnome-menus 2.28.0.1-0ubuntu1   gnome-mime-data 2.18.0-1   gnome-nettool 2.28.0-0ubuntu1   gnome-orca 2.28.1-0ubuntu1   gnome-panel 1:2.28.0-0ubuntu6   gnome-panel-data 1:2.28.0-0ubuntu6   gnome-pilot 2.0.17-0ubuntu2   gnome-pilot-conduits 2.0.15-1.2   gnome-power-manager 2.28.1-0ubuntu1   gnome-screensaver 2.28.0-0ubuntu3   gnome-session 2.28.0-0ubuntu5   gnome-session-bin 2.28.0-0ubuntu5   gnome-session-canberra 0.15-0ubuntu7   gnome-settings-daemon 2.28.1-0ubuntu1   gnome-sudoku 1:2.28.0-0ubuntu1   gnome-system-monitor 2.28.0-0ubuntu1   gnome-system-tools 2.28.1-0ubuntu2   gnome-terminal 2.28.1-0ubuntu1   gnome-terminal-data 2.28.1-0ubuntu1   gnome-themes-selected 2.28.1-0ubuntu1   gnome-themes-ubuntu 0.5.1   gnome-user-guide 2.28.0+git20090921ubuntu2   gnome-utils 2.28.1-0ubuntu1   gnometris 1:2.28.0-0ubuntu1   gnomine 1:2.28.0-0ubuntu1   gnotravex 1:2.28.0-0ubuntu1   gnotski 1:2.28.0-0ubuntu1   gnupg 1.4.9-4ubuntu7   gpgv 1.4.9-4ubuntu7   grep 2.5.4-4   groff-base 1.20.1-5   grub-common 1.97~beta4-1ubuntu3   grub-pc 1.97~beta4-1ubuntu3   gsfonts 1:8.11+urwcyr1.0.7~pre44-4   gstreamer0.10-alsa 0.10.25-2ubuntu1   gstreamer0.10-nice 0.0.9-2   gstreamer0.10-plugins-base 0.10.25-2ubuntu1   gstreamer0.10-plugins-base-apps 0.10.25-2ubuntu1   gstreamer0.10-plugins-good 0.10.16-1ubuntu3   gstreamer0.10-pulseaudio 0.10.16-1ubuntu3   gstreamer0.10-tools 0.10.25-2   gstreamer0.10-x 0.10.25-2ubuntu1   gtali 1:2.28.0-0ubuntu1   gtk2-engines 1:2.18.4-1ubuntu1   gtk2-engines-murrine 0.90.3-1ubuntu1   gtk2-engines-pixbuf 2.18.3-1   gucharmap 1:2.28.0-0ubuntu1   guile-1.8-libs 1.8.7+1-1ubuntu3   gvfs 1.4.1-0ubuntu1   gvfs-backends 1.4.1-0ubuntu1   gvfs-bin 1.4.1-0ubuntu1   gvfs-fuse 1.4.1-0ubuntu1   gzip 1.3.12-8ubuntu1   hal 0.5.13-1ubuntu8   hal-info 20090716-0ubuntu1   hdparm 9.15-1ubuntu4   hicolor-icon-theme 0.10-2   hostname 2.95ubuntu1   hpijs 3.9.8-1ubuntu2   hplip 3.9.8-1ubuntu2   hplip-data 3.9.8-1ubuntu2   human-theme 0.37   humanity-icon-theme 0.4.1ubuntu5   hunspell-en-us 20070829-2ubuntu4   iagno 1:2.28.0-0ubuntu1   ibus 1.2.0.20090927-2ubuntu1   ibus-gtk 1.2.0.20090927-2ubuntu1   ibus-m17n 1.2.0.20090930-1   ibus-table 1.2.0.20090625-1   ifupdown 0.6.8ubuntu21   im-switch 1.16ubuntu1   indicator-applet 0.2.0-0ubuntu2   indicator-applet-session 0.2.0-0ubuntu2   indicator-messages 0.2.6-0ubuntu1   indicator-session 0.1.7-0ubuntu3   info 4.13a.dfsg.1-4ubuntu1   initramfs-tools 0.92bubuntu53   initscripts 2.87dsf-4ubuntu11   inputattach 1.23-0ubuntu3   insserv 1.12.0-11   install-info 4.13a.dfsg.1-4ubuntu1   iproute 20090324-1   iptables 1.4.4-1ubuntu1   iputils-arping 3:20071127-1build1   iputils-ping 3:20071127-1build1   iputils-tracepath 3:20071127-1build1   iso-codes 3.10.2-1   jockey-common 0.5.5-0ubuntu2   jockey-gtk 0.5.5-0ubuntu2   kbd 1.15-1ubuntu1   kerneloops-daemon 0.12+git20090217-1ubuntu4   klibc-utils 1.5.15-1ubuntu2   language-pack-en 1:9.10+20091022   language-pack-en-base 1:9.10+20091022   language-pack-gnome-en 1:9.10+20091022   language-pack-gnome-en-base 1:9.10+20091022   language-selector 0.4.18   language-selector-common 0.4.18   language-support-en 1:9.10+20090909   language-support-writing-en 1:9.10+20090909   laptop-detect 0.13.7ubuntu1   laptop-mode-tools 1.47-1ubuntu2   latex-xft-fonts 0.1-8   launchpad-integration 0.1.26   less 429-2   lftp 3.7.15-1ubuntu2   libaa1 1.4p5-38   libacl1 2.2.47-2   libanthy0 9100h-0ubuntu1   libapparmor-perl 2.3.1+1403-0ubuntu27   libapparmor1 2.3.1+1403-0ubuntu27   libarchive1 2.6.2-1   libart-2.0-2 2.3.20-2   libart2.0-cil 2.24.1-4ubuntu1   libasound2 1.0.20-3ubuntu6   libasound2-plugins 1.0.20-1ubuntu8   libaspell15 0.60.6-2   libatasmart4 0.16-1   libatk1.0-0 1.28.0-0ubuntu1   libatk1.0-data 1.28.0-0ubuntu1   libatm1 2.4.1-17.2   libatspi1.0-0 1.28.1-0ubuntu1   libattr1 1:2.4.43-3   libaudiofile0 0.2.6-7ubuntu2   libavahi-client3 0.6.25-1ubuntu5   libavahi-common-data 0.6.25-1ubuntu5   libavahi-common3 0.6.25-1ubuntu5   libavahi-core6 0.6.25-1ubuntu5   libavahi-glib1 0.6.25-1ubuntu5   libavahi-gobject0 0.6.25-1ubuntu5   libavahi-ui0 0.6.25-1ubuntu5   libavc1394-0 0.5.3-1build3   libbabl-0.0-0 0.0.22-1   libbeagle1 0.3.9-1   libbind9-50 1:9.6.1.dfsg.P1-3   libblkid1 2.16-1ubuntu5   libbluetooth3 4.51-0ubuntu2   libbonobo2-0 2.24.2-1   libbonobo2-common 2.24.2-1   libbonoboui2-0 2.24.2-1ubuntu2   libbonoboui2-common 2.24.2-1ubuntu2   libbrasero-media0 2.28.1-0ubuntu1   libbrlapi0.5 4.0-7ubuntu2   libbsd0 0.1.4-1   libbz2-1.0 1.0.5-3   libc-bin 2.10.1-0ubuntu15   libc-dev-bin 2.10.1-0ubuntu15   libc6 2.10.1-0ubuntu15   libc6-dev 2.10.1-0ubuntu15   libcaca0 0.99.beta16-1   libcairo-perl 1.061-1   libcairo2 1.8.8-2ubuntu1   libcairomm-1.0-1 1.8.0-1build1   libcamel1.2-14 2.28.1-0ubuntu1   libcanberra-gtk-module 0.15-0ubuntu7   libcanberra-gtk0 0.15-0ubuntu7   libcanberra-pulse 0.15-0ubuntu7   libcanberra0 0.15-0ubuntu7   libcap2 1:2.16-5ubuntu1   libcdio-cdda0 0.78.2+dfsg1-3   libcdio-paranoia0 0.78.2+dfsg1-3   libcdio7 0.78.2+dfsg1-3   libcdparanoia0 3.10.2+debian-5   libck-connector0 0.3.1-0ubuntu2   libclass-accessor-perl 0.33-1   libclutter-1.0-0 1.0.6-0ubuntu1   libclutter-gtk-0.10-0 0.10.2-0ubuntu1   libcolamd2.7.1 1:3.4.0-1ubuntu2   libcomerr2 1.41.9-1ubuntu3   libcompizconfig0 0.8.4-0ubuntu1   libcompress-bzip2-perl 2.09-2   libcouchdb-glib-1.0-1 0.5.2-0ubuntu1   libcroco3 0.6.1-2   libcryptui0 2.28.1-0ubuntu1   libcups2 1.4.1-5ubuntu2   libcupscgi1 1.4.1-5ubuntu2   libcupsdriver1 1.4.1-5ubuntu2   libcupsimage2 1.4.1-5ubuntu2   libcupsmime1 1.4.1-5ubuntu2   libcupsppdc1 1.4.1-5ubuntu2   libcurl3 7.19.5-1ubuntu2   libcurl3-gnutls 7.19.5-1ubuntu2   libcwidget3 0.5.12-4ubuntu4   libdaemon0 0.13-3   libdatrie1 0.2.2-1   libdb4.7 4.7.25-7ubuntu2   libdbus-1-3 1.2.16-0ubuntu9   libdbus-glib-1-2 0.80-4ubuntu1   libdbusmenu-glib0 0.1.6-0ubuntu1   libdbusmenu-gtk0 0.1.6-0ubuntu1   libdecoration0 1:0.8.4-0ubuntu2   libdevkit-power-gobject1 011-1ubuntu1   libdevmapper1.02.1 2:1.02.27-4ubuntu7   libdirectfb-1.2-0 1.2.7-2ubuntu1   libdjvulibre-text 3.5.22-1ubuntu2   libdjvulibre21 3.5.22-1ubuntu2   libdns50 1:9.6.1.dfsg.P1-3   libdotconf1.0 1.0.13-2ubuntu1   libdrm-intel1 2.4.14-1ubuntu1   libdrm-radeon1 2.4.14-1ubuntu1   libdrm2 2.4.14-1ubuntu1   libdv4 1.0.0-2ubuntu1   libebackend1.2-0 2.28.1-0ubuntu1   libebook1.2-9 2.28.1-0ubuntu1   libecal1.2-7 2.28.1-0ubuntu1   libedata-book1.2-2 2.28.1-0ubuntu1   libedata-cal1.2-6 2.28.1-0ubuntu1   libedataserver1.2-11 2.28.1-0ubuntu1   libedataserverui1.2-8 2.28.1-0ubuntu1   libedit2 2.11-20080614-1   libeggdbus-1-0 0.5-1   libegroupwise1.2-13 2.28.1-0ubuntu1   libelf1 0.141-2ubuntu2   libempathy-common 2.28.1-1ubuntu1   libempathy-gtk-common 2.28.1-1ubuntu1   libempathy-gtk28 2.28.1-1ubuntu1   libempathy30 2.28.1-1ubuntu1   libenchant1c2a 1.5.0-0ubuntu2   libept0 0.5.26ubuntu3   libesd-alsa0 0.2.41-5   libespeak1 1.41.01-0ubuntu1   libevdocument1 2.28.1-0ubuntu1   libevent-1.4-2 1.4.11-stable-1   libevview1 2.28.1-0ubuntu1   libexchange-storage1.2-3 2.28.1-0ubuntu1   libexempi3 2.1.1-1build1   libexif12 0.6.17-1   libexpat1 2.0.1-4ubuntu1   libffi5 3.0.7-2ubuntu1   libflac8 1.2.1-2build1   libflickrnet2.2-cil 1:2.2.0-1   libfont-afm-perl 1.20-1   libfontconfig1 2.6.0-1ubuntu12   libfontenc1 1:1.0.4-3   libfreetype6 2.3.9-5   libfreezethaw-perl 0.45-1   libfribidi0 0.10.9-1build1   libfs6 2:1.0.2-1   libfuse2 2.7.4-1.1ubuntu4   libgadu3 1:1.8.0+r592-3   libgail-common 2.18.3-1   libgail-gnome-module 1.20.1-1ubuntu1   libgail18 2.18.3-1   libgamin0 0.1.10-1ubuntu2   libgc1c2 1:6.8-1.2   libgcc1 1:4.4.1-4ubuntu8   libgconf2-4 2.28.0-0ubuntu2   libgconf2.0-cil 2.24.1-4ubuntu1   libgcr0 2.28.1-0ubuntu1   libgcrypt11 1.4.4-2ubuntu2   libgd2-xpm 2.0.36~rc1~dfsg-3ubuntu1   libgdata-common 0.4.0-1   libgdata-google1.2-1 2.28.1-0ubuntu1   libgdata1.2-1 2.28.1-0ubuntu1   libgdata5 0.4.0-1   libgdbm3 1.8.3-4   libgdict-1.0-6 2.28.1-0ubuntu1   libgdiplus 2.4.2-1   libgdu-gtk0 2.28.0+git20091012-0ubuntu1   libgdu0 2.28.0+git20091012-0ubuntu1   libgegl-0.0-0 0.0.22-0ubuntu3   libgeoip1 1.4.6.dfsg-5   libggz2 0.0.14.1-1build1   libggzcore9 0.0.14.1-1ubuntu1   libggzmod4 0.0.14.1-1ubuntu1   libgif4 4.1.6-6   libgimp2.0 2.6.7-1ubuntu1   libgksu2-0 2.0.12-1ubuntu4   libgl1-mesa-dri 7.6.0-1ubuntu4   libgl1-mesa-glx 7.6.0-1ubuntu4   libglade2-0 1:2.6.4-1   libglade2.0-cil 2.12.9-1   libglib-perl 1:1.221-1   libglib2.0-0 2.22.2-0ubuntu1   libglib2.0-cil 2.12.9-1   libglib2.0-data 2.22.2-0ubuntu1   libglibmm-2.4-1c2a 2.22.1-2   libglitz-glx1 0.5.6-1   libglitz1 0.5.6-1   libglu1-mesa 7.6.0-1ubuntu4   libgmime-2.0-2a 2.2.22-4   libgmime-2.4-2 2.4.6-5   libgmime2.2a-cil 2.2.22-4   libgmp3c2 2:4.3.1+dfsg-1ubuntu3   libgnome-bluetooth7 2.28.1-0ubuntu2   libgnome-desktop-2-11 1:2.28.1-0ubuntu2   libgnome-keyring0 2.28.1-0ubuntu1   libgnome-keyring1.0-cil 1.0.0-1   libgnome-mag2 1:0.15.9-0ubuntu1   libgnome-media0 2.28.1-0ubuntu1   libgnome-menu2 2.28.0.1-0ubuntu1   libgnome-pilot2 2.0.17-0ubuntu2   libgnome-vfs2.0-cil 2.24.1-4ubuntu1   libgnome-window-settings1 1:2.28.1-0ubuntu1   libgnome2-0 2.28.0-0ubuntu3   libgnome2-canvas-perl 1.002-2   libgnome2-common 2.28.0-0ubuntu3   libgnome2-perl 1.042-2   libgnome2-vfs-perl 1.081-1   libgnome2.24-cil 2.24.1-4ubuntu1   libgnomecanvas2-0 2.26.0-1   libgnomecanvas2-common 2.26.0-1   libgnomekbd-common 2.28.0-0ubuntu2   libgnomekbd4 2.28.0-0ubuntu2   libgnomekbdui4 2.28.0-0ubuntu2   libgnomepanel2.24-cil 2.26.0-1   libgnomeui-0 2.24.2-1   libgnomeui-common 2.24.2-1   libgnomevfs2-0 1:2.24.2-1ubuntu1   libgnomevfs2-common 1:2.24.2-1ubuntu1   libgnomevfs2-extra 1:2.24.2-1ubuntu1   libgnutls26 2.8.3-2   libgomp1 4.4.1-4ubuntu8   libgp11-0 2.28.1-0ubuntu1   libgpg-error0 1.6-1ubuntu1   libgpgme11 1.1.8-2ubuntu3   libgphoto2-2 2.4.6-1ubuntu6   libgphoto2-port0 2.4.6-1ubuntu6   libgpm2 1.20.4-3.2ubuntu1   libgpod-common 0.7.2-1ubuntu1   libgpod4 0.7.2-1ubuntu1   libgraphviz4 2.20.2-3ubuntu5   libgs8 8.70.dfsg.1-0ubuntu3   libgsf-1-114 1.14.15-1ubuntu1   libgsf-1-common 1.14.15-1ubuntu1   libgsl0ldbl 1.12+dfsg-1   libgssapi-krb5-2 1.7dfsg~beta3-1   libgssdp-1.0-1 0.6.4-2   libgstfarsight0.10-0 0.0.15-1ubuntu1   libgstreamer-plugins-base0.10-0 0.10.25-2ubuntu1   libgstreamer0.10-0 0.10.25-2   libgtk-vnc-1.0-0 0.3.9-1ubuntu2   libgtk2-perl 1:1.221-4   libgtk2.0-0 2.18.3-1   libgtk2.0-bin 2.18.3-1   libgtk2.0-cil 2.12.9-1   libgtk2.0-common 2.18.3-1   libgtkhtml-editor-common 1:3.28.1-0ubuntu1   libgtkhtml-editor0 1:3.28.1-0ubuntu1   libgtkhtml2-0 2.11.1-2ubuntu2   libgtkhtml3.14-19 1:3.28.1-0ubuntu1   libgtkmm-2.4-1c2a 1:2.18.2-1   libgtksourceview2.0-0 2.8.1-1   libgtksourceview2.0-common 2.8.1-1   libgtkspell0 2.0.15-0ubuntu1   libgtop2-7 2.26.1-0ubuntu1   libgtop2-common 2.26.1-0ubuntu1   libgucharmap7 1:2.28.0-0ubuntu1   libgudev-1.0-0 1:147~-6   libgupnp-1.0-2 0.12.6-3.1   libgupnp-igd-1.0-2 0.1.3-0ubuntu3   libgutenprint2 5.2.4-0ubuntu2   libgvfscommon0 1.4.1-0ubuntu1   libgweather-common 2.28.0-1ubuntu2   libgweather1 2.28.0-1ubuntu2   libhal-storage1 0.5.13-1ubuntu8   libhal1 0.5.13-1ubuntu8   libhtml-format-perl 2.04-2   libhtml-parser-perl 3.61-1   libhtml-tagset-perl 3.20-2   libhtml-tree-perl 3.23-1   libhunspell-1.2-0 1.2.8-4ubuntu2   libhyphen0 2.4-4   libibus1 1.2.0.20090927-2ubuntu1   libical0 0.43-3   libice6 2:1.0.5-1   libicu40 4.0.1-2ubuntu2   libidl0 0.8.13-0.1   libidn11 1.15-1   libiec61883-0 1.2.0-0.1   libieee1284-3 0.2.11-5ubuntu2   libijs-0.35 0.35-7   libilmbase6 1.0.1-3build1   libindicate-gtk1 0.2.3-0ubuntu1   libindicate3 0.2.3-0ubuntu1   libio-string-perl 1.08-2   libisc50 1:9.6.1.dfsg.P1-3   libisccc50 1:9.6.1.dfsg.P1-3   libisccfg50 1:9.6.1.dfsg.P1-3   libiw29 29-2ubuntu6   libjasper1 1.900.1-6   libjpeg62 6b-14build1   libjs-jquery 1.3.3-1ubuntu1   libjson-glib-1.0-0 0.7.6-0ubuntu1   libk5crypto3 1.7dfsg~beta3-1   libkeyutils1 1.2-10   libklibc 1.5.15-1ubuntu2   libkpathsea4 2007.dfsg.2-7ubuntu1   libkrb5-3 1.7dfsg~beta3-1   libkrb5support0 1.7dfsg~beta3-1   liblaunchpad-integration1 0.1.26   liblcms1 1.18.dfsg-1ubuntu1   libldap-2.4-2 2.4.18-0ubuntu1   liblircclient0 0.8.6-0ubuntu2   liblocale-gettext-perl 1.05-4build1   liblockfile1 1.08-3   libloudmouth1-0 1.4.3-4   liblouis-data 1.7.0-1ubuntu1   liblouis0 1.7.0-1ubuntu1   liblpint-bonobo0 0.1.26   libltdl7 2.2.6a-4   liblwres50 1:9.6.1.dfsg.P1-3   libm17n-0 1.5.4-1ubuntu1   libmagic1 5.03-1ubuntu1   libmagickcore2 7:6.5.1.0-1.1ubuntu3   libmagickwand2 7:6.5.1.0-1.1ubuntu3   libmailtools-perl 2.04-1   libmeanwhile1 1.0.2-3build1   libmetacity0 1:2.28.0-0ubuntu1   libmldbm-perl 2.01-2   libmng1 1.0.9-1build1   libmono-addins-gui0.2-cil 0.4-5   libmono-addins0.2-cil 0.4-5   libmono-cairo2.0-cil 2.4.2.3+dfsg-2   libmono-corlib2.0-cil 2.4.2.3+dfsg-2   libmono-data-tds2.0-cil 2.4.2.3+dfsg-2   libmono-i18n-west2.0-cil 2.4.2.3+dfsg-2   libmono-posix2.0-cil 2.4.2.3+dfsg-2   libmono-security2.0-cil 2.4.2.3+dfsg-2   libmono-sharpzip2.84-cil 2.4.2.3+dfsg-2   libmono-sqlite2.0-cil 2.4.2.3+dfsg-2   libmono-system-data2.0-cil 2.4.2.3+dfsg-2   libmono-system-web2.0-cil 2.4.2.3+dfsg-2   libmono-system2.0-cil 2.4.2.3+dfsg-2   libmono2.0-cil 2.4.2.3+dfsg-2   libmpfr1ldbl 2.4.1-1ubuntu1   libmtp8 0.3.7-3ubuntu2   libmusicbrainz4c2a 2.1.5-2ubuntu1   libmysqlclient16 5.1.37-1ubuntu5   libnautilus-extension1 1:2.28.1-0ubuntu1   libncurses5 5.7+20090803-2ubuntu2   libncursesw5 5.7+20090803-2ubuntu2   libndesk-dbus-glib1.0-cil 0.4.1-2   libndesk-dbus1.0-cil 0.6.0-3   libneon27-gnutls 0.28.6-1   libnet-dbus-perl 0.33.6-1build2   libnewt0.52 0.52.10-4ubuntu1   libnice0 0.0.9-2   libnl1 1.1-5   libnm-glib2 0.8~a~git.20091013t193206.679d548-0ubuntu1   libnm-util1 0.8~a~git.20091013t193206.679d548-0ubuntu1   libnotify1 0.4.5-1ubuntu1   libnspr4-0d 4.8-0ubuntu1   libnss-mdns 0.10-3ubuntu3   libnss3-1d 3.12.3.1-0ubuntu2   libntfs-3g54 1:2009.4.4-1ubuntu4   libogg0 1.1.4~dfsg-1   liboil0.3 0.3.16-1ubuntu1   liboobs-1-4 2.22.2-0ubuntu1   libopenexr6 1.6.1-4ubuntu3   libopenobex1 1.5-2   liborbit2 1:2.14.17-0.1   libotf0 0.9.9-1   libpam-ck-connector 0.3.1-0ubuntu2   libpam-gnome-keyring 2.28.1-0ubuntu1   libpam-modules 1.1.0-2ubuntu1   libpam-runtime 1.1.0-2ubuntu1   libpam0g 1.1.0-2ubuntu1   libpanel-applet2-0 1:2.28.0-0ubuntu6   libpango-perl 1.220-1   libpango1.0-0 1.26.0-1   libpango1.0-common 1.26.0-1   libpangomm-1.4-1 2.26.0-0ubuntu2   libpaper-utils 1.1.23+nmu1   libpaper1 1.1.23+nmu1   libparse-debianchangelog-perl 1.1.1-2ubuntu1   libparted1.8-12 1.8.8.git.2009.06.03-1ubuntu6   libpcap0.8 1.0.0-2ubuntu1   libpci3 1:3.0.0-4ubuntu13   libpciaccess0 0.10.6-2ubuntu1   libpcre3 7.8-3   libpcsclite1 1.5.3-1ubuntu1   libperl5.10 5.10.0-24ubuntu4   libpisock9 0.12.4-3ubuntu1   libpisync1 0.12.4-3ubuntu1   libpixman-1-0 0.14.0-1   libpng12-0 1.2.37-1   libpolkit-agent-1-0 0.94-1ubuntu1   libpolkit-backend-1-0 0.94-1ubuntu1   libpolkit-gobject-1-0 0.94-1ubuntu1   libpolkit-gtk-1-0 0.94-1+1git.230873   libpoppler-glib4 0.12.0-0ubuntu2   libpoppler5 0.12.0-0ubuntu2   libpopt0 1.14-4   libportaudio2 19+svn20090620-0ubuntu1   libpq5 8.4.1-1   libprotobuf3 2.0.3-2.2ubuntu2   libproxy0 0.2.3-0ubuntu5   libpst4 0.6.41-0ubuntu2   libpth20 2.0.7-12   libpulse-browse0 1:0.9.19-0ubuntu4   libpulse-mainloop-glib0 1:0.9.19-0ubuntu4   libpulse0 1:0.9.19-0ubuntu4   libpurple-bin 1:2.6.2-1ubuntu7   libpurple0 1:2.6.2-1ubuntu7   libpython2.6 2.6.4~rc2-0ubuntu1   libraptor1 1.4.19-1   librarian0 0.8.1-2ubuntu3   librasqal1 0.9.16-1   libraw1394-11 2.0.4-1ubuntu1   librdf0 1.0.9-2   libreadline6 6.0-5   librpc-xml-perl 0.64-1   librsvg2-2 2.26.0-1   librsvg2-common 2.26.0-1   libsamplerate0 0.1.7-2   libsane 1.0.20-4ubuntu3   libsasl2-2 2.1.23.dfsg1-1ubuntu3   libsasl2-modules 2.1.23.dfsg1-1ubuntu3   libsctp1 1.0.10+dfsg-1   libsdl1.2debian 1.2.13-4ubuntu4   libsdl1.2debian-alsa 1.2.13-4ubuntu4   libselinux1 2.0.85-2ubuntu2   libsensors3 1:2.10.8-1   libsepol1 2.0.37-1   libsexy2 0.1.11-2build1   libsgutils2-2 1.27-0.1   libshout3 2.2.2-5ubuntu1   libsigc++-2.0-0c2a 2.0.18-2   libsilc-1.1-2 1.1.10-2   libsilcclient-1.1-3 1.1.10-2   libslang2 2.1.4-3   libslp1 1.2.1-7.5   libsm6 2:1.1.0-2   libsmbclient 2:3.4.0-3ubuntu5   libsndfile1 1.0.20-1ubuntu1   libsnmp-base 5.4.1~dfsg-12ubuntu7   libsnmp15 5.4.1~dfsg-12ubuntu7   libsoup-gnome2.4-1 2.28.1-2   libsoup2.4-1 2.28.1-2   libspectre1 0.2.2.ds-2   libspeechd2 0.6.7+git20090914~unofficial-0ubuntu4   libspeex1 1.2~rc1-1   libspeexdsp1 1.2~rc1-1   libsqlite0 2.8.17-6build1   libsqlite3-0 3.6.16-1ubuntu1   libss2 1.41.9-1ubuntu3   libssl0.9.8 0.9.8g-16ubuntu3   libstartup-notification0 0.10-1   libstdc++6 4.4.1-4ubuntu8   libsub-name-perl 0.04-1   libsysfs2 2.1.0-5   libtag1-vanilla 1.6-2ubuntu2   libtag1c2a 1.6-2ubuntu2   libtalloc1 1.4.0~git20090718-1   libtasn1-3 2.2-1   libtdb1 1.1.5-1   libtelepathy-farsight0 0.0.11-2   libtelepathy-glib0 0.9.0-1   libterm-readkey-perl 2.30-4   libtext-charwidth-perl 0.04-5build1   libtext-iconv-perl 1.7-1build1   libtext-wrapi18n-perl 0.06-7   libthai-data 0.1.12-1   libthai0 0.1.12-1   libtheora0 1.0-2.1build1   libtie-ixhash-perl 1.21-2   libtiff4 3.8.2-13   libtimedate-perl 1.1600-9   libtotem-plparser12 2.28.1-1   libtrackerclient0 0.6.95-1ubuntu3   libts-0.0-0 1.0-7   libudev0 147~-6   libunique-1.0-0 1.1.2-1ubuntu1   liburi-perl 1.37+dfsg-1ubuntu1   libusb-0.1-4 2:0.1.12-13   libusplash0 0.5.49   libuuid-perl 0.02-3build1   libuuid1 2.16-1ubuntu5   libv4l-0 0.6.0-1   libvisual-0.4-0 0.4.0-2.1+ubuntu1   libvisual-0.4-plugins 0.4.0.dfsg.1-2ubuntu5   libvorbis0a 1.2.0.dfsg-6   libvorbisenc2 1.2.0.dfsg-6   libvorbisfile3 1.2.0.dfsg-6   libvte-common 1:0.22.2-0ubuntu2   libvte9 1:0.22.2-0ubuntu2   libwavpack1 4.50.1-1   libwbclient0 2:3.4.0-3ubuntu5   libwebkit-1.0-2 1.1.15.2-1   libwebkit-1.0-common 1.1.15.2-1   libwmf0.2-7 0.2.8.4-6.1ubuntu1   libwmf0.2-7-gtk 0.2.8.4-6.1ubuntu1   libwnck-common 1:2.28.0-0ubuntu1   libwnck22 1:2.28.0-0ubuntu1   libwpd8c2a 0.8.14-1   libwpg-0.1-1 0.1.3-1   libwps-0.1-1 0.1.2-1   libwrap0 7.6.q-16   libwww-perl 5.831-1   libx11-6 2:1.2.2-1ubuntu1   libx11-data 2:1.2.2-1ubuntu1   libx86-1 1.1+ds1-4   libxapian15 1.0.15-2ubuntu2   libxau6 1:1.0.4-2   libxaw7 2:1.0.6-1   libxcb-atom1 0.3.6-1   libxcb-aux0 0.3.6-1   libxcb-event1 0.3.6-1   libxcb-render-util0 0.3.6-1   libxcb-render0 1.4-1   libxcb1 1.4-1   libxcomposite1 1:0.4.0-4   libxcursor1 1:1.1.9-1build1   libxdamage1 1:1.1.1-4   libxdmcp6 1:1.0.2-3   libxext6 2:1.0.99.1-0ubuntu4   libxfixes3 1:4.0.3-2build1   libxfont1 1:1.4.0-1ubuntu1   libxft2 2.1.13-3ubuntu1   libxi6 2:1.2.1-2ubuntu1   libxinerama1 2:1.0.3-2   libxkbfile1 1:1.0.5-1ubuntu2   libxklavier15 4.0-0ubuntu5   libxml-parser-perl 2.36-1.1build2   libxml-twig-perl 1:3.32-3ubuntu1   libxml-xpath-perl 1.13-6   libxml2 2.7.5.dfsg-1ubuntu1   libxml2-utils 2.7.5.dfsg-1ubuntu1   libxmu6 2:1.0.4-2   libxmuu1 2:1.0.4-2   libxp6 1:1.0.0.xsf1-2   libxpm4 1:3.5.7-2   libxrandr2 2:1.3.0-2   libxrender1 1:0.9.4-2ubuntu1   libxres1 2:1.0.3-2   libxslt1.1 1.1.24-2ubuntu2   libxss1 1:1.1.3-1   libxt6 1:1.0.5-3ubuntu1   libxtrap6 2:1.0.0-5build1   libxtst6 2:1.0.3-1ubuntu2   libxv1 2:1.0.4-1   libxvmc1 2:1.0.4-2ubuntu2   libxxf86dga1 2:1.0.2-1build1   libxxf86misc1 1:1.0.1-3   libxxf86vm1 1:1.0.2-1ubuntu1   libzephyr4 3.0~rc.2544-1   linux-firmware 1.24   linux-generic 2.6.31.14.27   linux-headers-2.6.31-14 2.6.31-14.48   linux-headers-2.6.31-14-generic 2.6.31-14.48   linux-headers-generic 2.6.31.14.27   linux-image-2.6.31-14-generic linux   linux-image-generic 2.6.31.14.27   linux-libc-dev 2.6.31-14.48   linux-sound-base 1.0.20+dfsg-1ubuntu5   lksctp-tools 1.0.10+dfsg-1   locales 2.9+git20090617-3   lockfile-progs 0.1.13   login 1:4.1.4.1-1ubuntu2   logrotate 3.7.8-4ubuntu1   lp-solve 5.5.0.13-6   lsb-base 4.0-0ubuntu5   lsb-release 4.0-0ubuntu5   lshw 02.14-1   lsof 4.81.dfsg.1-1   ltrace 0.5.3-2ubuntu2   lzma 4.43-14ubuntu1   m17n-contrib 1.1.9-1   m17n-db 1.5.4-1   make 3.81-6   makedev 2.3.1-88   man-db 2.5.6-2   manpages 3.21-1   mawk 1.3.3-15ubuntu1   media-player-info 3-0ubuntu1   memtest86+ 2.11-3ubuntu5   mesa-utils 7.6.0-1ubuntu4   metacity 1:2.28.0-0ubuntu1   metacity-common 1:2.28.0-0ubuntu1   mime-support 3.46-1ubuntu1   min12xxw 0.0.9-3ubuntu1   mlocate 0.21.1-2   mobile-broadband-provider-info 20091009-0ubuntu1   modemmanager 0.2.git.20091014t233208.16f3e00-0ubuntu1   module-init-tools 3.10-3   mono-2.0-gac 2.4.2.3+dfsg-2   mono-gac 2.4.2.3+dfsg-2   mono-runtime 2.4.2.3+dfsg-2   mount 2.16-1ubuntu5   mountall 1.0   mousetweaks 2.28.1-0ubuntu1   mscompress 0.3-3   mtools 4.0.10-1   mtr-tiny 0.75-2   myspell-en-au 2.1-3.1   myspell-en-gb 1:3.0.1-8ubuntu1   myspell-en-za 1:3.0.1-8ubuntu1   mysql-common 5.1.37-1ubuntu5   nano 2.0.9-2   nautilus 1:2.28.1-0ubuntu1   nautilus-data 1:2.28.1-0ubuntu1   nautilus-sendto 2.28.0-0ubuntu1   nautilus-share 0.7.2-12   ncurses-base 5.7+20090803-2ubuntu2   ncurses-bin 5.7+20090803-2ubuntu2   net-tools 1.60-23ubuntu1   netbase 4.35ubuntu2   netcat 1.10-38   netcat-traditional 1.10-38   network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1   network-manager-gnome 0.8~a~git.20091014t134532.4033e62-0ubuntu1   notify-osd 0.9.24-0ubuntu1   notify-osd-icons 0.3   ntfs-3g 1:2009.4.4-1ubuntu4   ntpdate 1:4.2.4p6+dfsg-1ubuntu5   nvidia-173-modaliases 173.14.20-0ubuntu5   nvidia-185-modaliases 185.18.36-0ubuntu9   nvidia-96-modaliases 96.43.13-0ubuntu6   nvidia-common 0.2.15   obex-data-server 0.4.4-2build1   obexd-client 0.14-0ubuntu1   onboard 0.92.0-0ubuntu3   openoffice.org-base-core 1:3.1.1-5ubuntu1   openoffice.org-calc 1:3.1.1-5ubuntu1   openoffice.org-common 1:3.1.1-5ubuntu1   openoffice.org-core 1:3.1.1-5ubuntu1   openoffice.org-draw 1:3.1.1-5ubuntu1   openoffice.org-emailmerge 1:3.1.1-5ubuntu1   openoffice.org-gnome 1:3.1.1-5ubuntu1   openoffice.org-gtk 1:3.1.1-5ubuntu1   openoffice.org-help-en-us 1:3.1.1-4ubuntu1   openoffice.org-hyphenation 0.3   openoffice.org-hyphenation-en-us 2.4-4   openoffice.org-impress 1:3.1.1-5ubuntu1   openoffice.org-math 1:3.1.1-5ubuntu1   openoffice.org-style-human 1:3.1.1-5ubuntu1   openoffice.org-thesaurus-en-au 2.1-3.1   openoffice.org-thesaurus-en-us 1:3.0.1-8ubuntu1   openoffice.org-writer 1:3.1.1-5ubuntu1   openprinting-ppds 20090825-0ubuntu4   openssh-client 1:5.1p1-6ubuntu2   openssl 0.9.8g-16ubuntu3   os-prober 1.35   parted 1.8.8.git.2009.06.03-1ubuntu6   passwd 1:4.1.4.1-1ubuntu2   pciutils 1:3.0.0-4ubuntu13   pcmciautils 014-4ubuntu3   perl 5.10.0-24ubuntu4   perl-base 5.10.0-24ubuntu4   perl-modules 5.10.0-24ubuntu4   pkg-config 0.22-1build1   pm-utils 1.2.5-2ubuntu7   pnm2ppa 1.12-16.2ubuntu2   policykit-1 0.94-1ubuntu1   policykit-1-gnome 0.94-1+1git.230873   poppler-utils 0.12.0-0ubuntu2   popularity-contest 1.48ubuntu1   powermgmt-base 1.30+nmu1   ppp 2.4.5~git20081126t100229-0ubuntu2   pppconfig 2.3.18ubuntu2   pppoeconf 1.18ubuntu1   procps 1:3.2.8-1ubuntu3   protobuf-compiler 2.0.3-2.2ubuntu2   psfontmgr 0.11.10-0.2ubuntu1   psmisc 22.7-1   pulseaudio 1:0.9.19-0ubuntu4   pulseaudio-esound-compat 1:0.9.19-0ubuntu4   pulseaudio-module-bluetooth 1:0.9.19-0ubuntu4   pulseaudio-module-gconf 1:0.9.19-0ubuntu4   pulseaudio-module-udev 1:0.9.19-0ubuntu4   pulseaudio-module-x11 1:0.9.19-0ubuntu4   pulseaudio-utils 1:0.9.19-0ubuntu4   pxljr 1.1-0ubuntu7   python 2.6.4~rc1-0ubuntu1   python-apport 1.9.3-0ubuntu4   python-apt 0.7.13.2ubuntu4   python-aptdaemon 0.10+bzr264-0ubuntu1   python-aptdaemon-gtk 0.10+bzr264-0ubuntu1   python-avahi 0.6.25-1ubuntu5   python-brlapi 4.0-7ubuntu2   python-cairo 1.8.6-1ubuntu1   python-central 0.6.11ubuntu9   python-configglue 0.2dev-0ubuntu2   python-couchdb 0.6-1   python-crypto 2.0.1+dfsg1-4ubuntu1   python-cups 1.9.46-0ubuntu2   python-cupshelpers 1.1.12+git20090826-0ubuntu8   python-dbus 0.83.0-1ubuntu2   python-debian 0.1.14ubuntu1   python-desktopcouch 0.5-0ubuntu1   python-desktopcouch-records 0.5-0ubuntu1   python-fstab 1.4-0ubuntu1   python-gconf 2.28.0-0ubuntu1   python-gdbm 2.6.3-0ubuntu1   python-glade2 2.16.0-0ubuntu1   python-gmenu 2.28.0.1-0ubuntu1   python-gnome2 2.28.0-0ubuntu1   python-gnomeapplet 2.28.0-0ubuntu1   python-gnomecanvas 2.28.0-0ubuntu1   python-gnomekeyring 2.28.0-0ubuntu1   python-gnupginterface 0.3.2-9ubuntu2   python-gobject 2.18.0-0ubuntu2   python-gst0.10 0.10.17-1   python-gtk2 2.16.0-0ubuntu1   python-gtkhtml2 2.25.3-3ubuntu1   python-gtksourceview2 2.8.0-1   python-httplib2 0.4.0-0ubuntu2   python-ibus 1.2.0.20090927-2ubuntu1   python-imaging 1.1.6-3ubuntu1   python-launchpad-integration 0.1.26   python-launchpadlib 1.5.1-0ubuntu1   python-lazr-restfulclient 0.9.3-0ubuntu3   python-lazr-uri 1.0-0ubuntu1   python-libxml2 2.7.5.dfsg-1ubuntu1   python-louis 1.7.0-1ubuntu1   python-minimal 2.6.4~rc1-0ubuntu1   python-newt 0.52.10-4ubuntu1   python-notify 0.1.1-2build2   python-oauth 1.0a~svn1124-0ubuntu2   python-openssl 0.9-1   python-pam 0.4.2-12ubuntu3   python-papyon 0.4.3-1ubuntu1   python-pkg-resources 0.6c9-0ubuntu5   python-problem-report 1.9.3-0ubuntu4   python-protobuf 2.0.3-2.2ubuntu2   python-pyatspi 1.28.1-0ubuntu1   python-pyinotify 0.8.6-2ubuntu2   python-pyorbit 2.24.0-0ubuntu3   python-rdflib 2.4.0-5ubuntu1   python-rsvg 2.28.0-0ubuntu1   python-serial 2.3-1   python-sexy 0.1.9-1ubuntu2   python-simplejson 2.0.9-1   python-smbc 1.0.6-0ubuntu2   python-software-properties 0.75.4   python-speechd 0.6.7+git20090914~unofficial-0ubuntu4   python-support 1.0.3ubuntu1   python-telepathy 0.15.11-1   python-twisted-bin 8.2.0-3   python-twisted-core 8.2.0-3   python-twisted-names 8.2.0-1ubuntu2   python-twisted-web 8.2.0-2ubuntu1   python-ubuntuone-client 1.0.2-0ubuntu1   python-ubuntuone-storageprotocol 1.0.0-0ubuntu1   python-uno 1:3.1.1-5ubuntu1   python-virtkey 0.50ubuntu2   python-vte 1:0.22.2-0ubuntu2   python-wadllib 1.1.2-0ubuntu1   python-webkit 1.1.5-1   python-xapian 1.0.14-1build1   python-xdg 0.15-1.1ubuntu5   python-xkit 0.4.2   python-zope.interface 3.5.2-1   python2.6 2.6.4~rc2-0ubuntu1   python2.6-minimal 2.6.4~rc2-0ubuntu1   radeontool 1.5+git76606164-0ubuntu2   raptor-utils 1.4.19-1   rarian-compat 0.8.1-2ubuntu3   rdesktop 1.6.0-2ubuntu2   readline-common 6.0-5   redland-utils 1.0.9-2   rhythmbox 0.12.5-0ubuntu4   rsync 3.0.6-1ubuntu1   rsyslog 4.2.0-2ubuntu5   samba-common 2:3.4.0-3ubuntu5   samba-common-bin 2:3.4.0-3ubuntu5   same-gnome 1:2.28.0-0ubuntu1   sane-utils 1.0.20-4ubuntu3   screen 4.0.3-13ubuntu4   screen-resolution-extra 0.11   screensaver-default-images 0.2-1   seahorse 2.28.1-0ubuntu1   sed 4.2.1-1   sgml-base 1.26   sgml-data 2.0.3   shared-mime-info 0.70-0ubuntu1   smartdimmer 0.8b4-1ubuntu2   smbclient 2:3.4.0-3ubuntu5   software-center 1.0.2   software-properties-gtk 0.75.4   speech-dispatcher 0.6.7+git20090914~unofficial-0ubuntu4   splix 2.0.0-2ubuntu2   sreadahead 1.0-5   ssh-askpass-gnome 1:5.1p1-6ubuntu2   ssl-cert 1.0.23ubuntu2   strace 4.5.18-1ubuntu2   sudo 1.7.0-1ubuntu2   synaptic 0.62.7ubuntu6   syslinux 2:3.63+dfsg-2ubuntu3   system-config-printer-common 1.1.12+git20090826-0ubuntu8   system-config-printer-gnome 1.1.12+git20090826-0ubuntu8   system-config-printer-udev 1.1.12+git20090826-0ubuntu8   system-tools-backends 2.8.2-1   sysv-rc 2.87dsf-4ubuntu11   sysvinit-utils 2.87dsf-4ubuntu11   tar 1.22-1   tasksel 2.73ubuntu23   tasksel-data 2.73ubuntu23   tcl8.4 8.4.19-3   tcpd 7.6.q-16   tcpdump 4.0.0-2ubuntu2   telepathy-butterfly 0.5.2-0ubuntu1   telepathy-gabble 0.8.7-1   telepathy-haze 0.3.2-1   telepathy-idle 0.1.5-1   telepathy-mission-control-5 5.3.1-1   telepathy-salut 0.3.10-1   telnet 0.17-36   time 1.7-23   tk8.4 8.4.19-3   tomboy 1.0.0-0ubuntu2   toshset 1.75-1   totem 2.28.1-0ubuntu4   totem-common 2.28.1-0ubuntu4   totem-mozilla 2.28.1-0ubuntu4   totem-plugins 2.28.1-0ubuntu4   transmission-common 1.75-0ubuntu2   transmission-gtk 1.75-0ubuntu2   tsclient 0.150-2ubuntu2   tsconf 1.0-7   ttf-dejavu-core 2.29-2   ttf-freefont 20090104-2   ttf-indic-fonts-core 1:0.5.4ubuntu2   ttf-kacst 2.0+mry-1   ttf-lao 0.0.20060226-2   ttf-opensymbol 1:3.1.1-5ubuntu1   ttf-thai-tlwg 1:0.4.13-1ubuntu1   ttf-unfonts-core 1.0.1-7ubuntu1   ttf-vlgothic 20090612-2   ttf-wqy-zenhei 0.8.38-1ubuntu1   tzdata 2009o-1ubuntu2   ubufox 0.8-0ubuntu1   ubuntu-artwork 51   ubuntu-desktop 1.175   ubuntu-docs 9.10.11   ubuntu-keyring 2009.08.28   ubuntu-minimal 1.175   ubuntu-sounds 0.12   ubuntu-standard 1.175   ubuntu-system-service 0.1.16   ubuntu-wallpapers 0.30   ubuntu-xsplash-artwork 0.8.4-0ubuntu1   ubuntuone-client 1.0.2-0ubuntu1   ubuntuone-client-gnome 1.0.2-0ubuntu1   ucf 3.0018ubuntu1   udev 147~-6   ufw 0.29-4ubuntu1   unattended-upgrades 0.52ubuntu1   uno-libs3 1.5.1+OOo3.1.1-5ubuntu1   unzip 6.0-1   update-inetd 4.31   update-manager 1:0.126.6   update-manager-core 1:0.126.6   update-notifier 0.90   update-notifier-common 0.90   upstart 0.6.3-10   ure 1.5.1+OOo3.1.1-5ubuntu1   usb-creator-common 0.2.12   usb-creator-gtk 0.2.12   usbutils 0.82-0ubuntu1   usplash 0.5.49   usplash-theme-ubuntu 0.27   util-linux 2.16-1ubuntu5   uuid-runtime 2.16-1ubuntu5   vbetool 1.1-2   vim-common 2:7.2.245-2ubuntu2   vim-tiny 2:7.2.245-2ubuntu2   vinagre 2.28.1-0ubuntu1   vino 2.28.1-0ubuntu2   w3m 0.5.2-2ubuntu1   wamerican 6-3   wbritish 6-3   wget 1.11.4-2ubuntu2   whiptail 0.52.10-4ubuntu1   whois 4.7.34ubuntu2   wireless-crda 1.10   wireless-tools 29-2ubuntu6   wodim 9:1.1.9-1ubuntu2   wpasupplicant 0.6.9-3ubuntu1   x-ttcidfont-conf 32   x11-apps 7.4+2   x11-common 1:7.4+3ubuntu7   x11-session-utils 7.3+1build1   x11-utils 7.4+1build1   x11-xfs-utils 7.4+1build1   x11-xkb-utils 7.4+3   x11-xserver-utils 7.4+2ubuntu3   xauth 1:1.0.3-2   xbitmaps 1.0.1-2ubuntu1   xcursor-themes 1.0.1-5ubuntu1   xdg-user-dirs 0.11-0ubuntu2   xdg-user-dirs-gtk 0.8-1   xdg-utils 1.0.2-6.1   xfonts-100dpi 1:1.0.0-4build1   xfonts-75dpi 1:1.0.0-4build1   xfonts-base 1:1.0.0-6   xfonts-encodings 1:1.0.2-3   xfonts-mathml 2   xfonts-scalable 1:1.0.0-7   xfonts-utils 1:7.4+1ubuntu1   xinit 1.1.1-1   xinput 1.4.2-1   xkb-data 1.6-1ubuntu5   xml-core 0.12   xorg 1:7.4+3ubuntu7   xorg-docs-core 1:1.4-5   xsane 0.996-2ubuntu1   xsane-common 0.996-2ubuntu1   xscreensaver-data 5.08-0ubuntu5   xscreensaver-gl 5.08-0ubuntu5   xserver-common 2:1.6.4-2ubuntu4   xserver-xorg 1:7.4+3ubuntu7   xserver-xorg-core 2:1.6.4-2ubuntu4   xserver-xorg-input-all 1:7.4+3ubuntu7   xserver-xorg-input-evdev 1:2.2.5-1ubuntu6   xserver-xorg-input-mouse 1:1.4.0-2   xserver-xorg-input-synaptics 1.1.2-1ubuntu7   xserver-xorg-input-vmmouse 1:12.6.4-1ubuntu3   xserver-xorg-input-wacom 1:0.8.4.1-0ubuntu4   xserver-xorg-video-all 1:7.4+3ubuntu7   xserver-xorg-video-apm 1:1.2.1-2   xserver-xorg-video-ark 1:0.7.1-2   xserver-xorg-video-ati 1:6.12.99+git20090929.7968e1fb-0ubuntu1   xserver-xorg-video-chips 1:1.2.1-3   xserver-xorg-video-cirrus 1:1.3.1-1ubuntu2   xserver-xorg-video-fbdev 1:0.4.0-4   xserver-xorg-video-i128 1:1.3.2-1   xserver-xorg-video-intel 2:2.9.0-1ubuntu2   xserver-xorg-video-mach64 6.8.2-1   xserver-xorg-video-mga 1:1.4.11.dfsg-1   xserver-xorg-video-neomagic 1:1.2.3-1   xserver-xorg-video-nv 1:2.1.14-2ubuntu3   xserver-xorg-video-openchrome 1:0.2.903+svn758-0ubuntu1   xserver-xorg-video-r128 6.8.1-1   xserver-xorg-video-radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1   xserver-xorg-video-rendition 1:4.2.1-1   xserver-xorg-video-s3 1:0.6.2-1   xserver-xorg-video-s3virge 1:1.10.2-2   xserver-xorg-video-savage 1:2.3.0-1ubuntu1   xserver-xorg-video-siliconmotion 1:1.7.2-1   xserver-xorg-video-sis 1:0.10.1-2   xserver-xorg-video-sisusb 1:0.9.1-1   xserver-xorg-video-tdfx 1:1.4.1-1   xserver-xorg-video-trident 1:1.3.1-1   xserver-xorg-video-tseng 1:1.2.1-1   xserver-xorg-video-v4l 1:0.2.0-3ubuntu1   xserver-xorg-video-vesa 1:2.2.1-1   xserver-xorg-video-vmware 1:10.16.7-1   xserver-xorg-video-voodoo 1:1.2.2-1   xsltproc 1.1.24-2ubuntu2   xsplash 0.8.4-0ubuntu1   xterm 243-1ubuntu1   xulrunner-1.9.1 1.9.1.3+build1+nobinonly-0ubuntu6   xulrunner-1.9.1-gnome-support 1.9.1.3+build1+nobinonly-0ubuntu6   yelp 2.28.0-0ubuntu2   zenity 2.28.0-0ubuntu2   zip 3.0-1ubuntu1   zlib1g 1:1.2.3.3.dfsg-13ubuntu3  [Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **Questions**

    Name Answer Comment  internet pass  
 network pass  
 modem pass  
[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **Contextual Information**

 **cat /proc/asound/card*/codec#***

Codec: Realtek ALC272
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0272
Subsystem Id: 0x1179ff76
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x30 0x30]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Connection: 2
     0x02 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a11c30: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x99a30950: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x5, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40168a2d: [N/A] Speaker at Ext N/A
    Conn = Digital, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x02451120: [Jack] SPDIF Out at Ext Front
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x80
  Coefficient Index: 0x06
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221141f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x11790001
Revision Id: 0x100200
Modem Function Group: 0x1

[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **cat /proc/cpuinfo**

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2401.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4787.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2401.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4788.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **dmidecode**

/dev/mem: Permission denied

[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **lspci -vvnn**

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 1800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 19
	Region 4: I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at f2504800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: be000000-be0fffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f20fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=14, subordinate=14, sec-latency=0
	Memory behind bridge: f2100000-f21fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
	Memory behind bridge: f2200000-f22fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f2504c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=26, subordinate=26, sec-latency=0
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 29
	Region 0: I/O ports at 18f0 [size=8]
	Region 1: I/O ports at 18e4 [size=4]
	Region 2: I/O ports at 18e8 [size=8]
	Region 3: I/O ports at 18e0 [size=4]
	Region 4: I/O ports at 18c0 [size=32]
	Region 5: Memory at f2504000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 10
	Region 0: Memory at be100000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: nVidia Corporation G94 [GeForce 9700M GTS] [10de:062a] (rev a1)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 30
	Region 0: I/O ports at 4000 [size=256]
	Region 2: Memory at f2010000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f2000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f2020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

14:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation Device [8086:1201]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 31
	Region 0: Memory at f2100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

20:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380] (prog-if 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f2200000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at f2201000 (32-bit, non-prefetchable) [size=128]
	Region 4: Memory at f2200c00 (32-bit, non-prefetchable) [size=128]
	Region 5: Memory at f2200800 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

20:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
	Subsystem: Toshiba America Info Systems Device [1179:ff02]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f2201400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

20:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (prog-if 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff02]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f2201800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

20:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
	Subsystem: Toshiba America Info Systems Device [1179:ff02]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f2201c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

20:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
	Subsystem: Toshiba America Info Systems Device [1179:ff02]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f2202000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **find /etc/modprobe.* -name \*.conf | xargs cat**

# Uncomment these entries in order to blacklist unwanted modem drivers
# blacklist snd-atiixp-modem
# blacklist snd-intel8x0m
# blacklist snd-via82xx-modem
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
# Watchdog drivers should not be loaded automatically, but only if a
# watchdog daemon is installed.
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist booke_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i6300esb
blacklist i8xx_tco
blacklist ib700wdt
blacklist ibmasr
blacklist indydog
blacklist iTCO_wdt
blacklist it8712f_wdt
blacklist it87_wdt
blacklist ixp2000_wdt
blacklist ixp4xx_wdt
blacklist machzwd
blacklist mixcomwd
blacklist mpc8xx_wdt
blacklist mpcore_wdt
blacklist mv64x60_wdt
blacklist pc87413_wdt
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist s3c2410_wdt
blacklist sa1100_wdt
blacklist sbc60xxwdt
blacklist sbc7240_wdt
blacklist sb8360
blacklist sc1200wdt
blacklist sc520_wdt
blacklist sch311_wdt
blacklist scx200_wdt
blacklist shwdt
blacklist smsc37b787_wdt
blacklist softdog
blacklist twl4030_wdt
blacklist w83627hf_wdt
blacklist w83697hf_wdt
blacklist w83697ug_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci
blacklist wm8350_wdt
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
blacklist visor
blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb-midi
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
blacklist vesafb
blacklist vfb
blacklist vga16fb
blacklist vt8623fb

[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **cat /etc/modules**

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

[Back to Table of Contents]("http://ubuntuforums.org/#toc")
 **find /etc/sysctl.* -name \*.conf | xargs cat**

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks.
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Turn on SYN-flood protections.  Starting with 2.6.26, there is no loss
# of TCP functionality/features under normal conditions.  When flood
# protections kick in under high unanswered-SYN load, the system
# should remain more stable, with a trade off of some loss of TCP
# functionality/features (e.g. TCP Window scaling).
net.ipv4.tcp_syncookies=1

[Back to Table of Contents]("http://ubuntuforums.org/#toc")

``` :popcorn:

---

### Post by ubun2warrior on 2010-04-11
Check your wire , the problem might be with it.

---

### Post by abdusamed on 2010-04-11
> **ubun2warrior said:**
> Check your wire , the problem might be with it.

The wire is fine because when I rebooted to windows 7, it worked fine on it. I didn't even move the wire or anything, same position as it was in ubuntu. So it ain't my wire fault.. something must be wrong

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
What does ```
sudo dhclient eth0
``` do?

---

### Post by abdusamed on 2010-04-11
> **Sin@Sin-Sacrifice said:**
> What does ```
sudo dhclient eth0
``` do?

thanks, after doing that, i got the mac address and netmask. I had to manually enter those numbers when creating a new network setting from network manager. The same thing you do when creating a static ip, thanks.. But it's weird it wasn't automactically detecting the mac address or the Ethernet default setting

---

### Post by bdaman80 on 2010-06-23
I too have this same problem as of the last couple of days.  I am on Ubuntu 10.04 64bit using Lenovo R61i Hardware.  My install is a couple of months old.

Since I set it up manually it works fine, automatically is broken.  I think it may have something to do with my last update??

What is your thoughts?

---

### Post by abdusamed on 2010-06-24
Small bugs which been in the ubuntu history for a VERY long time.... copy/paste bug, wallpaper slide show bug... loads of other

---

### Post by rad_sci_guy on 2010-06-27
> **Sin@Sin-Sacrifice said:**
> What does ```
sudo dhclient eth0
``` do?

I'm having a problem getting my wired connection to work.  When I enter that command I get

SIOCSIFADDR: no such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

I can connect with wire when running the windows 7 starter that was pre-installed on my netbook.

It looks to me the device driver isn't installed.  How do I do that?

---

### Post by heyandy889 on 2010-07-29
System-Administration-Hardware Drivers

That found drivers for my LG monitor.

I see that you are using Ubuntu 9.10. Not sure if "Hardware Drivers" is located in exactly the same place.

---

### Post by abhik117 on 2011-10-18
i am using ubuntu 10.10. and this happened to me b4..
and was cursing my router..but finally after some editing i got it solved..
first open terminal and type
sudo gedit /etc/NetworkManager/nm-system-settings.conf

after it opens "nm-system-settings.conf" in editor 
comment
no-auto-default=[-----------------]
to make it.
#no-auto-default=[-----------------]
now save and close..restart and see if it works

---

