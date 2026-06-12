---
title: "Network interface interrupt binding not working properly"
date: 2023-10-16
forum: Networking &amp; Wireless
---

### Post by tesla1060 on 2023-10-16
Hi,
I am on Ubuntu 20.04.6 LTS, numa with 2 node, each node has 64 physical cores.
I have bind all interrupt for a network interface on cpu 64, 65, as lspci -vvvs <bus-info> shows my network interface is on node 1


the problem is on numa node 1, only 64, 65 receive interrupt, but on node 0, all cpus still receives interrupt, but significantly fewer than 64, 65, when 64/65 receive 800+ interrupt, each cpu on node 0 only received 100.
My question is how is this possible as all interrupt for this interface is bind to 64,65, and cat /proc/irq/247/smp_affinity and cat /proc/irq/247/smp_affinity_list shows the binding was right, yet interrupt 247 still received by other not binded cpus.

---

