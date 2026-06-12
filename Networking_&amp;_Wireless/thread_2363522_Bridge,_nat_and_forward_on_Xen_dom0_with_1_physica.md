---
title: "Bridge, nat and forward on Xen dom0 with 1 physical interface"
date: 2017-06-11
forum: Networking &amp; Wireless
---

### Post by siben17 on 2017-06-11
Hello,

We have a server in DC with only 1 network interface connected. We have multi public IP addresses.
The server is running Ubuntu 14.04 LTS with Xen. Some of the VM are using public IP addresses through a bridge.
We would like to run some VM with private addresses and we would like to forward some ports of some public IP to this VM.

In a test environment I've try to use iptables to forward port. This work great if I connect a second network interface.

I would like to do this with 2 of the 5 public IP adresses.

Thanks a lot for all of your idea. I think I've miss something

---

