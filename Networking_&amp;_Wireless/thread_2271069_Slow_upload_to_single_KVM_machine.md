---
title: "Slow upload to single KVM machine"
date: 2015-03-27
forum: Networking &amp; Wireless
---

### Post by unknown6 on 2015-03-27
In my network there are several servers which run Ubuntu 14.04 with KVM. One of these servers runs multiple Ubuntu VM's. One of these VM's has trouble with downloading items from workstations. This while a different VM running on the same host, and is using the same bridge and route to the workstation, does not have this problem.

Some details:
uploading from workstation to VM1: 130kb/s
uploading from workstation to VM2: 32mb/s
uploading from VM2 to VM1: 32mb/s

Also downloading from the internet goes with full speed at the VM1.

VM1:
ethtool eth0
Settings for eth0:
    Link detected: yes

Both VMs run on the same machine, with the same bridge and route through the switches. And both VM's use Virtio for network.

This problem has started a while back, while we did not make any changes as far as we know. And I cannot find any errors in the logs.
Can someone please give me an idea what the problem might be?

---

### Post by TheFu on 2015-03-27
DNS? /etc/hosts so both sides of the connection easily find the other side?
Start by trying to ping each other from the opposite machine.

---

### Post by unknown6 on 2015-03-27
> **TheFu said:**
> DNS? /etc/hosts so both sides of the connection easily find the other side?
Start by trying to ping each other from the opposite machine.

The ping times are actually normal.
VM1 pinging VM2:
icmp_req=1 ttl=64 time=0.280 ms
icmp_req=2 ttl=64 time=0.379 ms
icmp_req=3 ttl=64 time=0.565 ms

VM1 pinging workstation (The problem connection:
icmp_req=1 ttl=64 time=0.200 ms
icmp_req=2 ttl=64 time=0.255 ms
icmp_req=3 ttl=64 time=0.216 ms

I also looked at the DNS, but even when making a sftp connection on IP instead of name, the problem is still there.
They both use the same DNS server and /etc/hosts looks correct too.

---

### Post by TheFu on 2015-03-27
And vm2 to workstation and workstation to vm2?

---

### Post by unknown6 on 2015-03-30
> **TheFu said:**
> And vm2 to workstation and workstation to vm2?

These are around the same times when vm1 is pinging a workstation.

---

### Post by TheFu on 2015-03-30
I would turn up the logging for the programs used to serve and receive the files transfers.

---

