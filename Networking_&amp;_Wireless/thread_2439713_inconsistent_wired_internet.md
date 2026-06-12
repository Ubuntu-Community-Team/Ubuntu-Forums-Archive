---
title: "inconsistent wired internet"
date: 2020-03-31
forum: Networking &amp; Wireless
---

### Post by subpar-user-1000 on 2020-03-31
I'm seeing very inconsistent wired internet behavior - when running a speed test sometimes both up and down are 100mbps. Other times up, down, or both will be <10mbps. The internet will also just randomly drop sometimes.

I'm not really sure where to go from here, any help is appreciated.

Snippet from lspci -v:

```

03:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5762 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Hewlett-Packard Company NetXtreme BCM5762 Gigabit Ethernet PCIe
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at e0820000 (64-bit, prefetchable) [size=64K]
	Memory at e0810000 (64-bit, prefetchable) [size=64K]
	Memory at e0800000 (64-bit, prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data
	Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [a0] MSI-X: Enable+ Count=6 Masked-
	Capabilities: [ac] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Device Serial Number 00-00-ec-b1-d7-50-f3-ac
	Capabilities: [150] Power Budgeting <?>
	Capabilities: [160] Virtual Channel
	Capabilities: [1b0] Latency Tolerance Reporting
	Capabilities: [230] Transaction Processing Hints
	Kernel driver in use: tg3
	Kernel modules: tg3

```


ifconfig -a:
```

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.69  netmask 255.255.255.0  broadcast 192.168.1.255
        ether ec:b1:d7:50:f3:ac  txqueuelen 1000  (Ethernet)
        RX packets 190395  bytes 172765953 (172.7 MB)
        RX errors 0  dropped 10  overruns 0  frame 0
        TX packets 164009  bytes 179599510 (179.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18 


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4879  bytes 725412 (725.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4879  bytes 725412 (725.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

---

### Post by QIII on 2020-03-31
Hello!

Who is your internet provider and what do they promise?  Is 100Mbps what you would normally expect?

---

### Post by subpar-user-1000 on 2020-03-31
I have AT&T. If I run a speed test from my windows laptop I'm getting over 100mbps down.
The ubuntu desktop (18.04 since I forgot to include it initially) is the only device I have an issue with the internet dropping.

Edit: I don't necessarily care if I even get 100+ speeds, I just want it to work consistently.

---

### Post by praseodym on 2020-04-01
Try adding the mtu value of your ISP instead of "Automatic" in your networkmanager profile. After reconnecting check the dropped packages output of "ifconfig" again

---

