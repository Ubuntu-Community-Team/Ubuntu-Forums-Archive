---
title: "How can I tell what has disabled my wired network driver?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by finalrequiem on 2008-09-29
Initially i thought it was related to the problems with the Intrepid alpha and the e1000e drivers but I'm running an older kernel (and have never used Intrepid) that shouldn't have the module blacklisted unless I missed something.  2.6.24-19-generic with x86_64.

-network UNCLAIMED
description: Ethernet controller
product: 82566DC Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
*-network DISABLED
description: Wireless interface
product: PRO/Wireless 4965 AG or AGN Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 61
serial: 00:1d:e0:66:a5:6d
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by pytheas22 on 2008-09-30
It looks like no driver is claiming your ethernet card at all, but I'm not sure why.  Did you blacklist any drivers or do anything else yourself that would have modified the default networking configuration on your system?

If you post the output of the following commands (in this order):
```

lspci -nn
lsmod | grep e1000
sudo rmmod e1000
sudo modprobe e1000
dmesg | grep -e e1000 -e eth0
lshw -C Network
```

it will help to figure out what could be causing this.

---

### Post by finalrequiem on 2008-09-30
_**lspci -nn**_
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Connection [8086:104b] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro FX 570M [10de:040c] (rev a1)
02:00.0 Memory controller [0580]: Intel Corporation Turbo Memory Controller [8086:444e] (rev 01)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4230] (rev 61)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 11)
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)

[B][U]lsmod | grep e1000
[/U][/B]
e1000                 137536  0 

[B][U]sudo rmmod e1000
[/U][/B]
ERROR: Module e1000 does not exist in /proc/modules

[U][B]sudo modprobe e1000
[/B][/U]
produced nothing at all

[B][U]dmesg | grep -e e1000 -e eth0
[/U][/B]
[   19.531889] e1000: 0000:00:19.0: e1000_probe: The EEPROM Checksum Is Not Valid
[   19.552175] e1000: probe of 0000:00:19.0 failed with error -5
[  107.333625] e1000: 0000:00:19.0: e1000_probe: The EEPROM Checksum Is Not Valid
[  107.353947] e1000: probe of 0000:00:19.0 failed with error -5

**_lshw -C Network_**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:66:a5:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.111 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by pytheas22 on 2008-09-30
I think I know what's wrong.  If you type:
```

sudo rmmod e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1
sudo ifconfig eth0 up
```

that should bring the ethernet card up and allow you to connect to the Internet using Network Manager.  Does it work?  If so, we can make this fix be applied automatically from now on.

In case you're interested, more information about the issue is available [here]("http://www.thinkwiki.org/wiki/Problem_with_e1000:_EEPROM_Checksum_Is_Not_Valid").  The problem seems to be, as your 'dmesg' output indicates, that the e1000 module doesn't like some checksum or other, which is a known issue in certain situations.  The commands above should force e1000 to work regardless of the checksum.

---

### Post by finalrequiem on 2008-09-30
First two seem to run ok (don't give me anything back )  third says:

eth0: ERROR while getting interface flags: No such device

---

### Post by pytheas22 on 2008-09-30
Sorry that didn't work.  Please post the output of this (in this order):
```

sudo rmmod e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1
dmesg | tail
ifconfig
lshw -C Network
```

---

### Post by finalrequiem on 2008-09-30
**_sudo rmmod e1000_**
ERROR: Module e1000 does not exist in /proc/modules
[B][U]
sudo modprobe e1000 eeprom_bad_csum_allow=1[/U][/B]
no output at all
[B][U]
dmesg | tail[/U][/B]
[  709.842353] ACPI: PCI interrupt for device 0000:00:19.0 disabled
[  709.842365] e1000: probe of 0000:00:19.0 failed with error -5
[  723.810094] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[  723.810103] Copyright (c) 1999-2006 Intel Corporation.
[  723.810163] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
[  723.810187] PCI: Setting latency timer of device 0000:00:19.0 to 64
[  723.817937] e1000: 0000:00:19.0: e1000_probe: The EEPROM Checksum Is Not Valid
[  723.817998] e1000: 0000:00:19.0: e1000_probe: Invalid MAC Address
[  723.838333] ACPI: PCI interrupt for device 0000:00:19.0 disabled
[  723.838357] e1000: probe of 0000:00:19.0 failed with error -5

**_ ifconfig_**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123400 (120.5 KB)  TX bytes:123400 (120.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.110.1  Bcast:172.16.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.193.1  Bcast:192.168.193.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:66:a5:6d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe66:a56d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2074649 (1.9 MB)  TX bytes:268368 (262.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-66-A5-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**_lshw -C Network_**
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:66:a5:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.111 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

Sorry, I'm not being much help...

---

### Post by pytheas22 on 2008-10-01
Sorry it's still not working.  Does it help if you shut your computer down completely (don't suspend or resume), unplug the power cable (or take out the battery) for a minute, then turn the machine back on, making sure that the ethernet cable is plugged in before you press the power button?  From what I'm reading, this may help.

If that still doesn't work, please try running these commands (you will need to connect using the wireless first):
```

wget http://burnthesorbonne.com/files/e1000-fix.sh
sudo chmod +x e1000-fix.sh
sudo modprobe -r e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1
sudo ./e1000-fix.sh
```

According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/60388"), they may help.

---

### Post by finalrequiem on 2008-10-01
Still nothing...  It makes me think I am missing something obvious.  What a pain...

---

### Post by pytheas22 on 2008-10-01
It's not you missing something obvious...the problem is clearly with the checksum; I'm just not sure why the things that you tried above didn't work around it.  I need to sleep now, but I'll look into this more tomorrow (please also feel free to google around for information about bad checksum and the e1000 driver, or look more at that web page that I linked to in my first post here--it has some more suggestions for getting the card working that we haven't tried).  If I haven't responded again by tomorrow at this time, please bump the thread or send a message.

---

### Post by pytheas22 on 2008-10-01
Please give these things a try:

1. disable the ethernet card in your BIOS (if possible), then reboot, then enable the card again, and boot to Ubuntu again.  Does it work?

2. what is the output of:
```

sudo rmmod e1000
sudo modprobe e1000e
dmesg | tail
```

3. what is the output of:
```

sudo modprobe -r e1000 e1000e
sudo modprobe e1000 eeprom_bad_csum_allow=1
ifconfig
sudo ifconfig eth0 hw ether 01:23:45:67:89:01
```

Sorry this is still not working, but if we keep trying, we'll get it...

By the way, this ethernet card works in Windows, right?

---

### Post by lavinog on 2008-10-02
[QUOTE=finalrequiem (from other thread)]I upgraded to 8.04 from Studio (7.10, I think) without a hitch, wired and wireless connections worked without any trouble. I just went with a fresh install of 8.04 because I wanted to completely wipe my HDD and start fresh. Now my wireless works but there is no wired connection. Not even showing one in Network Manager... Not sure where to go from here...

T61p, by the way...[/QUOTE]

Since it worked in fiesty, have you tried a live cd of fiesty to see if it worked?
Maybe test another distro too and see if it still fails.

---

### Post by finalrequiem on 2008-10-03
Been away for a couple of days so I'm just getting to the last couple of posts.  I don't have windows right now (disk didn't come with my notebook and I haven't requested one yet) and I don't have a feisty livecd just a studio alternate (which wreaks havoc on my system, hardware issues galore).  Working on getting windows AND a different linux distro to try.

---

### Post by finalrequiem on 2008-10-03
> **pytheas22 said:**
> Please give these things a try:

1. disable the ethernet card in your BIOS (if possible), then reboot, then enable the card again, and boot to Ubuntu again.  Does it work?

2. what is the output of:
```

sudo rmmod e1000
sudo modprobe e1000e
dmesg | tail
```

3. what is the output of:
```

sudo modprobe -r e1000 e1000e
sudo modprobe e1000 eeprom_bad_csum_allow=1
ifconfig
sudo ifconfig eth0 hw ether 01:23:45:67:89:01
```

Sorry this is still not working, but if we keep trying, we'll get it...

By the way, this ethernet card works in Windows, right?

[B][U]
1st set:[/U][/B]
```

[ 8776.589570] /dev/vmnet: open called by PID 5414 (vmnet-bridge)
[ 8776.589585] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 8776.589607] /dev/vmnet: port on hub 0 successfully opened
[ 8776.589623] bridge-wlan0: is a Wireless Adapter
[ 8776.589629] bridge-wlan0: up
[ 8776.589634] bridge-wlan0: attached
[ 8777.198760] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445521169115050315 new 18445521169120048730 attempts 1
[ 8779.235444] wlan0: no IPv6 routers present
[ 8838.621787] e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
[ 8838.621795] e1000e: Copyright (c) 1999-2007 Intel Corporation.
```
[B][U]
2nd:[/U][/B]
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:161692 (157.9 KB)  TX bytes:161692 (157.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.110.1  Bcast:172.16.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.193.1  Bcast:192.168.193.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:66:a5:6d  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe66:a56d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:311121423 (296.7 MB)  TX bytes:13739463 (13.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-66-A5-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```

SIOCSIFHWADDR: No such device
```

---

### Post by pytheas22 on 2008-10-03
hmmm, I don't get it.  There is a known issue with your ethernet card (the checksum error), but everything on the Internet says that at least one of the many things we've tried so far should have solved this.  Have you ever used this ethernet card before?  If not, it's possible that the hardware is just shot, although we don't have enough evidence at this point to know for sure (we'd really need to test it in Windows too).   Please let us know if you can get this to work in a different distribution, or in Windows when it's available.  In the meantime, I'll keep googling, but I'm not finding anything that we haven't already tried...

---

### Post by finalrequiem on 2008-10-03
I've used it with no problem since I got it (February).  I went with a fresh install of 8.04, same disk as before, and it just didn't work anymore.  It's possible the hardware is dead, it just seems strange that it would just go kaput out of the blue...  Soon as I get a Windows disk I will try that and I am d'loading a fedora live DVD right now.

---

### Post by lavinog on 2008-10-03
> **finalrequiem said:**
> I've used it with no problem since I got it (February).  I went with a fresh install of 8.04, same disk as before, and it just didn't work anymore.  It's possible the hardware is dead, it just seems strange that it would just go kaput out of the blue...  Soon as I get a Windows disk I will try that and I am d'loading a fedora live DVD right now.

link to fiesty live image: [http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso]("http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso")

It is still possible that it is a driver issue: It worked in fiesty, then you upgraded to hardy and it still worked. once you erased your hd and installed hardy fresh it stopped working. It is possible that what ever fiesty was doing for the driver was carried over to hardy when you upgraded.

---

### Post by finalrequiem on 2008-10-03
Didn't think about that...  I'll try that too.

---

### Post by mike-g2 on 2008-10-07
> **pytheas22 said:**
> I think I know what's wrong.  If you type:
```

sudo rmmod e1000
sudo modprobe e1000 eeprom_bad_csum_allow=1
sudo ifconfig eth0 up
```

that should bring the ethernet card up and allow you to connect to the Internet using Network Manager.  Does it work?  If so, we can make this fix be applied automatically from now on.
.
.
.

Although I am not the original poster... Yippie!  This solved my problem. Thanks for the post!

---

### Post by pytheas22 on 2008-10-07
> Although I am not the original poster... Yippie! This solved my problem. Thanks for the post!

Glad that worked for you--but you will probably need to type that command each time you reboot your computer in order to get the ethernet to work.  If you want to make the fix permanent, run these commands:
```

sudo -s
cd /etc/init.d
echo '#!/bin/bash' > ethernet-fix.sh
echo 'rmmod e1000' >> ethernet-fix.sh
echo 'modprobe e1000 eeprom_bad_csum_allow=1' >> ethernet-fix.sh
echo 'ifconfig eth0 up' >> ethernet-fix.sh
chmod +x ethernet-fix.sh
update-rc.d ethernet-fix.sh defaults
```

After doing that, you should be able to reboot your computer and the ethernet will 'just work' with no manual intervention required.

As for the original poster: have you made any progress in diagnosing or solving this?  Were you able to test the card under Windows to rule out hardware error?

---

