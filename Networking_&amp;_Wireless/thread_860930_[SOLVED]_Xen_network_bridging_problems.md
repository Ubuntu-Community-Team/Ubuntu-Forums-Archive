---
title: "[SOLVED] Xen network bridging problems"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Ingmar on 2008-07-16
Hello,

I'm trying to use Xen on my Homeserver (Ubuntu Hardy Server). I want to virtualize some servers for security reason. But I have some problems with the network bridges.

My server have three network interface cards. Two are connected to two switches and they should be bridged. The third should provide access to a DSL-Modem and should be connected to my Router-VM.

I can use the first nic (eth0) with the Dom0 and I haven't tested to bridge with eth1, but I don't need it yet. My problem is, that I can't access the network from the VMs and I don't know why it doesn't work.

When I start the VM and type "brctl show" I see, that the bridge seems to be configured corret, but I can't access the network out of the VM.

My VM-config-file includes this line:
```
vif = [ 'bridge=eth0,ip=192.168.213.6,mac=00:16:3E:XX:XX:XX' ]
```
And my network-script:
```
#!/bin/bash
dir=$(dirname "$0")
"$dir/network-bridge" "$@" vifnum=0 netdev=eth0
"$dir/network-bridge" "$@" vifnum=2 netdev=eth2
```


Where is my mistake? Why doesn't it work?

---

### Post by Ingmar on 2008-10-29
After long time wasted with some experiments on the network I nearly gave up setting up this network bridging.

But then after Upgrading the Kernel the problem disappeared and now the bridges with Xen-Network are working fine like I expected how it should work.

---

