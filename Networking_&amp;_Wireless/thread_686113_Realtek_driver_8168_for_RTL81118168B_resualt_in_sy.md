---
title: "Realtek driver 8168 for RTL8111/8168B resualt in system hung on Gigabit transfer"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by kyriakos1977 on 2008-02-02
Ok my first post...

This is a problem about RTL8111/8168B I could not solve. I have read ALL the posts on this forum and other.

First of all this is a gigabit only problem on 100mbit both drivers and all kernels work flawlessly.

The problem:
On gigabit transfer ftp (or samba) process freezes cannot be killed (not even with -9) the load goes hi as 6 and the server doesn't respond even in soft reboot, it hung's on trying to ifdown eth0.
with driver r8169 i got the following on syslog  (not always)

```
Jan 24 23:20:32 ermis kernel: [ 1637.147131] swapper: page allocation failure. order:1, mode:0x4020
Jan 24 23:20:32 ermis kernel: [ 1637.147135] Pid: 0, comm: swapper Not tainted 2.6.24-4-server #1
Jan 24 23:20:32 ermis kernel: [ 1637.147137]
Jan 24 23:20:32 ermis kernel: [ 1637.147137] Call Trace:
Jan 24 23:20:32 ermis kernel: [ 1637.147139]  <IRQ>  [__alloc_pages+0x2dd/0x3b0] __alloc_pages+0x2dd/0x3b0
Jan 24 23:20:32 ermis kernel: [ 1637.147158]  [do_IRQ+0x80/0x100] do_IRQ+0x80/0x100
Jan 24 23:20:32 ermis kernel: [ 1637.147163]  [new_slab+0x222/0x260] new_slab+0x222/0x260
Jan 24 23:20:32 ermis kernel: [ 1637.147168]  [__slab_alloc+0x2dc/0x400] __slab_alloc+0x2dc/0x400
Jan 24 23:20:32 ermis kernel: [ 1637.147172]  [r8169:__netdev_alloc_skb+0x2b/0x2fa0] __netdev_alloc_skb+0x2b/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147176]  [r8169:__netdev_alloc_skb+0x2b/0x2fa0] __netdev_alloc_skb+0x2b/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147180]  [__kmalloc_node_track_caller+0x121/0x130] __kmalloc_node_track_caller+0x121/0x13
0
Jan 24 23:20:32 ermis kernel: [ 1637.147185]  [ipv6:__alloc_skb+0x7b/0x4f0] __alloc_skb+0x7b/0x160
Jan 24 23:20:32 ermis kernel: [ 1637.147189]  [r8169:__netdev_alloc_skb+0x2b/0x2fa0] __netdev_alloc_skb+0x2b/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147196]  [r8169:rtl8169_rx_fill+0xb9/0x1c0] :r8169:rtl8169_rx_fill+0xb9/0x1c0
Jan 24 23:20:32 ermis kernel: [ 1637.147203]  [r8169:rtl8169_rx_interrupt+0x42a/0x600] :r8169:rtl8169_rx_interrupt+0x42a/0x600
Jan 24 23:20:32 ermis kernel: [ 1637.147210]  [r8169:rtl8169_interrupt+0x219/0x3c0] :r8169:rtl8169_interrupt+0x219/0x3c0
Jan 24 23:20:32 ermis kernel: [ 1637.147217]  [handle_IRQ_event+0x34/0x70] handle_IRQ_event+0x34/0x70
Jan 24 23:20:32 ermis kernel: [ 1637.147221]  [rcu_needs_cpu+0x3d/0x50] rcu_needs_cpu+0x3d/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147225]  [handle_edge_irq+0xdc/0x150] handle_edge_irq+0xdc/0x150
Jan 24 23:20:32 ermis kernel: [ 1637.147229]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
Jan 24 23:20:32 ermis kernel: [ 1637.147233]  [mwait_idle+0x0/0x50] mwait_idle+0x0/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147236]  [default_idle+0x0/0x40] default_idle+0x0/0x40
Jan 24 23:20:32 ermis kernel: [ 1637.147239]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Jan 24 23:20:32 ermis kernel: [ 1637.147241]  <EOI>  [mwait_idle+0x42/0x50] mwait_idle+0x42/0x50
Jan 24 23:20:32 ermis kernel: [ 1637.147249]  [cpu_idle+0x6f/0xc0] cpu_idle+0x6f/0xc0
Jan 24 23:20:32 ermis kernel: [ 1637.147255]

```

I Have tried 
both drivers 
1. r8169 7.10 Gutsy Gibbon 86x64 server native
2. Realtek r8168-8.004.00 compiled as described in 
[http://ohioloco.ubuntuforums.org/showthread.php?t=671614]("http://ohioloco.ubuntuforums.org/showthread.php?t=671614")
the module r8168 is properly installed and 8169 is deinstalled

I upgraded the kernel to 2.6.24-5 hardy with the r8169 driver. Same problem

changed PSU (just to be sure)

The problem is still there and the funny thing is that on the first gigabit trancfer I copied 2 Terrabites in a few hours with transfer rates of 60 to 110 Mbytes/sec  between 2 raid 5 arrays and of course a gigabit switch (3Com).

The only solution i have left is a pci gigabit NIC !

I thank you all in advance

File Server
OS: 7.10 Gutsy Gibbon 86x64 Server
GIGABYTE GA-P35C-DS3R motherboard. 
The Intel P35 chipset has an ICH-9 SATA controller with 6 X 500 GB WD aaks500 on software raid 5 = 2.5 Tbytes XFS

---

