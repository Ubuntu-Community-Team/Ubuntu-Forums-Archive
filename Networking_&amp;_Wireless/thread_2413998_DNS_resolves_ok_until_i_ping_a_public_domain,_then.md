---
title: "DNS resolves ok until i ping a public domain, then stops resolving internal"
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by dot-jon on 2019-03-04
I've hit a really odd issue that i can replicate but can't think of a reason for the unexpected behaviour.

The issue goes like this... I release my DHCP lease on my laptop and renew the lease.
At this point i can ping hosts in my domain for example
$ ping lab-host1
64 bytes from lab-host1.lab-1.directory (10.10.24.30): icmp_seq=1 ttl=63 time=0.582 ms

The same is true for anything in that domain, i can also use the fqdn of the host, all is well.
That is, until i then ping something on the public internet. After which i am then unable to ping ANYTHING on my domain by hostname or fqdn.

As soon as i release/renew i am immediately able to ping or dig local domain hosts by name or fqdn again

Additional info, there's two subnets here. My laptop is in one, and the lab is in another. from the lab i can always ping anything without any issues. DNS is coming from pfsense. From pcaps i can see that the lookups seem to skip my local dns resolver during the issue and go straight to my second dns server which is cloudflare, thus it returns no result. I'm using networkmanager and i have a bridge for KVM. The lab is on a different server

Any help at all is appreciated

---

### Post by jeremy31 on 2019-03-04
Moved to Networking

---

### Post by TheFu on 2019-03-04
I've seen KVM networking stop for a single VM, then magically start working the next day. Checked the VM using console access - everything internal seemed fine. Don't recall all the details, but some of the networking worked fine, just not to the internet.  10 other VMs on the same host, using the same bridge, were not impacted in any way.   The setup had been stable for years.  About a month later, the same thing happened.  I moved that single VM to a different VM host and haven't seen the issue again. No changes to the VM, the VM config or the bridges which are manually configured using bridge-utils.

I would check all the routing, all firewalls, all bridge configs, and ensure that IPv6 was disabled in the kernel. IPv6 still causes some odd problems.  Seeing how I "showed my work" might be helpful to you. Often, what we think we have configured isn't actually what we do have configured, so running the commands, showing the options, and showing the output is very important to get help here.

Stick with IPs. Does everything work?
Have you tried using static IPs for each server?  Does that fix it?

I don't use network manager - actually purge it from my systems.
I don't use the automatically created KVM/libvirt bridges or NAT devices.

[https://ubuntuforums.org/showthread.php?t=2396877](https://ubuntuforums.org/showthread.php?t=2396877) ... my thread.  It was never "solved", I just found a workaround. Perhaps there are some useful troubleshooting ideas in there for you?

---

### Post by dot-jon on 2019-03-05
Thanks for the input. I'll have some more time to do battle with this tomorrow. I'll post how it goes

---

