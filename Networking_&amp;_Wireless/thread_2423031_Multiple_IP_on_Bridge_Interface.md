---
title: "Multiple IP on Bridge Interface"
date: 2019-07-16
forum: Networking &amp; Wireless
---

### Post by driftavalii on 2019-07-16
I have a VM where I've created a bridge and assigned the IP address to the bridge interface. With one IP, this works okay but if I assign a second IP to the bridge interface, I am unable to reach the VM from outside. However, if I console into the VM and ping to an external address, the VM becomes reachable. It seems the VM is not sending out arp queries with two IP's assigned to the bridge interface. I could setup a job where I ping every 60 seconds but that would be a hack and I would rather address the root cause if there is one. Why am I doing this, the VM's are Kubernetes worker nodes with a different CIDR. I am running FRRouting on the VM and I would like traffic from the containers to have a default gateway as the second IP on the bridge interface and all traffic from a VM (whether host or containter) to be handled in the physical network once it leaves the VM. 

It seems setting the values below in /etc/sysctl.conf might help but I do not fully understand what they are supposed to do.

  net.bridge.bridge-nf-call-ip6tables = 0
  net.bridge.bridge-nf-call-iptables = 0
  net.bridge.bridge-nf-call-arptables = 0

I have thought of using gratuitous arp but you have to issue the command, would that be a viable direction? Any help is appreciated.

---

