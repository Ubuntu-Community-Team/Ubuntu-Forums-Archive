---
title: "Wireless networking not working after upgrade to 14.04"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by mark194 on 2015-02-04
I have an HP Pavilion dv6000 that I upgraded from 12.04 to 14.04.  The wireless was working fine under 12.04, but after the upgrade (I did a clean install), it's not recognizing any existing wireless networks.  Can't figure out how to get it to recognize the networks in our building.  Any ideas?

---

### Post by jeremy31 on 2015-02-04
Open a terminal window and enter```
lspci -nnk | grep -iA2 net
``` and paste the results

---

### Post by mark194 on 2015-02-04
No command 'lscpi'found, did you mean: 
 Command 'lscp' frompackage 'nilfs-tools' (universe) 
 Command 'lspci'from package 'pciutils' (main) 
 Command 'lscpu'from package 'util-linux' (main) 
lscpi: command notfound

---

### Post by mark194 on 2015-02-04
My apologies, just caught the typo in my last reply.  Here's the result when the command is run CORRECTLY:

02:00.0 Networkcontroller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY[14e4:4315] (rev 01) 
	Subsystem:Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller[103c:137c] 
	Kernel driver inuse: b43-pci-bridge 
06:00.0 Ethernetcontroller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102EPCI Express Fast Ethernet controller [10ec:8136] (rev 01) 
	Subsystem:Hewlett-Packard Company Pavilion dv6700 [103c:30cc] 
	Kernel driver inuse: r8169

---

### Post by jeremy31 on 2015-02-04
According to the sticky post [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
you just need to ```
sudo apt-get install firmware-b43-installer
``` and reboot

---

### Post by mark194 on 2015-02-04
Thanks. I had some trouble deciphering the sticky, your post makes it easier to follow.  Problem solved.

---

