---
title: "RTL8139 Card and forcedeth : Network Card all confused ..Help !"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by vidyut_vidyut on 2007-02-06
Hi,

I am trying to connect to my BroadBand ADSL connection using my Ethernet card ( Intex technologies RTL 8139 D ). I tried most of the things that were mentioned in many threads that .I read in the Forums :

* Configured Static IP Address, Gateway, Mask etc

* Tried Unloading forcedeth module ( using sudo modprobe -r forcedeth)  and then loading the drivers 8139cp.o and 8139too.o ( using sudo modprobe 8139cp and sudo modprobe 8139too)

* Tried the nvnet module too, but does not work

* Tried with Breezy, Dapper and Edgy still does not work

I suspect there is something is messed up with PCI bus, nVidia chipset and Network Driver mismatch.

First of all, ifconfig shows TX and RX of eth0 to be 0 :

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:2F:35:0A:D7  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe35:ad7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1197852 (1.1 MiB)  TX bytes:1197852 (1.1 MiB)


The output of lspci :

$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:08.0 Ethernet controller: Unknown device 1904:2031 (rev 01)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

The output of dmesg ( cut out the irrelevant stuff ) :

[4295102.495000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[4295102.497000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LKLN] -> GSI 22 (level, high) -> IRQ 22
[4295102.497000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4295103.010000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[4295103.156000] eth0: no link during initialization.
[4295113.903000] eth0: no IPv6 routers present

This is when the system is first booted. After i unload forcedeth and insert 8139too and 8139cp, dmesg shows :

[4297822.345000] ACPI: PCI interrupt for device 0000:00:04.0 disabled
[4297831.077000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4297832.941000] 8139too Fast Ethernet driver 0.9.27

Last the output of lshw :

-----
        *-network UNCLAIMED
             description: Ethernet controller
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             resources: iomemory:fe800000-fe800fff ioport:eff0-eff7 irq:22

------
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network UNCLAIMED
                description: Ethernet controller
                physical id: 8
                bus info: pci@01:08.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:fbe00000-fbe000ff ioport:d800-d8ff irq:10

Still I am not able to ping my gateway 192.168.1.1. What could be going wrong ?
I am at my wit's end having run out of ideas :-(.
Any pointers would be of great help !

Thanks !

---

### Post by vidyut_vidyut on 2007-02-06
I am able to connect to my modem using Win XP ( Dual Boot)  and also able to access the net on ubuntu using usbnet USB-Ethernet driver (eth1). But I wont be having the USB access for long as we are planning to share the internet connection using a Ethernet Hub ..please help

---

### Post by igorc on 2007-03-27
Hi,

I have the same problem with the same Realtek 8139 network card. It was working fine for 6 months on Ubuntu 6.06 kernel 2.6.15-23 and suddenly decided to stop. This card should work with 8139too driver or 8139cp which are already compiled in the 2.6.x kernels.

I did some goggling and it seams that a lot of users have the same problem with this card. It might be a problem related to:

- IRQ settings, ACPI or APIC according to this link:
[https://help.ubuntu.com/community/De...%7C%2](https://help.ubuntu.com/community/De...%7C%2) 8IRQ%29

- or duplicate driver problem: try booting with 8139cp driver (generic one) blacklisted in /etc/hotplug/blacklist file

- or parameter settings in the 8139too module.

You can try booting with the kernel parameters disabled like in the recommendations from the link above. Also can you please send the output of these commands:

# ifconfig
# ping <router_ip_address>
# dmesg | grep eth
# lspci -vv
# lsmod | grep 8139
# sudo lshw -class network
# sudo dhclient eth0
# modinfo 8139too

In case you have solved the problem could you post the solution please? Thanks!

Igor

---

