---
title: "network stops after a while"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by hutxubix on 2008-01-21
Hi!

In a computer AMD64 Athlon X2 where I had before doble boot XP/Debian and everything was fine, I have now double boot XP/Ubuntu 7.10. and I have a problem with the network: After a while (can be 1 hour or 6 hours) the net just stops working. Is not a problem of hardware because on the rest of OSs this does not happen.

(Note: I have working a 3Com 3c90SC-TX/TX-M (Tornado) because the SiS 190 On board gave me problems in Debian and now, Ubuntu doesn't like it either though it recognizes it)

Any idea about the ' random stopping' problem?

Thanks

---

### Post by rkane1226 on 2008-03-27
My AMD64 machine (but running 32 bit Ubuntu 7.10) Compaq R4000 has the same problem.  

I have tried both the restricted drivers available for the Broadcom Chipset and ndiswrappers and both exhibit the same problem.

The problem seems new over the last month, however, rolling back to older versions of drivers and the network manager does not seem to help.

---

### Post by mindfall903 on 2008-04-06
Hi

I have the same problem with my AMD 64bit installation (Ubuntu 7.04)

Networking stops after a while (can be 30min up to a couple of hours). Nothing I try brings networking back. In this forum I found another post which suggested to run this in the CLI:

sudo /etc/init.d/dbus restart

which runs:

 * Stopping System Tools Backends system-tools-backends [ OK ]
 * Stopping network events dispatcher NetworkManagerDispatcher [ OK ]
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon [ OK ]
 * Stopping network connection manager NetworkManager [ OK ]
 * Stopping DHCP D-Bus daemon dhcdbd [ OK ]
 * Stopping Hardware abstraction layer hald [ OK ]
 * Stopping system message bus dbus [ OK ]
 * Starting system message bus dbus [ OK ]
 * Starting Hardware abstraction layer hald [ OK ]
 * Starting DHCP D-Bus daemon dhcdbd [ OK ]
 * Starting network connection manager NetworkManager [ OK ]
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon [ OK ]
 * Starting network events dispatcher NetworkManagerDispatcher [ OK ]
 * Starting System Tools Backends system-tools-backends [ OK ]

this *should* have the same effect as a reboot but it doesn't. In the end I just have to reboot.
 A colleague suggested this is an AMD problem.
Running 'lspci' gives returns the following networking card:

05:06.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)

But still, no clue on how to fix it....

---

### Post by hutxubix on 2008-04-29
I still have the same problem. Any advance with this?

---

### Post by mackyman on 2008-05-15
I have the same problem since Hardy... But this is the first time I have the AMD64 install.

I guess this indicates that it's a AMD64 specific problem ( since everyone have a AMD64 install and even older versions have the same problem )

As far as I have analyzed it, seems to be a problem or conflict in IRQ, as the last output from dmesg is:

```
[ 2464.295600] irq 23: nobody cared (try booting with the "irqpoll" option)
[ 2464.295608] Pid: 15942, comm: glxgears Tainted: P        2.6.24-16-generic #1
[ 2464.295610] 
[ 2464.295610] Call Trace:
[ 2464.295612]  <IRQ>  [<ffffffff8027ad8e>] __report_bad_irq+0x1e/0x80
[ 2464.295637]  [<ffffffff8027b09d>] note_interrupt+0x2ad/0x2e0
[ 2464.295644]  [<ffffffff8027bbe1>] handle_fasteoi_irq+0xa1/0x110
[ 2464.295839]  [<ffffffff8853fb15>] :nvidia:_nv004178rm+0x1f/0x27
[ 2464.295847]  [<ffffffff8020ef6b>] do_IRQ+0x7b/0x100
[ 2464.295851]  [<ffffffff8020c891>] ret_from_intr+0x0/0xa
[ 2464.295855]  [<ffffffff803d4f90>] pci_conf1_read+0x0/0x100
[ 2464.295862]  [<ffffffff80243220>] __do_softirq+0x60/0xe0
[ 2464.295869]  [<ffffffff8020d50c>] call_softirq+0x1c/0x30
[ 2464.295872]  [<ffffffff8020ed25>] do_softirq+0x35/0x90
[ 2464.295875]  [<ffffffff802431b8>] irq_exit+0x88/0x90
[ 2464.295878]  [<ffffffff8020ef70>] do_IRQ+0x80/0x100
[ 2464.295881]  [<ffffffff8020c891>] ret_from_intr+0x0/0xa
[ 2464.295883]  <EOI> 
[ 2464.295892] handlers:
[ 2464.295893] [<ffffffff8809f300>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 2464.295910] [<ffffffff880f1d70>] (rhine_interrupt+0x0/0x7f0 [via_rhine])
[ 2464.295916] Disabling IRQ #23
[ 2506.626178] NETDEV WATCHDOG: eth0: transmit timed out
[ 2506.626326] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[ 2506.627003] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

Would be great if someone who know more could confirm or kick down my suspicions so that I know if I should install x86 version instead.

//Markus

---

### Post by rmccarri on 2008-05-17
I'm running Ubuntu Hardy i386 on a computer with an AMD 64bit Athlon processor.  I'm having the same problem, but only after a recent series of updates.

---

### Post by mackyman on 2008-05-21
Seems like there are no answer to this problem... And none who really have a clue...

I guess its time for me too do the deep-dive in the distro-watch again for a while and wait this problem is solved

---

### Post by sthenley on 2008-05-26
This problem is mostly ACPI related. First, try to disable any ACPI 2.0 extensions at BIOS (solve to me on a Fedora Host).

You also can try this:
> ethtool -K eth0 tso off

If the output shows anything like "*Cannot set device tcp segmentation offload settings: Operation not supported*", You can do this via module parameter:
> options your_3com_module_name seg_offload=0

Still having problems?

- Check if the kernel module of eth0 is correct for your device. Try to update it.

- Might be an irq conflict. So, fix IRQ for eth0 related device on BIOS.

- Analyse **dmesg** output an good luck!

If solve, pls, tell us! :)

---

