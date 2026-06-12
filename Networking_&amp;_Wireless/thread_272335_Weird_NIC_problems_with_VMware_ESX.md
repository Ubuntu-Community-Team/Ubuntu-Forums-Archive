---
title: "Weird NIC problems with VMware ESX"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by pronik on 2006-10-06
Hello!

I'm getting some really weird problems using Ubuntu Dapper Server on VMware ESX. I had a dedicated server for an Ubuntu install; however, I had to move it to a virtual machine. To accomplish that I've started a live rescue CD on both physical and virtual server (source and target), rsynced (with complete permissions and ownership) the root partition and installed grub to the MBR on the target. The virtual machine booted up fine, except for the ethernet device (pcnet32): even though the module is loaded (according to lsmod) and eth0 is detected (according to dmesg), "ifup eth0" tells me "eth0: no such device". Another Dapper Server installation on the same ESX (installed, not cloned) works fine out of the box.

What might be causing this behaviour? I've been suspecting some permission problem with modules caused by rsync, but I have no idea where to start looking for it. Any ideas?

Thanks!

---

### Post by pronik on 2006-10-06
Problem solved: the network device has been placed onto eth2, because /etc/iftab included eth0 and eth1, both bound to the MAC of the physical server.

---

