---
title: "multiple gateways vmware server"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by kristapscv on 2008-04-29
Hello I&#8217;m challenging following problem:

I have two network interfaces one for LAN second for WAN
VMware server is installed and bridged interfaces are configured

Eth0 > wmeth0
Eth1 > wmeth2

If I&#8217;m adding two GT to one to eth1 and another to eth0 Ubuntu is going mad :)
(quite logical)

What should be the configuration in interfaces to separate eth1 and eth0 and somehow force Ubuntu use only one of them.

In vmware server I can manually set which interface should be used for which guest opsystem

---

