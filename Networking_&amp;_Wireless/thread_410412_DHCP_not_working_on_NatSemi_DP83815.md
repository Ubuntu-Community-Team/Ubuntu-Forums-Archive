---
title: "DHCP not working on NatSemi DP83815"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by whfrazier on 2007-04-15
I'm a noob to ubuntu with very little linux experience, used redhat many years ago
I've installed Ubuntu 6.10 (Edgy) on a Compaq laptop that has a broken CD drive and no floppy. Installed from hard drive using Grub and alternative iso. 
Eth0 is wireless "Broadcom Corp BCM4306 802.11b/g" will need ndiswrapper for that i think
Eth1 is wired "Nationla Semiconductor DP83815 (MacPhyter)"
My router is a DLink DI-624 setup for DHCP, also switched ethernet cables 3 times and they work on the other 2 machines.

Trying to get Eth1 going right now so I can download drivers for Eth0.
I set Eth1 up DCHP and reset and it didnt get an IP. sudo /etc/init.d/networking restart claims no DCHP offer was recived. but the router is catching the mac address in log and even had an ip assigned. The networking GUI crashes now and i've been using the terminal to play with it. Trying to figure out what is wrong, hoping someone ahd some ideas.

```
/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

iface eth0 inet dhcp
wireless-essid dlink
 
```

Result from ifconfig -a
```
eth1      Link encap:Ethernet  HWaddr 00:0D:9D:5E:A0:4C
          inet6 addr: *skipped* Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1088 overruns:0 frame:0
          TX packets:56 errors:0 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14400 (14.0 KiB)
          Interrupt:10 Base Address:0xa000
```

Not sure what other info is needed, just ask, Thanks

---

### Post by whfrazier on 2007-04-15
sudo ethtool eth1 returns

```

Settings for eth1:
           Speed: 100Mb/s
           Duplex: Full
           Port: Twisted Pair
           PHYAD: 1
           Transceiver: internal
           Auto-negotiation: on
           Supports Wake-on: pumbags
           Wake-on: ub
           Current Message Level: 0x000040c5 (16581)
           Link Detected: Yes
```

---

### Post by whfrazier on 2007-04-15
I tried setting a static IP but I still couldnt ping the router. Also disabled IPv6 with no effect. Still just trying to get the wired ethernet (eth1) working.

---

### Post by whfrazier on 2007-04-17
Ok, I reinstalled 6.10 to correct any mistakes I had made and to setup my partitions better (/home has its own). I went ahead and assigned it 192.168.0.100, still didnt work. Did some reading and found that my DLink DI-624 doesnt like Ipv6, fresh install so I tried it.

[http://paulsiu.wordpress.com/2006/12/28/unable-to-connect-linux-computer-to-dlink-di-624-router-due-to-ipv6/](http://paulsiu.wordpress.com/2006/12/28/unable-to-connect-linux-computer-to-dlink-di-624-router-due-to-ipv6/)
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

I'm watching the DHCP menu of the router from my XP computer, and when Ubuntu rebooted, it showed up on the list!

got in terminal and did

ip a | grep inet6
no return

ifconfig eth1 gave me
```

eth1  Link:Ethernet HWaddr 00 Link encap:Ethernet  HWaddr 00:0D:9D:5E:A0:4C
          inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:43 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:672 (672.0 KiB)
          Interrupt:10 Base Address:0x8000
```
Still had dropped packed on RX so I did
sudo ifconfig eth1 down , then sudo eth1 up , then sudo ifconfig eth1 returned
```

eth1  Link:Ethernet HWaddr 00 Link encap:Ethernet  HWaddr 00:0D:9D:5E:A0:4C
          inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:115 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3332 (3.2 KiB)  TX bytes:1344 (1.3 KiB)
          Interrupt:10 Base Address:0x8000
```
Got excited because is saw packets recieved, was about to try and ping 192.168.0.1 when this popped up
```

[17179845.044000] irq 10: nobody cared (try booting with "irqpoll" option)
[17179845.044000] handlers:
[17179845.044000] [<dc89f230>] (ohci_irq_handler+0x0/0x990 [ohci1394])
[17179845.044000] [<dc93f830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17179845.044000] [<dc93f830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17179845.044000] [<dcbe2890>] (radeon_driver_irq_handler+0x0/0xc0 [radeon])
[17179845.044000] [<dc8e3460>] (intr_handler+0x0/0xd0 [natsemi])
[17179845.044000] Disabling IRQ #10
```

Hoping someone has some ideas or things i need to check.

---

### Post by whfrazier on 2007-04-17
ACK!! I got it working, then the Kernal disabled the IRQ...

Checked route and got...nothing, so I did
sudo ifconfig eth1 inet down
sudo ifconfig eth1 inet up 192.168.0.2 broadcast 192.168.0.255
sudo route add -net 10.0.0.0 netmask 255.0.0.0 gw 192.168.0.1 dev eth1
route
```
Kernel IP routing table
Destination   Gateway        Genmask              Flags    Metric Ref   Use   Iface
localnet         *                    255.255.255.0      U         0         0       0      eth1
10.0.0.0       192.168.0.1  255.0.0.0             UG        0         0       0      eth1
```
still couldnt ping out so i did
sudo ifup eth1
sudo ifdown eth1  (which reset it back to DHCP but the route stuff I added stayed)
it returned "DCHPOFFER from 192.168.0.1
bound to 192.168.0.1"
got excited, ping 192.168.0.1 and I got returns!!
couple seconds later before I typed anything....
Ubuntu-Laptop kernel: [17190971.752000] Disabling IRO #10

couldnt ping 192.168.0.1 again...

So, why is it disabling the IRQ?
 I assume it will work ok if I stop that, taking a break before I break the computer now.

---

### Post by chili555 on 2007-04-18
Man, oh man! You have a confused computer here:
[LIST]
[*]ethernet is eth1 while wireless is eth0
[*]router offered its OWN IP address
[*]IRQ 10 disabled
[/LIST]Let's take a look at:```
sudo lshw -C network
cat /etc/iftab
cat /etc/network/interfaces
lsmod | grep natsemi
```Also, please look in the computer's BIOS and see if IRQ's are explicitly called or set to AUTO. Change them to AUTO if they are not.

Let's see if we can tune this hotrod up.

---

### Post by whfrazier on 2007-04-18
Thank you for replying and helping.

Here is the information you requested
```
whfrazier@Ubuntu-Laptop:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:d4002000-d4003fff irq:255
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth1
       version: 00
       serial: 00:0d:9d:5e:a0:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=full link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d4006000-d4006fff irq:10

```
> whfrazier@Ubuntu-Laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:90:4b:42:4d:de arp 1
eth1 mac 00:0d:9d:5e:a0:4c arp 1

```
whfrazier@Ubuntu-Laptop:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
#       address 192.168.0.100
#       netmask 255.255.255.0
#       network 192.168.0.0
#       broadcast 192.168.0.255
#       gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

auto eth1


```
> whfrazier@Ubuntu-Laptop:~$ lsmod | grep natsemi
natsemi                30688  0 




There are no IRQ options in the BIOS, in fact there are almost no options in there besides basic hard drive, time and boot options.

I tried several times by rebooting and getting the eth1 to work (by method 2 posts up) and did
sudo apt-get update , but it would get about 5 downloaded and then the IRQ would be disabled. I am thinking it is a acpi problem, I tried noapic, acpi=off, acpi=noirq, acpi_irq_balance. None ever stopped the IRQ being disabled but did vary when. IRQ #10 usually is not disabled until I start messing with eth1.
 
eth0 and eth1 are how the installer set them up and I did not change it.

The router offered 192.168.0.100, I think that was a typo, the logs above are copied and pasted into a text file, just put the hard drive in my xp machine to get them here so there were no mistakes.

---

### Post by chili555 on 2007-04-18
i feel better about the IP address, but we still have a naughty computer! Let's try a few other things. First, when you can get connected, and IRQ #10 gets disabled, open a terminal and do:```
sudo cat /var/log/messages | grep IRQ
```See if there is any mention of IRQ #10 towards or at the end. See what the lines are leading up to the disable. You might also do:```
dmesg | grep IRQ
```Look for any conflicts or complaints about IRQ #10.

Please also try another boot parameter:```
pci=routeirq
```Post back and let us know.

---

### Post by whfrazier on 2007-04-18
With pci=routeirq it disabled IRQ #10 on startup.

sudo cat /var/log/messages | grep IRQ
trimmed it down to the ones in the last hour
```
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.352000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.352000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.352000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.352000] ACPI: PCI Interrupt Link [LNK3] (IRQs *7 10)
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.356000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.356000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.356000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.356000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.356000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] PCI: Using ACPI for IRQ routing
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 7
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 7 (level, low) -> IRQ 7
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 7 (level, low) -> IRQ 7
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: Unable to derive IRQ for device 0000:00:10.0
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.372000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.376000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.808000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179571.808000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179574.492000] ACPI: Unable to derive IRQ for device 0000:00:10.0
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179577.256000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.000000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.000000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.000000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.052000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d4005800-d4005fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.052000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.160000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 7 (level, low) -> IRQ 7
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.264000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179578.264000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179591.528000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179591.532000] natsemi eth0: NatSemi DP8381[56] at 0xd4006000 (0000:00:12.0), 00:0d:9d:5e:a0:4c, IRQ 10, port TP.
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179591.644000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179591.772000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
Apr 18 17:07:27 Ubuntu-Laptop kernel: [17179593.636000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
Apr 18 17:07:29 Ubuntu-Laptop kernel: [17179603.768000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:10:04 Ubuntu-Laptop kernel: [17179758.784000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Apr 18 17:10:04 Ubuntu-Laptop kernel: [17179758.784000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Apr 18 17:10:04 Ubuntu-Laptop kernel: [17179758.784000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK3] (IRQs *7 10)
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.624000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.628000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.628000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.628000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.640000] PCI: Using ACPI for IRQ routing
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.644000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179574.644000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179575.080000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179575.080000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179575.080000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179577.776000] ACPI: Unable to derive IRQ for device 0000:00:10.0
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179580.536000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179580.536000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.280000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.280000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.280000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.336000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d4005800-d4005fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.336000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.440000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 7
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.440000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 7 (level, low) -> IRQ 7
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.544000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179581.544000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179594.676000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179594.676000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179594.680000] natsemi eth0: NatSemi DP8381[56] at 0xd4006000 (0000:00:12.0), 00:0d:9d:5e:a0:4c, IRQ 10, port TP.
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179595.184000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179595.312000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179596.680000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
Apr 18 17:19:09 Ubuntu-Laptop kernel: [17179596.680000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
Apr 18 17:19:11 Ubuntu-Laptop kernel: [17179606.920000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
Apr 18 17:19:11 Ubuntu-Laptop kernel: [17179606.920000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
Apr 18 17:21:34 Ubuntu-Laptop kernel: [17179749.980000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Apr 18 17:21:34 Ubuntu-Laptop kernel: [17179749.980000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Apr 18 17:21:34 Ubuntu-Laptop kernel: [17179749.980000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30

```

```
whfrazier@Ubuntu-Laptop:~$ dmesg | grep IRQ
[17179574.640000] PCI: Using ACPI for IRQ routing
[17179574.644000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[17179574.644000] PCI: setting IRQ 11 as level-triggered
[17179574.644000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179575.080000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179575.080000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[17179575.080000] PCI: setting IRQ 10 as level-triggered
[17179575.080000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[17179577.776000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179580.536000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[17179580.536000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179581.280000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
[17179581.280000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179581.280000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
[17179581.280000] Disabling IRQ #10
[17179581.336000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d4005800-d4005fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179581.336000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179581.440000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 7
[17179581.440000] PCI: setting IRQ 7 as level-triggered
[17179581.440000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 7 (level, low) -> IRQ 7
[17179581.544000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179581.544000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
[17179594.676000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[17179594.676000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[17179594.680000] natsemi eth0: NatSemi DP8381[56] at 0xd4006000 (0000:00:12.0), 00:0d:9d:5e:a0:4c, IRQ 10, port TP.
[17179595.184000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179595.312000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[17179596.680000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[17179596.680000] PCI: setting IRQ 5 as level-triggered
[17179596.680000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[17179606.920000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[17179606.920000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[17179749.980000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
[17179749.980000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179749.980000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
[17179749.980000] Disabling IRQ #10

```

---

### Post by whfrazier on 2007-04-19
Problem solved! Thanks again for your help, the wired ethernet worked on install of Ubuntu Feisty!

---

