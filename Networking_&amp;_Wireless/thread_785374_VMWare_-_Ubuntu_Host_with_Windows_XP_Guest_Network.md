---
title: "VMWare - Ubuntu Host with Windows XP Guest Networking"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by brandes on 2008-05-07
Hi,
Im really new using Ubuntu. Last weekend i decided to try Ubuntu and reinstall my Dell notebook (originally with Vista). Everything with Ubuntu works perfect and im very happy with the results. The problem is that i need to use certain apps of my work (windows compatible), so i decided to install VMWARE Server. The installation went ok, i added a new virtual machine and configured it with Windows XP Sp2.
On the Ubuntu host, i have internet connection through a wireless NIC and its working perfect (Static IP: 192.168.100.2/24, Gateway: 192.168.100.1). I configured the virtual machine to use a bridged network connection. The virtual Windows XP is configured with a 192.168.100.3 ip address.
The problem is that i cannot ping any IP address outside my notebook from the XP virtual. I CAN ping the Ubuntu's ip address from the XP machine.
Is there anything else i need to do on the Ubuntu OS to let the virtual machine get to the outside network?
Thanks in advance!!!
(using ubuntu gutsy gibon)

---

### Post by superprash2003 on 2008-05-07
are you able to ping your router from xp?

---

### Post by brandes on 2008-05-07
No, nothing outside my notebook, only the wireless adapter's IP address.

---

