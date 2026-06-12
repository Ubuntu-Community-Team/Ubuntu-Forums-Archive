---
title: "Two IP Addresses in same Computer with different O/S"
date: 2017-10-28
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2017-10-28
In my PC I'm having two O/S - Main is UBUNTU 16.04 and the other is Windows 7 in Virtual Box. My Router is NETGEAR with wired connection. It is observed that the IP address shown in Ubuntu is different with the Windows 7. My humble query - is it normal? If not, what to do?

---

### Post by ajgreeny on 2017-10-28
I suspect it is dependent upon the way your router (is that how you connect?) detects the hardware address of the VM's virtual hardware compared with the real hardware address and therefore the router does not reserve the IPs.

I think my situation is the same as yours, and also the 5 VMs I use each have different IPs as a result of that.

So, no need to worry; just accept it as it is.

---

### Post by AnupamMitra on 2017-10-28
@ ajgreeny Thanks for your reply and advise.

---

