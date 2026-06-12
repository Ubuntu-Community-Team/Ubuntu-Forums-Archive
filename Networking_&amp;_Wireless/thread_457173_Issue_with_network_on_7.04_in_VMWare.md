---
title: "Issue with network on 7.04 in VMWare"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by wslyhbb on 2007-05-28
I am funning Kubuntu inside VMWare Workstation 5.5.4.  I upgraded 6.10 to 7.04, the network stopped working, I reinstalled VMWare Tools and still having an issue.  The network is up and has an IP address but I cannot get out to the Internet.  I usually use NAT but I also tried Bridged.

If someone could help me get my network back up and running, it would be appreciated.  Thanks.

---

### Post by turinglabs on 2007-05-28
I had the same issue when I upgraded to Festy. The problem is bridged networking with the 2.6.20 kernels. For now, the fix is to upgrade to vmware 6 (which I think is out of beta now), or install the latest patch (vmware-any-any-update109) and re-configure your vmware install to disable bridged networking (I am just using NAT at the moment and it's working fine). Search the vmware forums for 'Fesity' and you'll get some more info.

---

### Post by wslyhbb on 2007-05-29
Thanks.  I actually ended up starting from scratch and installing a fresh Feisty which worked fine in Workstation 5.5.4.

---

