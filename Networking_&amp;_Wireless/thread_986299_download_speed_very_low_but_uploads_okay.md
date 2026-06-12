---
title: "download speed very low but uploads okay"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by mattsajay on 2008-11-18
I noticed very slow download speeds (~400kbps) but okay upload speeds (~1.5mbps) over the last couple of days. I am at an university and generally the ethernet LAN works with blazing speed here. If I connect another machine (running MacOSX) to the same ethernet port, the speeds are much faster than that observed on the machine running Ubuntu Feisty 7.04. Other machines in neighboring offices are also not complaining about download speeds, so I know the problem is not systemic to the University LAN.

Networking tools show the " Network device " as "loopback interface" with " Ethernet interface" eth0 being in the drop down menu (along with a few other virtual ware interfaces. I have tried setting the Network Device to Ethernet Interface without success. The machine currently runs DHCP configuration. 

How do I go about diagnosing the problem and solving it.

---

### Post by Iowan on 2008-11-18
Try disabling ipv6.  There's a link in my sig, but it's several versions old.

---

### Post by mattsajay on 2008-11-19
Iowan,

Thank mate! I have tried that (disabling ipv6) but do not notice any significant upswing in speed. For some reason even epiphany is slow. Streaming video which used to be very smooth till day before yesterday is unwatchable now. I hope my machine's security is not compromised@!

---

### Post by mattsajay on 2008-11-26
any other suggestions. still suffering from pitifully slow system on University LAN. I download stuff from rapidshare/megaupload. could that have affected the system.

---

