---
title: "Onboard NIC not working"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by Snowin on 2007-04-05
Hi,

I recently took the plunge and bought myself some new hardware.  I'm running an dual core Athlon 64 on an Asus M2N4-SLI motherboard.

Having taken on plunge, I decided to take another.  I grabbed a copy of Feisty Fawn, booted the live CD and installed.  The installation appeared to go fine (well I'm typing this from it anyway), and I rebooted the machine at the end of the install.

On logging in, I didn't have any connectivity out of the box.  ifconfig -a reveals:


```
eth0   Link encap:Ethernet  HWaddr 00:18:F3:7E:64:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xa000 
```

So to my mainly windows mind, that says that Feisty can see my NIC, but can't get a DHCP lease from my router. 

The network infrastructure isn't suspect (more than one machine and everything else down to the cable works).  I've also had Windows XP running OK with the hardware, no connectivity problems.

lspci reveals:
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 LE (rev a1)
```

After that I'm on a vanilla feisty install and dist-upgraded to 15:00 BST today.

I've bunged an old PCI RTL8139 in just to get connectivity, but i'd rather get the onboard NIC working before looking at setting up the wireless kit I've got.

Anybody got any ideas?

---

### Post by spd106 on 2007-04-05
Could you post the output of this command? ```
sudo lshw -class network
``` Maybe check dmesg or syslog for any errors.

---

### Post by Snowin on 2007-04-05
Ok,

 lshw -class network

```
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth1
       version: 10
       serial: 00:0e:2e:8c:16:c3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ac00-acff iomemory:fdfff000-fdfff0ff irq:5
```

Which is the working NIC that i bunged in to get connectivity.  

lshw has a little more information:
```

*-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@01:06.0
             logical name: eth1
             version: 10
             serial: 00:0e:2e:8c:16:c3
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: ioport:ac00-acff iomemory:fdfff000-fdfff0ff irq:5
     *-bridge DISABLED
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          logical name: eth0
          version: f3
          serial: 00:18:f3:7e:64:14
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: iomemory:fe02a000-fe02afff ioport:bc00-bc07

```

As to why it's disabled I origonally had no idea, it's on in the BIOS, but running ifdown/up eth0 puts the following to dmesg:

```
[ 7096.228000]  =======================
[ 7096.236000] IRQ handler type mismatch for IRQ 0
[ 7096.236000] current handler: timer
[ 7096.236000]  [<c01540fe>] setup_irq+0x12e/0x1e0
[ 7096.236000]  [<f88c0f00>] nv_nic_irq+0x0/0x2a0 [forcedeth]
[ 7096.236000]  [<c0154253>] request_irq+0xa3/0xc0
[ 7096.236000]  [<f88c04b7>] nv_request_irq+0x97/0x3a0 [forcedeth]
[ 7096.236000]  [<f88c19b9>] nv_open+0x2f9/0x4b0 [forcedeth]
[ 7096.236000]  [<c02843b1>] dev_open+0x31/0x70
[ 7096.236000]  [<c0282bac>] dev_change_flags+0xfc/0x130
[ 7096.236000]  [<c02c9221>] devinet_ioctl+0x551/0x6c0
[ 7096.236000]  [<c0283f3b>] dev_ifsioc+0xeb/0x360
[ 7096.236000]  [<c01f2099>] copy_to_user+0x29/0x50
[ 7096.236000]  [<c0277e9f>] sock_ioctl+0xbf/0x210
[ 7096.236000]  [<c0277de0>] sock_ioctl+0x0/0x210
[ 7096.236000]  [<c018269b>] do_ioctl+0x2b/0x90
[ 7096.236000]  [<c018275c>] vfs_ioctl+0x5c/0x2a0
[ 7096.236000]  [<c0182a12>] sys_ioctl+0x72/0x90
[ 7096.236000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[ 7096.236000]  =======================
```

and the following into /var/log/syslog:

```
Apr  5 20:35:04 owen-desktop kernel: [ 7096.172000]  =======================
Apr  5 20:35:04 owen-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Apr  5 20:35:04 owen-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Apr  5 20:35:04 owen-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Apr  5 20:35:04 owen-desktop dhclient: All rights reserved.
Apr  5 20:35:04 owen-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr  5 20:35:04 owen-desktop dhclient: 
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000] IRQ handler type mismatch for IRQ 0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000] current handler: timer
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [setup_irq+302/480] setup_irq+0x12e/0x1e0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [<f88c0f00>] nv_nic_irq+0x0/0x2a0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [request_irq+163/192] request_irq+0xa3/0xc0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [<f88c04b7>] nv_request_irq+0x97/0x3a0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [<f88c19b9>] nv_open+0x2f9/0x4b0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [dev_open+49/112] dev_open+0x31/0x70
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [dev_change_flags+252/304] dev_change_flags+0xfc/0x130
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [devinet_ioctl+1361/1728] devinet_ioctl+0x551/0x6c0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [dev_ifsioc+235/864] dev_ifsioc+0xeb/0x360
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [copy_to_user+41/80] copy_to_user+0x29/0x50
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [do_ioctl+43/144] do_ioctl+0x2b/0x90
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Apr  5 20:35:04 owen-desktop kernel: [ 7096.228000]  =======================
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000] IRQ handler type mismatch for IRQ 0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000] current handler: timer
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [setup_irq+302/480] setup_irq+0x12e/0x1e0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [<f88c0f00>] nv_nic_irq+0x0/0x2a0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [request_irq+163/192] request_irq+0xa3/0xc0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [<f88c04b7>] nv_request_irq+0x97/0x3a0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [<f88c19b9>] nv_open+0x2f9/0x4b0 [forcedeth]
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [dev_open+49/112] dev_open+0x31/0x70
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [dev_change_flags+252/304] dev_change_flags+0xfc/0x130
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [devinet_ioctl+1361/1728] devinet_ioctl+0x551/0x6c0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [dev_ifsioc+235/864] dev_ifsioc+0xeb/0x360
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [copy_to_user+41/80] copy_to_user+0x29/0x50
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [sock_ioctl+191/528] sock_ioctl+0xbf/0x210
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [sock_ioctl+0/528] sock_ioctl+0x0/0x210
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [do_ioctl+43/144] do_ioctl+0x2b/0x90
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [vfs_ioctl+92/672] vfs_ioctl+0x5c/0x2a0
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Apr  5 20:35:04 owen-desktop kernel: [ 7096.236000]  =======================
Apr  5 20:35:05 owen-desktop dhclient: Listening on LPF/eth0/00:18:f3:7e:64:14
Apr  5 20:35:05 owen-desktop dhclient: Sending on   LPF/eth0/00:18:f3:7e:64:14
Apr  5 20:35:05 owen-desktop dhclient: Sending on   Socket/fallback
Apr  5 20:35:05 owen-desktop dhclient: receive_packet failed on eth0: Network is down
Apr  5 20:35:07 owen-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr  5 20:35:07 owen-desktop dhclient: send_packet: Network is down

```

---

### Post by Snowin on 2007-04-06
Right, I've had a bit more of a play this morning.

I've got sound and ethernet working again by adding the following options to the boot options for the kernel:

"acpi=off"

The next thing i'll be doing is seeing if can get all of the kit working, with CPU scaling as well, which something informed me was now broken.

---

