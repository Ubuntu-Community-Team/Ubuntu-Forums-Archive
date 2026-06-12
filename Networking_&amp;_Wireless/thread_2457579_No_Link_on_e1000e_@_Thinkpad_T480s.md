---
title: "No Link on e1000e @ Thinkpad T480s"
date: 2021-02-05
forum: Networking &amp; Wireless
---

### Post by thebigk on 2021-02-05
Hi,

please I am new to this forum. Be nice to me please ;)

Since a couple of weeks, can't pinpoint when it started but I have issues with getting a LAN link. When I boot up I have no LAN link. (this is also happening when putting LAN cable into the laptop directly instead of using my dock.) I also tried putting my Laptop on different Working desk to check if something is wrong with my switch or cable. But when the Error occurs it doesnt matter. I just have no link.

The only solution is to reboot or unloading and reloading the module. Sometimes I need to do it more than once. When I find a link the Network Connection is completely fine till the next reboot.

What I did so far is to install a newer version of the Kubuntu 2010 Kernel of the proposed mirror since I saw in changelog there are some changes made to the e1000e Driver. But that did not do the trick for me so far. I also have a different dock now with newest firmware which did not change anything either. My strong believe is that something is wrong with the driver.

Any suggestions?


```
Linux Thinkpad-T480s 5.8.0-42-generic #47-Ubuntu SMP Thu Jan 28 01:29:42 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
USER@Thinkpad-T480s:~$ sudo dmesg | grep e1000e
[    1.439549] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.439549] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.444126] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.650098] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    1.717924] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) xx:xx:xx:xx:xx:xx
[    1.717929] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.718000] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: 1000FF-0FF
[    1.737173] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[   32.984346] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   39.307663] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Up 1000 Mbps Half Duplex, Flow Control: None
[   39.308635] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Down
USER@Thinkpad-T480s:~$ sudo modprobe -r e1000e
USER@Thinkpad-T480s:~$ sudo modprobe e1000e
USER@Thinkpad-T480s:~$ sudo dmesg | grep e1000e
[    1.439549] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.439549] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.444126] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.650098] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    1.717924] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) xx:xx:xx:xx:xx:xx
[    1.717929] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.718000] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: 1000FF-0FF
[    1.737173] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[   32.984346] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   39.307663] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Up 1000 Mbps Half Duplex, Flow Control: None
[   39.308635] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Down
[  122.344421] e1000e 0000:00:1f.6 enp0s31f6: removed PHC
[  122.421935] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Down
[  125.843257] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[  125.843259] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[  125.843608] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[  126.045948] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[  126.114764] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) xx:xx:xx:xx:xx:xx
[  126.114776] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[  126.114870] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: 1000FF-0FF
[  126.121051] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[  131.299537] e1000e 0000:00:1f.6 enp0s31f6: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None

```

---

### Post by deadflowr on 2021-02-05
*Thread moved to **Networking and Wireless***

---

