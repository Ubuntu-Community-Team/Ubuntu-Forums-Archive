---
title: "How can I block a usb device from being detected by ubuntu linux"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-10-03
Hi,

I have two usb network cards wlan0 and wlan1.


I have a VM on the host.  The host OS is ubuntu, the guest is also a flavor of ubuntu.

I want wlan0 to be accessible to the host only

and wlan1 to be accessible to the guest only as wlan0

How can I block wlan1 from showing up in host linux distro.

Thanks.

---

### Post by nixscripter on 2008-10-04
The guest must share the host's network interfaces, I'm afraid, or networking won't work at all.

Why would you want to block one of them?

---

### Post by sefs on 2008-10-05
It's two usb network interfaces I have.

And sometimes I enable the wrong one by mistake...the one being used by the host and it always locks up the system and i need to do a hard reboot.

So i wanted to blacklist the one that used in the guest so that the host never sees it.

---

### Post by nixscripter on 2008-10-06
I don't think you can do that.

One alternative would be to set up a bridged network with the guest OS using 1 to 1 NAT. This way, the host and guest could share one interface without hardware lockups (something I question should happen in the first place). Here's how:

1. On the host, set up a [_TAP device_]("http://vtun.sourceforge.net/tun/faq.html#1.2") with a fake IP, like 10.0.0.1

2. Set up the guest to use the other end of the TAP device. Depending on the emulation software, this may require some research. QEMU can do it, I'm not sure about virtual box or vmware.

3. Have the guest self-assign an IP on the fake subnet, like 10.0.0.2, and set the gateway to 10.0.0.1 and mask to 255.255.255.0

3. Set up [_one-to-one NAT with iptables_]("http://www.linuxquestions.org/questions/linux-security-4/iptables-11-nat-66791/") on the host.

The tap device is installed with Ubuntu already. Just ```
sudo modprobe tun
``` and use the **tunctl** command to set one up.

Hope this helps.

---

