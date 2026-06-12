---
title: "chroot for different default route?"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by eldaria on 2013-09-07
I'm trying to get certain applications to use an OpenVPN route, while others should not.

If I start a VPN on my computer all outgoing traffic will default to this connection(Route).
However since VPN traffic is slower, I only want certain applications to take this route.

So I was thinking, how do chroot handle networking? if I start the OpenVPN client inside the chroot, and then start the application also inside the chroot, would it then take the OpenVPN route, while applications outside the chroot takes the normal route?

Also do the chroot get the same IP as the "host" for incoming connections, for example a web server?

---

### Post by ian-weisser on 2013-09-07
It may be simpler to define separate routes for the VPN/Non-VPN IP address ranges using the **route** command.
That would be independent of any application(s).

---

### Post by eldaria on 2013-09-07
> **ian-weisser said:**
> It may be simpler to define separate routes for the VPN/Non-VPN IP address ranges using the **route** command.
That would be independent of any application(s).

Well that would work if I knew what IP ranges I will connect to.

I previously had all traffic going through the VPN, and had certain connections specifically routed to bypass the VPN, however I want to do a separation on application level as I will not know where the application will connect.

I'm actually thinking that if it is not possible with chroot, then I'll set up KVM and run a virtual machine instead. ;-) Just wanted something with less overhead.

---

