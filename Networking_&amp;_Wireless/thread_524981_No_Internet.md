---
title: "No Internet"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by fatsheep on 2007-08-13
I connect fine to the internet on Windows but on Ubuntu the machine in question doesn't connect and not only that, the LED for my NIC does not turn on.  Other machines on the network (including the one I am typing from) get internet fine as well.  What gives?  

Thanks in advance,

- fatsheep

---

### Post by moore.bryan on 2007-08-13
[I]what's the output of ```
lspci
```?

it's possible linux isn't loading your card...[/I]

---

### Post by fatsheep on 2007-08-14
> **moore.bryan said:**
> [I]what's the output of ```
lspci
```?

it's possible linux isn't loading your card...[/I]

Looks like it is detected:

```
alex@alex-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
**04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)**
```

---

### Post by moore.bryan on 2007-08-14
*so you're "hard-wired?"  if so, then your card is loaded and you're just not getting on.  if you're wireless... you don't have a card. ;-)*

---

### Post by fatsheep on 2007-08-14
> **moore.bryan said:**
> *so you're "hard-wired?"  if so, then your card is loaded and you're just not getting on.  if you're wireless... you don't have a card. ;-)*

I have a physical, wired NIC.  It's integrated into the motherboard and works fine on Windows as I said.  Actually it worked fine on Ubuntu up till now.  Maybe a recent firefox update broke it?

---

### Post by moore.bryan on 2007-08-14
*hmm... i don't know why that would change anything.  have you tried another browser?*

---

### Post by fatsheep on 2007-08-14
> **moore.bryan said:**
> *hmm... i don't know why that would change anything.  have you tried another browser?*

Firefox updated like I said but besides that no.  Should I post a support request on Launchpad?

---

### Post by moore.bryan on 2007-08-15
*it wouldn't hurt... i've never experienced an ethernet problem; ubuntu "just works" for me there.  perhaps a much more enlightened poster will come along to help you...  if i think of anything, i'll repost.*

---

### Post by Noodels on 2007-08-15
Hang on a minute, I have the same problem. In my room there is a printserver acting as a switch (no printer) and two computers. My windows laptop (this one) and my ubuntu computer (no internet). As indicated above when I switch on my computer the led on the switch doesn't even turn on, unlike the windows laptop where it turns on as soon as I hit the power button. Ubuntu worked fine on the internet up until recently, when I plugged the laptop into the ethernet. After a couple of hours on the laptop the internet went on ubuntu. I've been unable to get it back. I have tried :
[LIST]
[*]Changing where the cables are plugged in on the print server.
[*]Cold booting both printserver and computer.
[*]Unplugging laptop ethernet and trying everything else on the list.
[*]Restarting ubuntu repeatedly.
[*]Banging my head against the desk.
[/LIST]

EDIT : Okay, when I started ubuntu and the internet was working, it would connect to the internet straight away. When the internet isn't going to work and the led in the printserver hasn't come on ubuntu says it's connecting, does that for a while then says "Connected to Ethernet" when it's really not what with not being able to use gaim. So, I tried unplugging the network cable into my computer, apparently it was "Connected to Ethernet" despite the fact that I couldn't use the internet at all and it being unplugged. Suggestions would be nice while I go look for another wire.

EDIT : Alright fatsheep, this makes sense now, no led on the switch or whatever your using sounds a lot like your wire is broken, like mine was. SO, replace the wire, I'm using the one my windows computer was plugged in with (Grr windows...) and I'm now on my ubuntu computer. :) Just take one of the wires from a lower priority computer, like someone elses. My internet must have went when I fiddled around with the printserver and lost one of the connections in the wire.

---

### Post by fatsheep on 2007-08-15
> **Noodels said:**
> Hang on a minute, I have the same problem. In my room there is a printserver acting as a switch (no printer) and two computers. My windows laptop (this one) and my ubuntu computer (no internet). As indicated above when I switch on my computer the led on the switch doesn't even turn on, unlike the windows laptop where it turns on as soon as I hit the power button. Ubuntu worked fine on the internet up until recently, when I plugged the laptop into the ethernet. After a couple of hours on the laptop the internet went on ubuntu. I've been unable to get it back. I have tried :
[LIST]
[*]Changing where the cables are plugged in on the print server.
[*]Cold booting both printserver and computer.
[*]Unplugging laptop ethernet and trying everything else on the list.
[*]Restarting ubuntu repeatedly.
[*]Banging my head against the desk.
[/LIST]

EDIT : Okay, when I started ubuntu and the internet was working, it would connect to the internet straight away. When the internet isn't going to work and the led in the printserver hasn't come on ubuntu says it's connecting, does that for a while then says "Connected to Ethernet" when it's really not what with not being able to use gaim. So, I tried unplugging the network cable into my computer, apparently it was "Connected to Ethernet" despite the fact that I couldn't use the internet at all and it being unplugged. Suggestions would be nice while I go look for another wire.

EDIT : Alright fatsheep, this makes sense now, no led on the switch or whatever your using sounds a lot like your wire is broken, like mine was. SO, replace the wire, I'm using the one my windows computer was plugged in with (Grr windows...) and I'm now on my ubuntu computer. :) Just take one of the wires from a lower priority computer, like someone elses. My internet must have went when I fiddled around with the printserver and lost one of the connections in the wire.

I've already tried a different wire.  Same results: Windows works, Ubuntu does not. And if it was a broken wire then why does Windows still connect? :(

---

### Post by noob12 on 2007-08-15
Can we have a look at what's going on?
```

sudo lshw -C network

```
Post the whole output and if there is a logical name listed (like eth0), use that interface name in the following
```

ifconfig -a

#substitute your actual interface name from the above for eth0 if it is different
sudo ethtool eth0

```
and post the output of these.

---

### Post by fatsheep on 2007-08-15
I ran those commands but still no internet.  Here is the output:

```
**alex@alex-desktop:~$ sudo lshw -C network**
Password:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:47:2a:65
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:d000-d0ff iomemory:f8000000-f8000fff irq:16

**alex@alex-desktop:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:47:2A:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:47:2A:65  
          inet addr:169.254.4.43  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27636 (26.9 KiB)  TX bytes:27636 (26.9 KiB)

**alex@alex-desktop:~$ sudo ethtool eth0**
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no


```

---

### Post by noob12 on 2007-08-15
The device is claimed, interface is there.  Ethtool says there is no link detected.  (Check your connection to be sure).  If you're sure there should be, we want see if the driver had any kind of initialization issues or to see if there were any PCI routing issues at boot.

This will try to reload the driver module and ask it to spit out more.
```

sudo /etc/init.d/networking stop
sudo modprobe -r r8169
sudo modprobe r8169 debug=16
sudo /etc/init.d/networking start

```

Please post the full output of
```

dmesg

```
after that.  This is to see both the boot-time condition and the last attempt above.

---

### Post by Mrs Twaddle on 2007-08-16
I've just had this problem,.

Did you just get a windows update?
I did, and that is the ONLY thing that has changed on my connection (I use dual boot)
Linux will NOT connect, windows does no problem.
"Realtek Semiconductor Corp. - Networking - Realtek RTL8139/810x Family Fast Ethernet NIC" is the update i had today....
i'm going to try uninstalling it to see if that helps.

---

### Post by Mrs Twaddle on 2007-08-16
> **Mrs Twaddle said:**
> I've just had this problem,.

Did you just get a windows update?
I did, and that is the ONLY thing that has changed on my connection (I use dual boot)
Linux will NOT connect, windows does no problem.
"Realtek Semiconductor Corp. - Networking - Realtek RTL8139/810x Family Fast Ethernet NIC" is the update i had today....
i'm going to try uninstalling it to see if that helps.

sorry for the double post, but I just rolled back the driver for that device on my windows partition


And the internet WORKS now.
I can't understand how there can be a connection or if it is just co-incidence,....

---

### Post by noob12 on 2007-08-16
Twaddle is running an 8139 device and 8139too on the linux side.  That's now a known recent issue for that device (see [http://ubuntuforums.org/showthread.php?p=3193599](http://ubuntuforums.org/showthread.php?p=3193599) as well).  

This may not be the same issue with the 8169.

fatsheep: If you are dual-booting and you recently upgraded a windows driver, you might try rolling it back, particularly if you warm reboot across to linux.

If that isn't it, we need to continue with the diagnostics.  Please try the procedure in post #13 on this thread to get more info about why you're in this situation.

---

### Post by fatsheep on 2007-08-17
> **noob12 said:**
> Twaddle is running an 8139 device and 8139too on the linux side.  That's now a known recent issue for that device (see [http://ubuntuforums.org/showthread.php?p=3193599](http://ubuntuforums.org/showthread.php?p=3193599) as well).  

This may not be the same issue with the 8169.

fatsheep: If you are dual-booting and you recently upgraded a windows driver, you might try rolling it back, particularly if you warm reboot across to linux.

If that isn't it, we need to continue with the diagnostics.  Please try the procedure in post #13 on this thread to get more info about why you're in this situation.

Rolling back the driver didn't seem to do anything.  I could try again though.  Here's the output of those diagnostic commands:

```

**alex@alex-desktop:~$ sudo /etc/init.d/networking stop**
 * Deconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:4d:47:2a:65
Sending on   LPF/eth0/00:1a:4d:47:2a:65
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
sudo modprobe -r r8169
alex@alex-desktop:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                   [ OK ] 
**alex@alex-desktop:~$ sudo modprobe -r r8169**
**alex@alex-desktop:~$ sudo modprobe r8169 debug=16**
**alex@alex-desktop:~$ sudo /etc/init.d/networking start**
 * Configuring network interfaces...                                            eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]

```

Output of dmseg:

```

[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=41ac4713-a7fa-4fa5-92a2-47638500d4ee ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x00000000000f6f10
[    0.000000] ACPI: RSDT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x000000007fee3040
[    0.000000] ACPI: FADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x000000007fee30c0
[    0.000000] ACPI: HPET (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x00000098) @ 0x000000007fee7d80
[    0.000000] ACPI: MCFG (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x000000007fee7e00
[    0.000000] ACPI: MADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x000000007fee7c80
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20040311) @ 0x000000007fee7e80
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20040311) @ 0x000000007fee8310
[    0.000000] ACPI: DSDT (v001 GBT    GBTUACPI 0x00001000 MSFT 0x0100000c) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515652
[    0.000000] Kernel command line: root=UUID=41ac4713-a7fa-4fa5-92a2-47638500d4ee ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   30.965608] Console: colour VGA+ 80x25
[   30.966557] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   30.967326] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.967466] Checking aperture...
[   30.967475] Calgary: detecting Calgary via BIOS EBDA area
[   30.967477] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   30.984850] Memory: 2052456k/2096000k available (2217k kernel code, 43156k reserved, 1162k data, 304k init)
[   31.061792] Calibrating delay using timer specific routine.. 4270.42 BogoMIPS (lpj=8540840)
[   31.061837] Security Framework v1.0.0 initialized
[   31.061842] SELinux:  Disabled at boot.
[   31.061863] Mount-cache hash table entries: 256
[   31.061988] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.061990] CPU: L2 cache: 4096K
[   31.061993] CPU 0/0 -> Node 0
[   31.061994] using mwait in idle threads.
[   31.061996] CPU: Physical Processor ID: 0
[   31.061997] CPU: Processor Core ID: 0
[   31.062003] CPU0: Thermal monitoring enabled (TM2)
[   31.062013] SMP alternatives: switching to UP code
[   31.062217] Early unpacking initramfs... done
[   31.360718] ACPI: Core revision 20060707
[   31.363786] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.406923] Using local APIC timer interrupts.
[   31.453804] result 16666645
[   31.453806] Detected 16.666 MHz APIC timer.
[   31.457938] SMP alternatives: switching to SMP code
[   31.457998] Booting processor 1/2 APIC 0x1
[   31.468595] Initializing CPU#1
[   31.545790] Calibrating delay using timer specific routine.. 4266.76 BogoMIPS (lpj=8533528)
[   31.545796] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.545797] CPU: L2 cache: 4096K
[   31.545799] CPU 1/1 -> Node 0
[   31.545801] CPU: Physical Processor ID: 0
[   31.545802] CPU: Processor Core ID: 1
[   31.545807] CPU1: Thermal monitoring enabled (TM2)
[   31.546265] Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[   31.549801] Brought up 2 CPUs
[   31.549840] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer.
[   31.549842] time.c: Detected 2133.332 MHz processor.
[   31.684570] migration_cost=19
[   31.684829] Time: 21:40:38  Date: 07/17/107
[   31.684856] NET: Registered protocol family 16
[   31.684918] ACPI: bus type pci registered
[   31.684923] PCI: Using configuration type 1
[   31.684925] mtrr: your CPUs had inconsistent variable MTRR settings
[   31.684927] mtrr: probably your BIOS does not setup all CPUs.
[   31.684928] mtrr: corrected configuration.
[   31.692130] ACPI: Interpreter enabled
[   31.692134] ACPI: Using IOAPIC for interrupt routing
[   31.692662] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.692668] PCI: Probing PCI hardware (bus 00)
[   31.693562] Boot video device is 0000:01:00.0
[   31.694068] PCI: Transparent bridge - 0000:00:1e.0
[   31.694123] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.710978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   31.711361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   31.711963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   31.712244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   31.715258] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   31.715463] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   31.715671] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   31.715877] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   31.716080] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   31.716290] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   31.716495] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   31.716701] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   31.716877] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.716886] pnp: PnP ACPI init
[   31.719611] pnp: PnP ACPI: found 15 devices
[   31.719656] PCI: Using ACPI for IRQ routing
[   31.719658] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.719741] NET: Registered protocol family 8
[   31.719743] NET: Registered protocol family 20
[   31.719753] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   31.719757] hpet0: 4 64-bit timers, 14318180 Hz
[   31.720769] PCI-GART: No AMD northbridge found.
[   31.721171] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[   31.721436] PCI: Bridge: 0000:00:01.0
[   31.721438]   IO window: b000-bfff
[   31.721441]   MEM window: f4000000-f6ffffff
[   31.721444]   PREFETCH window: e0000000-efffffff
[   31.721447] PCI: Bridge: 0000:00:1c.0
[   31.721449]   IO window: 9000-9fff
[   31.721452]   MEM window: disabled.
[   31.721455]   PREFETCH window: disabled.
[   31.721459] PCI: Bridge: 0000:00:1c.3
[   31.721461]   IO window: c000-cfff
[   31.721465]   MEM window: f9000000-f90fffff
[   31.721468]   PREFETCH window: disabled.
[   31.721472] PCI: Bridge: 0000:00:1c.4
[   31.721474]   IO window: d000-dfff
[   31.721478]   MEM window: f7000000-f8ffffff
[   31.721481]   PREFETCH window: 80000000-800fffff
[   31.721485] PCI: Bridge: 0000:00:1e.0
[   31.721487]   IO window: a000-afff
[   31.721491]   MEM window: disabled.
[   31.721493]   PREFETCH window: disabled.
[   31.721505] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.721509] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.721522] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.721526] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.721540] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   31.721544] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   31.721558] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   31.721562] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.721570] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.721600] NET: Registered protocol family 2
[   31.766072] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   31.766210] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   31.767444] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   31.767939] TCP: Hash tables configured (established 262144 bind 65536)
[   31.767941] TCP reno registered
[   31.782277] checking if image is initramfs... it is
[   32.368323] Freeing initrd memory: 6827k freed
[   32.371339] audit: initializing netlink socket (disabled)
[   32.371355] audit(1187386838.368:1): initialized
[   32.371503] VFS: Disk quotas dquot_6.5.1
[   32.371520] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   32.371564] io scheduler noop registered
[   32.371566] io scheduler anticipatory registered
[   32.371568] io scheduler deadline registered
[   32.371579] io scheduler cfq registered (default)
[   32.371836] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.371863] assign_interrupt_mode Found MSI capability
[   32.371866] Allocate Port Service[0000:00:01.0:pcie00]
[   32.371932] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.371965] assign_interrupt_mode Found MSI capability
[   32.371967] Allocate Port Service[0000:00:1c.0:pcie00]
[   32.371995] Allocate Port Service[0000:00:1c.0:pcie02]
[   32.372073] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   32.372106] assign_interrupt_mode Found MSI capability
[   32.372107] Allocate Port Service[0000:00:1c.3:pcie00]
[   32.372132] Allocate Port Service[0000:00:1c.3:pcie02]
[   32.372210] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   32.372242] assign_interrupt_mode Found MSI capability
[   32.372244] Allocate Port Service[0000:00:1c.4:pcie00]
[   32.372271] Allocate Port Service[0000:00:1c.4:pcie02]
[   32.389850] Real Time Clock Driver v1.12ac
[   32.389893] Linux agpgart interface v0.102 (c) Dave Jones
[   32.389895] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.390004] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.390448] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.390616] mice: PS/2 mouse device common for all mice
[   32.391079] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.391239] input: Macintosh mouse button emulation as /class/input/input0
[   32.391268] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.391271] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.391435] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   32.391708] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.391711] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.391786] TCP cubic registered
[   32.391794] NET: Registered protocol family 1
[   32.391872] ACPI: (supports S0 S3 S4 S5)
[   32.391909]   Magic number: 3:650:702
[   32.391969] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   32.392030] Freeing unused kernel memory: 304k freed
[   32.408470] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.529516] Capability LSM initialized
[   33.556004] ACPI: Processor [CPU0] (supports 8 throttling states)
[   33.556199] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   33.556231] ACPI: Processor [CPU1] (supports 8 throttling states)
[   33.556236] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   33.556241] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   33.811756] usbcore: registered new interface driver usbfs
[   33.811772] usbcore: registered new interface driver hub
[   33.811789] usbcore: registered new device driver usb
[   33.858072] USB Universal Host Controller Interface driver v3.0
[   33.858123] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.858132] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   33.858136] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   33.858231] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   33.858256] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   33.858341] usb usb1: configuration #1 chosen from 1 choice
[   33.858362] hub 1-0:1.0: USB hub found
[   33.858366] hub 1-0:1.0: 2 ports detected
[   33.862111] SCSI subsystem initialized
[   33.865491] libata version 2.20 loaded.
[   33.889974] Floppy drive(s): fd0 is 1.44M
[   33.912219] FDC 0 is a post-1991 82077
[   33.965616] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   33.965625] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   33.965629] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   33.965738] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   33.965763] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[   33.966120] usb usb2: configuration #1 chosen from 1 choice
[   33.966248] hub 2-0:1.0: USB hub found
[   33.966253] hub 2-0:1.0: 2 ports detected
[   34.074118] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.074125] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   34.074128] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   34.074143] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   34.074164] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[   34.074227] usb usb3: configuration #1 chosen from 1 choice
[   34.074247] hub 3-0:1.0: USB hub found
[   34.074250] hub 3-0:1.0: 2 ports detected
[   34.178456] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   34.178464] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.178467] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.178489] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   34.178512] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[   34.178593] usb usb4: configuration #1 chosen from 1 choice
[   34.178623] hub 4-0:1.0: USB hub found
[   34.178628] hub 4-0:1.0: 2 ports detected
[   34.283509] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   34.283517] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.283520] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.283539] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   34.283563] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[   34.283644] usb usb5: configuration #1 chosen from 1 choice
[   34.283674] hub 5-0:1.0: USB hub found
[   34.283678] hub 5-0:1.0: 2 ports detected
[   34.388545] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.388552] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.388556] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.388574] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   34.388595] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[   34.388676] usb usb6: configuration #1 chosen from 1 choice
[   34.388702] hub 6-0:1.0: USB hub found
[   34.388717] hub 6-0:1.0: 2 ports detected
[   34.493585] ata_piix 0000:00:1f.2: version 2.10ac1
[   34.493590] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   34.493610] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   34.493625] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   34.494164] ata1: SATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001f000 irq 14
[   34.494215] ata2: SATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001f008 irq 15
[   34.494230] scsi0 : ata_piix
[   34.525477] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   34.700610] usb 4-1: configuration #1 chosen from 1 choice
[   34.710261] usbcore: registered new interface driver libusual
[   34.712570] Initializing USB Mass Storage driver...
[   34.712612] scsi2 : SCSI emulation for USB Mass Storage devices
[   34.712649] usbcore: registered new interface driver usb-storage
[   34.712651] USB Mass Storage support registered.
[   34.712709] usb-storage: device found at 2
[   34.712710] usb-storage: waiting for device to settle before scanning
[   34.989690] ata1.00: ATAPI, max UDMA/100
[   35.170802] ata1.00: configured for UDMA/100
[   35.170810] scsi1 : ata_piix
[   35.381642] ata2.00: ata_hpa_resize 1: sectors = 976771055, hpa_sectors = 976773168
[   35.381647] ata2.00: Host Protected Area detected.
[   35.381648]      current size : 976771055 sectors (500106 MB)
[   35.381650]      native  size : 976773168 sectors (500107 MB)
[   35.550085] ata2.00: Native size increased to 976773168 sectors
[   35.550089] ata2.00: ATA-7: ST3500641AS, 3.AAJ, max UDMA/133
[   35.550091] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   35.589833] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
[   35.589838] ata2.00: configured for UDMA/133
[   35.591070] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[   35.591615] scsi 1:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
[   35.592037] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   35.592056] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   35.592070] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   35.592094] ata3: SATA max UDMA/133 cmd 0x000000000001e700 ctl 0x000000000001e802 bmdma 0x000000000001eb00 irq 19
[   35.592113] ata4: SATA max UDMA/133 cmd 0x000000000001e900 ctl 0x000000000001ea02 bmdma 0x000000000001eb08 irq 19
[   35.592120] scsi3 : ata_piix
[   35.758347] ATA: abnormal status 0x7F on port 0x000000000001e707
[   35.758356] scsi4 : ata_piix
[   35.927925] ATA: abnormal status 0x7F on port 0x000000000001e907
[   35.928753] ahci 0000:03:00.0: version 2.1
[   35.928769] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   36.933473] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   36.933482] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   36.933486] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   36.933545] ata5: SATA max UDMA/133 cmd 0xffffc2000001c100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   36.933601] ata6: SATA max UDMA/133 cmd 0xffffc2000001c180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   36.933607] scsi5 : ahci
[   37.243738] ata5: SATA link down (SStatus 0 SControl 300)
[   37.243749] scsi6 : ahci
[   37.554126] ata6: SATA link down (SStatus 0 SControl 300)
[   37.554296] r8169 Gigabit Ethernet driver 2.2LK loaded
[   37.554317] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.554339] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   37.554636] eth0: RTL8168b/8111b at 0xffffc20000006000, 00:1a:4d:47:2a:65, IRQ 16
[   37.558981] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   37.558991] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   37.558994] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   37.559115] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   37.559142] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   37.559146] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9104000
[   37.563018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.563370] usb usb7: configuration #1 chosen from 1 choice
[   37.563501] hub 7-0:1.0: USB hub found
[   37.563506] hub 7-0:1.0: 6 ports detected
[   37.667485] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   37.667494] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   37.667497] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   37.667611] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   37.667634] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   37.667638] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9105000
[   37.671509] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.671849] usb usb8: configuration #1 chosen from 1 choice
[   37.671977] hub 8-0:1.0: USB hub found
[   37.671983] hub 8-0:1.0: 6 ports detected
[   37.777817] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   37.777825] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
[   37.777844] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   37.777943] ata7: PATA max UDMA/100 cmd 0x000000000001c000 ctl 0x000000000001c102 bmdma 0x000000000001c400 irq 16
[   37.778555] ata8: PATA max UDMA/100 cmd 0x000000000001c200 ctl 0x000000000001c302 bmdma 0x000000000001c408 irq 16
[   37.778566] scsi7 : pata_jmicron
[   37.937530] scsi8 : pata_jmicron
[   38.013846] usb 8-1: new high speed USB device using ehci_hcd and address 2
[   38.101707] ATA: abnormal status 0x7F on port 0x000000000001c207
[   38.114963] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   38.114967] Uniform CD-ROM driver Revision: 3.20
[   38.115130] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   38.115349] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   38.115357] sda: Write Protect is off
[   38.115358] sda: Mode Sense: 00 3a 00 00
[   38.115371] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.115403] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   38.115411] sda: Write Protect is off
[   38.115412] sda: Mode Sense: 00 3a 00 00
[   38.115424] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.115428]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   38.117764] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.128623]  sda1 sda2 < sda5 > sda3
[   38.142943] sd 1:0:0:0: Attached scsi disk sda
[   38.149597] usb 8-1: configuration #1 chosen from 1 choice
[   38.149847] scsi9 : SCSI emulation for USB Mass Storage devices
[   38.149886] usb-storage: device found at 2
[   38.149888] usb-storage: waiting for device to settle before scanning
[   38.149961] usb 4-1: USB disconnect, address 2
[   38.350365] Attempting manual resume
[   38.350368] swsusp: Resume From Partition 8:5
[   38.350369] PM: Checking swsusp image.
[   38.350542] PM: Resume from disk failed.
[   38.377351] kjournald starting.  Commit interval 5 seconds
[   38.377359] EXT3-fs: mounted filesystem with ordered data mode.
[   43.150704] usb-storage: device scan complete
[   43.151561] scsi 9:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
[   43.152671] SCSI device sdb: 1981440 512-byte hdwr sectors (1014 MB)
[   43.153417] sdb: Write Protect is off
[   43.153419] sdb: Mode Sense: 43 00 00 00
[   43.153420] sdb: assuming drive cache: write through
[   43.155670] SCSI device sdb: 1981440 512-byte hdwr sectors (1014 MB)
[   43.156419] sdb: Write Protect is off
[   43.156421] sdb: Mode Sense: 43 00 00 00
[   43.156423] sdb: assuming drive cache: write through
[   43.156426]  sdb: sdb1
[   43.157722] sd 9:0:0:0: Attached scsi removable disk sdb
[   43.157756] sd 9:0:0:0: Attached scsi generic sg2 type 0
[   45.021051] r8169: eth0: link down
[   46.026280] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.027878] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.103792] input: PC Speaker as /class/input/input2
[   46.274964] parport: PnPBIOS parport detected.
[   46.275007] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   46.623670] nvidia: module license 'NVIDIA' taints kernel.
[   46.877158] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.877166] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   46.880196] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.11  Wed Jun 13 16:33:22 PDT 2007
[   46.891704] NET: Registered protocol family 17
[   47.015909] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   47.015925] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   47.025593] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   47.225017] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   47.457491] fuse init (API version 7.8)
[   47.483421] lp0: using parport0 (interrupt-driven).
[   47.521444] Adding 2931820k swap on /dev/disk/by-uuid/24aebded-41d2-4dae-9569-faf4017fa8e5.  Priority:-1 extents:1 across:2931820k
[   47.651087] EXT3 FS on sda1, internal journal
[   47.829179] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   47.878877] NTFS volume version 3.1.
[   54.591838] input: Power Button (FF) as /class/input/input4
[   54.591860] ACPI: Power Button (FF) [PWRF]
[   54.591889] input: Power Button (CM) as /class/input/input5
[   54.591901] ACPI: Power Button (CM) [PWRB]
[   54.645565] ibm_acpi: ec object not found
[   54.709347] No dock devices found.
[   54.725361] Using specific hotkey driver
[   54.830678] pcc_acpi: loading...
[   58.632692] ppdev: user-space parallel port driver
[   59.647139] NET: Registered protocol family 10
[   59.647231] lo: Disabled Privacy Extensions
[   59.647273] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.733514] Bluetooth: Core ver 2.11
[   59.733567] NET: Registered protocol family 31
[   59.733569] Bluetooth: HCI device and connection manager initialized
[   59.733572] Bluetooth: HCI socket layer initialized
[   59.752797] Bluetooth: L2CAP ver 2.8
[   59.752801] Bluetooth: L2CAP socket layer initialized
[   59.955318] Bluetooth: RFCOMM socket layer initialized
[   59.955331] Bluetooth: RFCOMM TTY layer initialized
[   59.955333] Bluetooth: RFCOMM ver 1.8
[  169.486101] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[  173.387145] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  173.387388] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  173.387882] eth0: RTL8168b/8111b at 0xffffc20000006000, 00:1a:4d:47:2a:65, IRQ 16
[  173.405642] r8169: eth0: link down
[  173.405666] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  183.404784] eth0: PHY reset until link up
[  193.404685] eth0: PHY reset until link up
[  203.404586] eth0: PHY reset until link up
[  213.404487] eth0: PHY reset until link up
[  234.273029] r8169: eth0: link down
[  234.276369] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  244.273910] eth0: PHY reset until link up
[  254.273810] eth0: PHY reset until link up
[  257.477739] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[  261.673259] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  261.673308] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  261.674208] eth0: RTL8168b/8111b at 0xffffc20000006000, 00:1a:4d:47:2a:65, IRQ 16
[  261.690870] r8169: eth0: link down
[  261.690897] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  271.690193] eth0: PHY reset until link up
[  281.690094] eth0: PHY reset until link up
[  291.690978] eth0: PHY reset until link up
[  301.690877] eth0: PHY reset until link up

```

---

### Post by noob12 on 2007-08-18
fatsheep:  Try this.  Shutdown, power down.  Unplug (cuts power to card if wake-on-lan power is maintained).  Wait 15 seconds.  Plug in.  Boot ubuntu.

If this works, you are probably affected by the following (excerpt from gentoo wiki [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)).  Note the second and third paragraphs.  Then read the Windows-side workaround in the first paragraph.

> 
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.


I'm hopting that's your issue. If that doesn't work, I'm not seeing any evident issues in the dmesg.  Can you confirm that your ethernet cable is connected at boot?  There is also a  known bug in the Ubuntu driver that the cable must be connected to an active link at boot time for the card to work ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798))

---

### Post by fatsheep on 2007-08-19
> **noob12 said:**
> fatsheep:  Try this.  Shutdown, power down.  Unplug (cuts power to card if wake-on-lan power is maintained).  Wait 15 seconds.  Plug in.  Boot ubuntu.

If this works, you are probably affected by the following (excerpt from gentoo wiki [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)).  Note the second and third paragraphs.  Then read the Windows-side workaround in the first paragraph.



I'm hopting that's your issue. If that doesn't work, I'm not seeing any evident issues in the dmesg.  Can you confirm that your ethernet cable is connected at boot?  There is also a  known bug in the Ubuntu driver that the cable must be connected to an active link at boot time for the card to work ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798))

**1.**  I can confirm that ethernet cable is connected at boot time.
**2.**  I shut down the computer, unplugged it for a minute or two and then rebooted and I now get a lit LED on the NIC in Ubuntu.  I also get a "Connection Established" message in Ubuntu.  HOWEVER, I still get no connection, google does not load in firefox.  :confused:  I think we are headed in the right direction, what should I do next?

---

### Post by noob12 on 2007-08-19
That's good.  

I will be away from the forum for a week, so unable to respond.  I hope some of the other folks who've already contributed to this thread can help you along through the rest.

With the link now working, you might try manually to configure the address,gateway, and DNS servers using System | Administration | Networking and see if you can get connectivity that way.

The following will probably provide some help to whoever helps you diagnose the problem, but you could also wait till someone asks directly.
```

sudo ethtool eth0

ifconfig -a

cat /etc/network/interfaces

route -n

grep dhclient /var/log/syslog

```

Good luck.

---

### Post by fatsheep on 2007-08-24
I just retried cold booting the computer and the internet now works!  I disabled wake-on LAN and the internet in Ubuntu is working so hopefully it will continue to do so ( *crosses fingers* ).  Thanks for all the help. :)

---

### Post by radoslav_sm_bg on 2007-09-20
> **Mrs Twaddle said:**
> I've just had this problem,.

Did you just get a windows update?
I did, and that is the ONLY thing that has changed on my connection (I use dual boot)
Linux will NOT connect, windows does no problem.
"Realtek Semiconductor Corp. - Networking - Realtek RTL8139/810x Family Fast Ethernet NIC" is the update i had today....
i'm going to try uninstalling it to see if that helps.

I had the same problem on my machine.
I'm using the same ethernet device and have two operating sysems - Ubuntu and Windows XP.
Try enabling the 'Wake-On-LAN After Shutdown' option. It worked with me.
If this option is set to 'disable' then when you shut down Windows it turns off the ethernet device and Ubuntu does not switch it off when it boots. I think so. Correct me if i I'm wrong.

---

### Post by railz68 on 2007-09-26
hi, I'm looking into getting the Gigabyte P35-DS3P.

Curious about this bug. Does it happen each and every time you boot from windows xp to ubuntu ?.

Or do just have to change the "wake on lan" once in windows and it's fixed ?.

---

### Post by noob12 on 2007-09-26
If it's this problem  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)  then the wake-on-lan setting should fix it.

---

### Post by fatsheep on 2007-09-26
> **railz68 said:**
> hi, I'm looking into getting the Gigabyte P35-DS3P.

Curious about this bug. Does it happen each and every time you boot from windows xp to ubuntu ?.

Or do just have to change the "wake on lan" once in windows and it's fixed ?.


Wake on lan fixes it.

---

### Post by Banny706 on 2007-09-27
Hi guys,  for a few weeks now, I haven't been able to connect to the internet through my Ubuntu installation on my new computer, therefore I still have a nice shiny new install.  Last night while looking through the forums, I stumbled across this thread and decided to check it out.  My ethernet controller is a [COLOR="Blue"]Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)[/COLOR] as well.  I booted back to Windows and enabled the [COLOR="Blue"]'Wake on LAN after shutdown' [/COLOR]option of my ethernet controller and rebooted to Ubuntu.  I crossed my fingers and hoped for the best.  What was even more pleasently surprising is that I connected to the internet through my [COLOR="blue"]Belkin Wireless G F5D7230-4 Router [/COLOR]which my computer is hard wired to  (My old computer connects wirelessly).  It worked right out of the box.  No more Pon and Poffing for me.  Thanks a whole bunch to[COLOR="Red"]'radoslav_sm_bg' and 'noob12'[/COLOR].  You guys :guitar: \\:D/ :biggrin:

---

### Post by geoff123 on 2007-09-30
I also had the same problem with no internet (and no light on card). It came after upgrading to gutsy, but not immediately (after a few reboots and removing old packages).  I do not have Windows installed on this computer. 

This fixed it as noted above....
sudo /etc/init.d/networking stop
sudo modprobe -r r8169
sudo modprobe r8169
sudo /etc/init.d/networking start

Hope this helps someone..

---

### Post by fatvampire on 2007-10-06
hay every body!

i followed this thread all the way, with amazing resamblance to fatsheep's problam - all hardware and outputs was the same - except that i'm working from the LIVEcd (doe's it makes a difference??)  but when  fatsheep's network connection started to work, (a lit LID & internet connection) mine computer still won't light the ethernet cable LID even thugh i can see my card. and the modem work's fine for another computer...

can anybody H-E-L-P!?

thanks...

---

### Post by DarinB on 2007-10-08
these are my results can someone help me get on-line i have a wired set up i can go online with another feisty machine using the same wire.


darin@darin-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03) 
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) 
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) 
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02) 
01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09) 
01:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30) 
01:0b.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08) 
darin@darin-desktop:~$

---

### Post by talent03 on 2007-10-12
I just came across this same problem in the Gutsy Release Candidate... which made me want to bitch and complain because I had never had this problem. But what you guys mentioned to do... fixed it. Thank you... to the community. :)

---

