---
title: "New kernels limiting my internet access.."
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by likewtfster on 2007-02-15
Alright, as the subject says, I'm having problems using the internet on distributions newer than Hoary. In fact, it isn't just newer than hoary, it's any distribution with a newer kernel than 2.6.13. That is, I can browse the net on Slackware's 2.4 kernels; Ubuntu Hoary, Suse 10.0, but nothing with a newer kernel.


Using new kernels (practically any distro now uses >2.6.13) it turns out that I can resolve some IPs, but not enough to be able to do anything useful. I can resolve google.com, and a few others like my ISP's website, but nothing else. When I'm using an older kernel, I can access websites which I hadn't been able to with a newer one.
If I type "ping www.google.com" everything is fine, however, if I type "ping www.ubuntu.org", or most other sites, it shows the IP in brackets, and then just times out.

I do not believe this is related to ipv6, which I have disabled, without success, and even recompiling kernels without it. Nor can it be a DNS issue, as I use the same DNS server for every computer in my network.

This "problem" occurs on every computer in my network, all using the same DNS server, different distros (Windows works fine), and different network hardware (wireless pci/usb, ethernet), which suggests there is a problem with my router, which is a Netgear Wgr614v1.

Is anyone familiar with this problem?

Thanks

---

### Post by bnuytten on 2007-02-15
For some reason ping is blocked to [www.ubuntu.org](www.ubuntu.org). The .com site is replying ping. If you still experience problems, post the output of "tracepath -n www.google.com" and "ip r" or "route -n".

---

