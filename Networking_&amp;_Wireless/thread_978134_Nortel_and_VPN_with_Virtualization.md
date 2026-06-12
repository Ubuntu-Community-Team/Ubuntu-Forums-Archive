---
title: "Nortel and VPN with Virtualization"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by irregardlessly on 2008-11-10
I need to use Nortel VPN to connect to my work machine.  I have given up trying to get the linux version to work (see [http://ubuntuforums.org/showthread.php?t=110843&page=11]("http://ubuntuforums.org/showthread.php?t=110843&page=11") and others).

So what I want to know is if anyone has had success getting the VPN to work through a VPN running Windows in Linux.  Anyone get this to work?  Any advice or pitfalls to watch out for?  What VM did you use?  wine, qemu, vmware? 

Thanks for any help.

---

### Post by sentron on 2009-01-24
> **irregardlessly said:**
> I need to use Nortel VPN to connect to my work machine.  I have given up trying to get the linux version to work (see [http://ubuntuforums.org/showthread.php?t=110843&page=11]("http://ubuntuforums.org/showthread.php?t=110843&page=11") and others).

So what I want to know is if anyone has had success getting the VPN to work through a VPN running Windows in Linux.  Anyone get this to work?  Any advice or pitfalls to watch out for?  What VM did you use?  wine, qemu, vmware? 

Thanks for any help.

I couldn't get Nortel VPN client to run under Opensuse 11.1. So, I installed Windows XP inside a VirtualBox VM, and used the Nortel Windows VPN client. It worked flawlessly, and it did not affect the host's network. In fact, I created two VMs running Windows XP, and I could connect VPN clients on them to two different VPN gateways simultaneously, and of course, the linux host's network did not get locked down by the VMs. 

I tried this by configuring the network adapters in the VM in bridged mode as well as the NAT mode. It worked fine in both modes.

---

