---
title: "NIC IRQ gets &quot;disabled&quot;, supposedly after being idle for too long"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by distort on 2007-07-09
Hi,

I'm having a problem with my integrated VIA Rhine Network interface. It seems that when it's idle for too long, it's IRQ gets disabled and it can't be used any more until the next reboot.

Here's the relevant dmesg output:

[  240.579485] eth0: no IPv6 routers present
[ 1858.832501] irq 19: nobody cared (try booting with the "irqpoll" option)
[ 1858.832538]  [<c01561b4>] __report_bad_irq+0x24/0x80
[ 1858.832565]  [<c0156449>] note_interrupt+0x239/0x270
[ 1858.832591]  [<c01556f0>] handle_IRQ_event+0x30/0x60
[ 1858.832610]  [<c0156b10>] handle_fasteoi_irq+0xc0/0xf0
[ 1858.832628]  [<c0105e00>] do_IRQ+0x40/0x80
[ 1858.832658]  [<c01043a3>] common_interrupt+0x23/0x30
[ 1858.832695]  [<f92500d8>] _nv000154rm+0x0/0x284 [nvidia]
[ 1858.832833]  [<c012ca59>] __do_softirq+0x59/0x100
[ 1858.832867]  [<c012cb6d>] do_softirq+0x6d/0x70
[ 1858.832879]  [<c012cd23>] irq_exit+0x43/0x50
[ 1858.832887]  [<c0105e05>] do_IRQ+0x45/0x80
[ 1858.832915]  [<c01043a3>] common_interrupt+0x23/0x30
[ 1858.832950]  [<c01200d8>] find_busiest_group+0x328/0x5c0
[ 1858.832958]  [<c0101216>] mwait_idle_with_hints+0x46/0x60
[ 1858.832973]  [<c0101230>] mwait_idle+0x0/0x20
[ 1858.832981]  [<c0101414>] cpu_idle+0x54/0xf0
[ 1858.832999]  [<c03df805>] start_kernel+0x375/0x430
[ 1858.833009]  [<c03df230>] unknown_bootoption+0x0/0x260
[ 1858.833048]  =======================
[ 1858.833050] handlers:
[ 1858.833052] [<f88abdd0>] (rhine_interrupt+0x0/0xb90 [via_rhine])
[ 1858.833065] Disabling IRQ #19

and uname -a:
Linux anonymous 2.6.20-15-lowlatency #2 SMP PREEMPT Sun Apr 15 07:39:03 UTC 2007 i686 GNU/Linux
The network interface is built-in on an asrock 775dual-880pro mainboard.
The Ubuntuversion is 7.04 feisty (Ubuntustudio)

This doesn't happen when I keep it busy, but when I let it sit there doing nothing for approx 15-30 minutes, the above problem occurs.

additional information about the hardware:

#lspci |grep -i rhine
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

#dmesg |grep rhine
[    3.321778] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker


Thanks for reading this,

d.

---

### Post by distort on 2007-07-12
The fact that I use Tor for Internet browsing seems to act as a workaround for said problem, maybe because a running Tor client keeps the network interface busy somehow, even when I'm not using the internet connection.
But as soon as Tor doesn't run and the interface is idle for some time, the problem occurs again.

---

### Post by morgan_greywolf on 2007-07-22
Hey!  I'm getting the same problem.  I have a Via Rhine (VT6102) onboard integreted NIC.  I'm also using Ubuntu Studio with the latest low-latency kernel.  After the NIC 'idles' for a long time, the kernel disables the IRQ, bringing the interface down.  I can fix it by:

```

ifconfig eth0 down
ifconfig eth0 up
```

and waiting for the NIC to get a DHCP from dhcpd.

Since this is my wife's computer, I'd rather not have to do this.  Seems that keeping the NIC busy with some background process might be okay, but this computer is used for sound processing, and sometimes you want to minimize on  backgroud tasks.

---

### Post by distort on 2007-08-29
That works, thanks.

I have also updated my kernel from low-latency to realtime (as described here: [https://wiki.ubuntu.com/RealTime/Feisty](https://wiki.ubuntu.com/RealTime/Feisty)), 
because this computer is also used mainly for sound processing. I'm not sure, but it seems that made this problem go away.

---

