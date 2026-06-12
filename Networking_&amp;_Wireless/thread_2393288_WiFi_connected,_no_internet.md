---
title: "WiFi connected, no internet"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by lubomir on 2018-06-01
UPC router has two WiFi networks: Private and Public called UPC Wi-Free.  Second one stop working. Notebook connect to WiFi network (connection  established) but cannot access (ping) any address on internet (for instace DNS  server or gateway). UPC WiFi private network works fine. I try connect to this UPC  Wi-Free network on another UPC router with same result. I try connect to  this UPC Wi-Free network with second notebook with Ubuntu 16.04 64 bit  and it still working. I did not find any software update on my notebook  in this period, when WiFi stop working. I ask UPC provider and they say,  that they change nothing in they network in this period. So nothing  changed, but this network stop working. Here is a output from nmcli:    [https://paste.ubuntu.com/p/T2Y2vKKzdj/](https://paste.ubuntu.com/p/T2Y2vKKzdj/). There is one line suspicious for me GENERAL.MTU: 0. But it is the same on second notebook, which is working. Actually, after I connect to wifi it shows GENERAL.MTU:1500 and after short time it changes to 0.
How can I find what is wrong with connection to this network?

---

### Post by lubomir on 2018-06-02
I do not known what was exactly wrong, but when I clone MAC address, it start working. I suppose that in this UPC Wi-Free network was/is something wrong with ARP tables.

---

