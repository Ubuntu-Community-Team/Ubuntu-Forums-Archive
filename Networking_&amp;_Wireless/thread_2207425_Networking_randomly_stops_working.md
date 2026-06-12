---
title: "Networking randomly stops working"
date: 2014-02-23
forum: Networking &amp; Wireless
---

### Post by numeritos on 2014-02-23
I'm currently using Kubuntu 13.10 with all the latest updates. Around mid-January networking started to fail and randomly stop working. I have to restart the PC in order to have it properly functioning again (and when I restart, it fails on stopping some process so I have to manually restart using the restart button. 
I thought it might have been a problem with some update so I waited a month or so to create this thread since it doesn't stop working THAT often.

I use Kernel 3.11.0-17-generic (that's what 'uname -r' shows). 

This is what syslog shows before networking stopped working today:

```
Feb 23 14:19:19 kubuntu kernel: [179723.004032] ------------[ cut here ]------------
Feb 23 14:19:19 kubuntu kernel: [179723.004045] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.11.0/net/sched/sch_generic.c:260 dev_watchdog+0x1ef/0x200()
Feb 23 14:19:19 kubuntu kernel: [179723.004047] NETDEV WATCHDOG: eth0 (ATL1E): transmit queue 0 timed out
Feb 23 14:19:19 kubuntu kernel: [179723.004049] Modules linked in: parport_pc ppdev nfsd rfcomm auth_rpcgss bnep nfs_acl bluetooth nfs lockd sunrpc binfmt_misc fscache ext2 nvidia(POF) snd_hda_codec_hdmi sn$
Feb 23 14:19:19 kubuntu kernel: [179723.004108] CPU: 0 PID: 0 Comm: swapper/0 Tainted: PF          O 3.11.0-17-generic #31-Ubuntu
Feb 23 14:19:19 kubuntu kernel: [179723.004110] Hardware name: System manufacturer P5Q/P5Q, BIOS 0703    06/12/2008
Feb 23 14:19:19 kubuntu kernel: [179723.004112]  00000000 00000000 f6c0bec0 c1627735 f6c0bf00 f6c0bef0 c10526ae c188f708
Feb 23 14:19:19 kubuntu kernel: [179723.004118]  f6c0bf1c 00000000 c188f744 00000104 c15696bf c15696bf f653d000 00000000
Feb 23 14:19:19 kubuntu kernel: [179723.004123]  02ac71c8 f6c0bf08 c1052703 00000009 f6c0bf00 c188f708 f6c0bf1c f6c0bf40
Feb 23 14:19:19 kubuntu kernel: [179723.004129] Call Trace:
Feb 23 14:19:19 kubuntu kernel: [179723.004135]  [<c1627735>] dump_stack+0x41/0x52
Feb 23 14:19:19 kubuntu kernel: [179723.004141]  [<c10526ae>] warn_slowpath_common+0x7e/0xa0
Feb 23 14:19:19 kubuntu kernel: [179723.004143]  [<c15696bf>] ? dev_watchdog+0x1ef/0x200
Feb 23 14:19:19 kubuntu kernel: [179723.004146]  [<c15696bf>] ? dev_watchdog+0x1ef/0x200
Feb 23 14:19:19 kubuntu kernel: [179723.004149]  [<c1052703>] warn_slowpath_fmt+0x33/0x40
Feb 23 14:19:19 kubuntu kernel: [179723.004151]  [<c15696bf>] dev_watchdog+0x1ef/0x200
Feb 23 14:19:19 kubuntu kernel: [179723.004158]  [<c105da5d>] call_timer_fn+0x2d/0xe0
Feb 23 14:19:19 kubuntu kernel: [179723.004160]  [<c15694d0>] ? dev_deactivate_queue.constprop.35+0x50/0x50
Feb 23 14:19:19 kubuntu kernel: [179723.004164]  [<c105e9c9>] run_timer_softirq+0x179/0x220
Feb 23 14:19:19 kubuntu kernel: [179723.004167]  [<c15694d0>] ? dev_deactivate_queue.constprop.35+0x50/0x50
Feb 23 14:19:19 kubuntu kernel: [179723.004171]  [<c1057461>] __do_softirq+0xc1/0x1d0
Feb 23 14:19:19 kubuntu kernel: [179723.004175]  [<c162e4eb>] ? nmi_stack_correct+0x2f/0x34
Feb 23 14:19:19 kubuntu kernel: [179723.004178]  [<c10573a0>] ? remote_softirq_receive+0xb0/0xb0
Feb 23 14:19:19 kubuntu kernel: [179723.004181]  [<c10573a0>] ? remote_softirq_receive+0xb0/0xb0
Feb 23 14:19:19 kubuntu kernel: [179723.004183]  <IRQ>  [<c10576d5>] ? irq_exit+0x95/0xa0
Feb 23 14:19:19 kubuntu kernel: [179723.004188]  [<c1635658>] ? smp_apic_timer_interrupt+0x38/0x50
Feb 23 14:19:19 kubuntu kernel: [179723.004191]  [<c162e05c>] ? apic_timer_interrupt+0x34/0x3c
Feb 23 14:19:19 kubuntu kernel: [179723.004196]  [<c150be50>] ? cpuidle_enter_state+0x40/0xd0
Feb 23 14:19:19 kubuntu kernel: [179723.004199]  [<c150bf7e>] ? cpuidle_idle_call+0x9e/0x1d0
Feb 23 14:19:19 kubuntu kernel: [179723.004204]  [<c1016ded>] ? arch_cpu_idle+0xd/0x30
Feb 23 14:19:19 kubuntu kernel: [179723.004207]  [<c109fd51>] ? cpu_startup_entry+0x1c1/0x210
Feb 23 14:19:19 kubuntu kernel: [179723.004212]  [<c161e642>] ? rest_init+0x62/0x70
Feb 23 14:19:19 kubuntu kernel: [179723.004218]  [<c1973acd>] ? start_kernel+0x397/0x39d
Feb 23 14:19:19 kubuntu kernel: [179723.004220]  [<c197356d>] ? repair_env_string+0x51/0x51
Feb 23 14:19:19 kubuntu kernel: [179723.004223]  [<c1973394>] ? i386_start_kernel+0x137/0x13a
Feb 23 14:19:19 kubuntu kernel: [179723.004225] ---[ end trace d00d7a84d9d7634f ]---
Feb 23 14:19:19 kubuntu kernel: [179723.092033] ATL1E 0000:02:00.0 eth0: MAC state machine can't be idle since disabled for 10ms second
Feb 23 14:19:19 kubuntu NetworkManager[993]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Feb 23 14:19:19 kubuntu kernel: [179723.100262] ATL1E 0000:02:00.0 eth0: atl1e_configure failed, PCIE phy link down
Feb 23 14:19:23 kubuntu NetworkManager[993]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Feb 23 14:19:23 kubuntu NetworkManager[993]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Feb 23 14:19:24 kubuntu NetworkManager[993]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1100
Feb 23 14:19:24 kubuntu avahi-daemon[971]: Withdrawing address record for 192.168.1.100 on eth0.
Feb 23 14:19:24 kubuntu avahi-daemon[971]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
Feb 23 14:19:24 kubuntu avahi-daemon[971]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb 23 14:19:24 kubuntu NetworkManager[993]: <warn> DNS: plugin dnsmasq update failed
Feb 23 14:19:24 kubuntu NetworkManager[993]: <info> Removing DNS information from /sbin/resolvconf
Feb 23 14:19:24 kubuntu dnsmasq[1306]: setting upstream servers from DBus
Feb 23 14:19:25 kubuntu named[1126]: error (network unreachable) resolving 's.gateway.messenger.live.com/A/IN': 192.26.92.30#53
Feb 23 14:19:25 kubuntu named[1126]: error (network unreachable) resolving 's.gateway.messenger.live.com/A/IN': 192.43.172.30#53
```


And then it goes on with network unreachable error nonstop.

Any clues on what could be going on here?

---

### Post by ian-weisser on 2014-02-23
The kernel is recording a crash.
Either the update introduced a bug for your specific hardware that crashes the kernel module (driver),
Or your hardware has developed a fault that results in the crash.

One way to check is to downgrade to a previous kernel you used before mid-January. If the problem goes away, then you know that the problem was introduced by an upgrade. If the problem recurs, then replace your faulty hardware.

---

### Post by numeritos on 2014-02-24
> **ian-weisser said:**
> The kernel is recording a crash.
Either the update introduced a bug for your specific hardware that crashes the kernel module (driver),
Or your hardware has developed a fault that results in the crash.

One way to check is to downgrade to a previous kernel you used before mid-January. If the problem goes away, then you know that the problem was introduced by an upgrade. If the problem recurs, then replace your faulty hardware.

Forgot to say that when it's working lots of times the transfer rates are ridiculous (transferring through Samba at 1MB/s or so). Already tried downgrading to a few previous Kernels and the problem is still there. The networking device is onboard. Could it be failing independently of the rest of the motheboard?

---

### Post by ian-weisser on 2014-02-24
> **numeritos said:**
> Could it be failing independently of the rest of the motheboard?

Yes. A motherboard fault would likely occur during more activities than networking.

A hardware could be as simple as a bad solder or dislodged connector - easily fixed.
If it's an ethernet connection, also try a different cord, and try a different port in the switch/router at the other end.
If it's a wireless connection, it's often worth an hour to find out how to access the mini-PCI card and reseat it.
Rarely do loose connections result in kernel crashes (usually the device is simply unavailable), but cheap-and-easy solutions cost little, and sometimes do work.

---

### Post by numeritos on 2014-02-24
> **ian-weisser said:**
> Yes. A motherboard fault would likely occur during more activities than networking.

A hardware could be as simple as a bad solder or dislodged connector - easily fixed.
If it's an ethernet connection, also try a different cord, and try a different port in the switch/router at the other end.
If it's a wireless connection, it's often worth an hour to find out how to access the mini-PCI card and reseat it.
Rarely do loose connections result in kernel crashes (usually the device is simply unavailable), but cheap-and-easy solutions cost little, and sometimes do work.

Already tried connecting to a different router and still transferring at ~1MB/s. Thought it could be the router as I have a dual-wan and a wifi router acting as a switch. Disconnected from the "switch" and directly to the dual-wan (where the other PC I tested the transfer is connected) and still got this low rate.

Guess I could try a different cable but probly will get the same results. The thing is I don't want to spend time purchasing and installing a new netorking card when the problem could easily be software related. I think I'm gonna try with a live-dvd and see if the problem continues.

---

### Post by tgalati4 on 2014-02-24
Get yourself a cheap network card and turn off the on-board NIC in BIOS.  Check for leaky or bulging capacitors while you are inside.  If your system runs and the network speed returns then you can be reasonably assured that you have a failed on-board ethernet chip.  However, my experience is that when you start losing on-board functions, you start to lose more.  Your sound or USB will go next.  If that is the case, then the motherboard has started to fail and there is not much you can do about it.

---

### Post by numeritos on 2014-02-24
Ok just tried booting an old Kubuntu 13.04, transferred some stuff and still ~1MB/s. Tried with a different cable, same story. Seems like the onboard networking chip is failing (had a lot of power outtage during the last few months, so it could be that). Will try with a new card

---

### Post by ian-weisser on 2014-02-24
Well done.
A little bit of work has narrowed the problem considerably.
Glad to see you're chasing it methodically instead of randomly.

---

