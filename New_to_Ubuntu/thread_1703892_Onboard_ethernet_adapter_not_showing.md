---
title: "Onboard ethernet adapter not showing"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by jasperto on 2011-03-09
Hi everyone, I haven't been able to solve this problem despite several days on Google, was hoping for some feedback.  Thanks in advance.

Install: Ubuntu 10.0.4
Motherboard: GA-MA785GM-US2H (Realtek 8111C)

lspci ouput:
> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]lshw -C network output:
> 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:09:a1:08:c1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.12 multicast=yes wireless=IEEE 802.11bgnifconfig -a output
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1536 (1.5 KB)  TX bytes:1536 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:09:a1:08:c1  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9ff:fea1:8c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84629 errors:0 dropped:306 overruns:0 frame:0
          TX packets:58190 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)content of /etc/init/rc.conf:
> 
# rc - System V runlevel compatibility
#
# This task runs the old System V-style rc script when changing between
# runlevels.

description    "System V runlevel compatibility"
author        "Scott James Remnant <scott@netsplit.com>"

start on runlevel [0123456]
stop on runlevel [!$RUNLEVEL]

export RUNLEVEL
export PREVLEVEL

console output
env INIT_VERBOSE

task

exec /etc/init.d/rc $RUNLEVEL


---

### Post by jasperto on 2011-03-10
bump?  Would really appreciate any help

---

### Post by grahammechanical on 2011-03-10
I have just searched for your motherboard on the Gigabyte web site and according to the specifications list your board has on the back panel 1 x RJ45 port. This is your ethernet port. So, you do have ethernet on the motherboard. I was just checking.

So, why does it not show up in the listings from those commands? The only thing that I can think of is that the ethernet adapter may not be enabled in the BIOS.

The thing that really surprises me it that you have wireless working but not ethernet.

Have you tried the code ifup -v eth0?

Regards.

---

### Post by Lord Quinny on 2011-07-10
How is this marked as solved? Where's the solution?

My ethernet was working fine until I booted up today and there is no ethernet detected at all, with the same results as the original poster. There is no ethernet in lspci.
No eth0 anywhere. No network or eth in dmesg.

Does it mean a hardware failure?

---

### Post by Lord Quinny on 2011-07-11
No idea what's going on. It's working fine since I booted up today.

---

