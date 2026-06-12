---
title: "KVM VM IP address same as physical NIC IP address?"
date: 2019-11-04
forum: Networking &amp; Wireless
---

### Post by Heeter on 2019-11-04
Hi all,

If I have a KVM VM instance running on an IP Address, and this VM runs through a dedicated physical NIC using passthrough, should the IP Address of the Physical NIC be the same as the VM IP address?

I can't find anything in the KVM online documentation concerning this, using the passthrough function.

Regards

---

### Post by Skaperen on 2019-11-04
no.  use a private IP and make a virtual LAN if you do a 2nd one.  then set up masquerade NAT so its traffic out to the internet acquires the same IP as the host (physical machine) and return traffic is translated back to the private IP.  local port numbers will be translated automatically.  if you want to run a fixed port service inside the VM guest, you will need to set up a NAT rule for that, or run a relay process in the host.

---

### Post by Heeter on 2019-11-04
Awesome, Great News, Thank you!!!!!!!!!!!

---

### Post by Skaperen on 2019-11-04
if you set up a physical LAN connected to a 2nd physical interface on a host that becomes a router for that LAN, the setup is basically the same.  one is physical and one is virtual.  NAT would just treat them the same.  you might need to set up a bridge to do 2 VMs, but i think one can work by itself.  2 VMs won't need the bridge if you don't mind having them in different subnets.  but bridges can sometimes make things easier.  it's been a while since i've done this, and i might never, again, since i use cloud instances, now.

---

### Post by Heeter on 2019-11-04
I have 4 dedicated NICs on this server, just wanted to put them to use, even though it is overkill for my setup and bridging one NIC is fine for my setup.

But hey, why not go overkill once in a while!!!

Thank you so much for your response, I do appreciate it.

Regards

---

### Post by Skaperen on 2019-11-04
it won't be that easy to make use of them.  i assume one of them is a link to your ISP's box (whatever that is).  in that case going to 3 hosts or LANs is what they could be used for.  if you have a 2nd server with 4 NICs you could connect them together with 3 each to get triple speed.  but that would require some added software.  maybe someone has made a kernel module/patch to do it.  i think it might even be doable in userspace but performance might be the issue if theses are 10gig interfaces.  i've been thinking up a way to merge 2 ISPs for bandwidth sharing and failure fallback.  you might be able to do that with 3 or 4 ISPs.

---

