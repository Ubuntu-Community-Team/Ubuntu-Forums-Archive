---
title: "Ubuntu 18.04.1 LTS WiFi Stopped Working"
date: 2018-10-04
forum: Networking &amp; Wireless
---

### Post by gamedevguy on 2018-10-04
Yup, it's another one of those pesky Wifi threads!
I am running a Gigabyte H370N WIFI with Intel CNVi 802.11ac Dual Band 9560 Wave2 2T2R (external split-tail antenna) WiFi.
Fortunately, I can pinpoint what I was doing when the WiFi became disabled. I had compiled the source code for Unreal Engine 4. I ran the editor, which worked fine. Then, I saved, closed, and reopened the editor. That's when I lost the WiFi. When I went to launch a test application window, the editor informed me that there was no network connection. I tried to log out to see if logging back in would fix the problem, but the OS crashed on logout. I rebooted and found that I still have no WiFi. I have done the appropriate terminal probing. Here are the results:

```

sudo lshw -c network
  *-network:0               
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:16 memory:a3334000-a3337fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: e0:d5:5e:84:bf:fa
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:a3200000-a321ffff ioport:3000(size=32) memory:a3220000-a3223fff
  *-network:1
       description: Ethernet interface
       product: Ethernet Connection (7) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 10
       serial: e0:d5:5e:84:bf:fb
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:123 memory:a3300000-a331ffff

```
```

sudo modprobe wl
modprobe: FATAL: Module wl not found in directory /lib/modules/4.15.0-36-generic

```
```

lspci -nnk
Network controller [0280]: Intel Corporation Device [8086:a370] (rev 10)
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```
```

iwconfig
lo        no wireless extensions.


enp2s0    no wireless extensions.


eno1      no wireless extensions.

```
```

sudo iwlist scan
lo        Interface doesn't support scanning.


enp2s0    Interface doesn't support scanning.


eno1      Interface doesn't support scanning.

```
```

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
```

dmesg | grep wl
[    0.063853] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.065215] ACPI Error: [_SB_.PCI0.RP09.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    0.066765] ACPI Error: [_SB_.PCI0.RP13.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[    6.243647] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    6.265555] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[    6.280341] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    6.325499] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[    6.325504] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[    6.325544] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x3, CPU2 Status: 0x2459
[    6.325546] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[    6.337795] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5

```

[LIST]
[/LIST]

---

### Post by gamedevguy on 2018-10-07
I just wanted to let people know that I got into a discussion for this on LinuxQuestions. You can read the convo [here]("https://www.linuxquestions.org/questions/showthread.php?p=5912013#post5912013").

UPDATE: This is solved. You can read the steps taken at the link above.

---

