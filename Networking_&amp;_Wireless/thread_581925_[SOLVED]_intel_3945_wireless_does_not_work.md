---
title: "[SOLVED] intel 3945 wireless does not work"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by sayyeah on 2007-10-19
It works eventually.....
I waited for some time and did ifup wlan0 again, and it works !
I'll try again with the acpi service running.
But it took many hours to arrive here.
.
------------------------------------------------------------------------------------------------------------------------------------------------

Hi all.  I installed the official version of ubuntu 7.10 on my T61 notebook.
Because the wireless card didn't work(not even wlan0 or eth1 could be seen),
I rmmod'ed ipw3945 and modprobe'd iwl3945.
Also, i stopped the acpi service to see whether it works..
After stopping acpi service I can see that "wmaster0" and "wlan0 " appeared on iwconfig.

However, if I run sudo ifup wlan0, it says:
Ignoring unknown interface wlan0=wlan0

Did I miss something ?

Any comments would be appreciated.
Thanks.

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

lsmod|grep 3945
iwl3945                88424  0 
iwlwifi_mac80211      175112  1 iwl3945

```

```

dmesg|grep 3945
[   14.820000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.820000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.910000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  124.270000] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
[  124.270000] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[  124.270000] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  124.410000] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  124.410000] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

```

```

lspci
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
        Subsystem: Lenovo Lenovo Thinkpad T61
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe000000 (32-bit, non-prefetchable) [size=128K]
        Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1840 [size=32]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at df3ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

```

```

lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:16:1b:8a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=143.215.207.105 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:04:19:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

---

### Post by millfarm on 2007-10-20
did you do anything except wait? I can't get it to work, my wireless finds the network correctly, but can't connect :(

---

### Post by toni2 on 2007-10-25
Tell me something when exists a patch that solves this problem via ubuntu update (using ethernet to get patches. Then we can say this problem is fixed)

---

### Post by millfarm on 2007-10-25
yes, this is very annoying and I'm very close to going back to Windows..

I've noticed a strange thing though, I was at a hotel the past 2 days, and their wireless internet connection was no problem getting a connection to.... but my own, where i'm using a 3com access point.... no such luck... even with all types of encryption and so on disabled.

Come on, someone must have a solution for this..

---

### Post by BC7333 on 2007-12-30
> **millfarm said:**
> yes, this is very annoying and I'm very close to going back to Windows..

I've noticed a strange thing though, I was at a hotel the past 2 days, and their wireless internet connection was no problem getting a connection to.... but my own, where i'm using a 3com access point.... no such luck... even with all types of encryption and so on disabled.

Come on, someone must have a solution for this..

Had similar problems with a USR9106 wl router.  Hotels ok but home really wierd.  get about 15 feet from router hold laptop to chest away from router, swing back and forth three times and wireless came up..

upgrading the kernel resolved this.  I followed [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Good luck!

---

