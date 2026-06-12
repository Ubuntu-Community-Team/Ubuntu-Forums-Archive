---
title: "sky2"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by marwooj on 2007-07-17
shy2 is doing this to me every couple minutes 
<unknown>: hw csum failure.
[  813.003357] 
[  813.003358] Call Trace:
[  813.003360]  <IRQ>  [<ffffffff8024f75e>] __skb_checksum_complete+0x4e/0x70
[  813.003385]  [<ffffffff80256889>] __tcp_checksum_complete_user+0x29/0x40
[  813.003390]  [<ffffffff8021c23c>] tcp_rcv_established+0x6bc/0x9a0
[  813.003401]  [<ffffffff8023d406>] tcp_v4_do_rcv+0x1f6/0x550
[  813.003408]  [<ffffffff88245569>] :sky2:sky2_intr+0x39/0x50
[  813.003414]  [<ffffffff8027cd82>] ack_apic_level+0x42/0x70
[  813.003421]  [<ffffffff802bdfc6>] handle_fasteoi_irq+0xf6/0x120
[  813.003426]  [<ffffffff802386e6>] ip_route_input+0x36/0xd40
[  813.003432]  [<ffffffff802701d9>] do_IRQ+0xd9/0x100
[  813.003442]  [<ffffffff8022880e>] tcp_v4_rcv+0x99e/0xa60
[  813.003455]  [<ffffffff80235e5e>] ip_local_deliver+0x1be/0x290
[  813.003462]  [<ffffffff80236f7e>] ip_rcv+0x4de/0x550
[  813.003470]  [<ffffffff883306f7>] :af_packet:packet_rcv_spkt+0x187/0x1b0
[  813.003477]  [<ffffffff80220d1f>] netif_receive_skb+0x26f/0x320
[  813.003488]  [<ffffffff8824524a>] :sky2:sky2_poll+0x71a/0xa00
[  813.003499]  [<ffffffff8028fae0>] run_rebalance_domains+0xd0/0x3b0
[  813.003508]  [<ffffffff8020c2ba>] net_rx_action+0xba/0x200
[  813.003517]  [<ffffffff80211c9f>] __do_softirq+0x5f/0xd0
[  813.003525]  [<ffffffff8026223c>] call_softirq+0x1c/0x28
[  813.003530]  [<ffffffff8027009c>] do_softirq+0x2c/0x90
[  813.003535]  [<ffffffff802701d9>] do_IRQ+0xd9/0x100
[  813.003538]  [<ffffffff8025a110>] mwait_idle+0x0/0x50
[  813.003543]  [<ffffffff80261631>] ret_from_intr+0x0/0xa
[  813.003546]  <EOI>  [<ffffffff802134f0>] tcp_poll+0x0/0x150
[  813.003559]  [<ffffffff8025a152>] mwait_idle+0x42/0x50
[  813.003565]  [<ffffffff8024b15b>] cpu_idle+0x9b/0xd0
[  813.003572]  [<ffffffff805707ca>] start_kernel+0x24a/0x260
[  813.003577]  [<ffffffff80570163>] _sinittext+0x163/0x170
[  813.003583] 


how it can be resolved?

---

### Post by DrCore on 2007-09-10
I have the same problem. Since 7.04 it has been impossible to use the network card while transmitting large amounts of data (> 2 GB). My hope was that Gutsy would have solved this issue but is has gotten worse.

In Feisty if I physically would disconnect the ethernet plug, the network would be restored. As of Gutsy this doesn't work anymore. As I have two network connectors, I have one chance last before restarting the system to change the plug to the other connector.

In Launchpad [https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/2.6.22-11.32]("https://launchpad.net/ubuntu/gutsy/+source/linux-source-2.6.22/2.6.22-11.32") I see some fixes are going to come. Maybe that will resolve these problems.

---

