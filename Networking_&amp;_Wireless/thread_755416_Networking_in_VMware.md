---
title: "Networking in VMware"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Jawmht on 2008-04-14
Hi, I have Ubuntu 6.10 installed as a guest in VMware 6 with a host of Windows Vista Ultimate. I am tring to connect to the internet by having the NAT feature (without DHCP on the guest side), and use my dialup connection in windows. However, although I enter the IP address and subnet mask in on Ubuntu, I cannot access the internet. Is their something I am missing or overlooked?

---

### Post by PilotJLR on 2008-04-14
Why is guest dhcp disabled??

If you want to statically address the guest for some reason, then can you confirm that you are in the right subnet? To find out, post windows' "ipconfig /all "

---

### Post by superprash2003 on 2008-04-14
assuming that you are on DSL.. when you want two connections to use the internet simulataneously you need to configure it in ppoe mode, where the modem dials instead of windows.. or another option is to enable ICS in windows, you need to have 2 network cards for that.. the best way is to use ppoe mode and also set to bridged mode in vmware

---

### Post by PilotJLR on 2008-04-14
Vmware server's NAT interface does all of that for you. 
It doesn't even matter if the host has a net connection or not; the guests get NAT access to the host (as if a virtual router was between them).

Of course, the internet connection must be up for the guest to use it... but aside from that it's irrelevant. Addressing on the guest side is a likely culprit here.

I would recommend enabling the vmware dhcp server, then making the guest a dhcp client. That would eliminate a couple possible faults right there.

---

### Post by Jawmht on 2008-04-14
> **PilotJLR said:**
> Vmware server's NAT interface does all of that for you. 
It doesn't even matter if the host has a net connection or not; the guests get NAT access to the host (as if a virtual router was between them).

Of course, the internet connection must be up for the guest to use it... but aside from that it's irrelevant. Addressing on the guest side is a likely culprit here.

I would recommend enabling the vmware dhcp server, then making the guest a dhcp client. That would eliminate a couple possible faults right there.That worked thank you very much, I didn't have it on before because... well I don't know why. Thanks agian.

---

