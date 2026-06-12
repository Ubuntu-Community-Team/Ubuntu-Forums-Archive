---
title: "Changed eth0 alias of NIC at boot"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by sunbear-c22 on 2017-03-05
I am using Ubuntu 16.04 LTS on a system with a built-in Ethernet card on a ASUS motherboard. 
I noticed that the alias of my network card has been changed during boot up from eth0 to enp031f6. See below output from 
*dmesg*.

Questions: 
[LIST=1]
[*]Is this change caused by Ubuntu 16.04?
[*]If yes, why did Ubuntu change the alias?
[*]If not, then which program changed the alias?
[*]Why was the alias changed at boot? Example, is there any benefit(s) (e.g. security, ...) for not using the usual eth0 than enp0s31f6?
[/LIST]

```
[    0.787243] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.787244] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.822820] e1000e 0000:00:1f.6: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.168534] e1000e 0000:00:1f.6 eth0: registered PHC clock
[    1.168535] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 1c:b7:2c:af:a3:a0
[    1.168536] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.169241] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[   23.006520] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

```

---

### Post by opsusec on 2017-03-06
more than likely a firmware update from your ISP; tunneling, then creating the need for a new, compatible driver for your hardware.

---

### Post by The Cog on 2017-03-06
This is indeed a change in Ubuntu. I believe the reason is that hardware discovery happens in parallel and therefore on some machines hardware is not always discovered in the same order. This meant that all the eth? numbers could be different after each reboot. The new naming stragegy is intended to guarantee the same name after every boot as it's based on hardware identity rather than order of discovery.

If you prefer the old eth0 type names, create a file /etc/udev/rules.d/80-net-setup-link.rules . I put a comment in mine reminding me that the presence of this file overrides the new default naming procedure.

```
$ cat /etc/udev/rules.d/80-net-setup-link.rules 
# The presence of this file overrides the default interface naming
```

[http://askubuntu.com/questions/704361/why-is-my-network-interface-named-enp0s25-instead-of-eth0](http://askubuntu.com/questions/704361/why-is-my-network-interface-named-enp0s25-instead-of-eth0)

---

### Post by chili555 on 2017-03-06
> **opsusec said:**
> more than likely a firmware update from your ISP; tunneling, then creating the need for a new, compatible driver for your hardware.Untrue.

It is caused by the recent change to systemd: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

There is no reason not to embrace and use the new naming convention.

---

### Post by sunbear-c22 on 2017-03-07
Thank you @The Cog and @chilli555 for the new information. I am glad to learn something new from you both.

---

