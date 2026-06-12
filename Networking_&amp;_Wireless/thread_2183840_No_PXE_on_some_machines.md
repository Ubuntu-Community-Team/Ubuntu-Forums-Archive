---
title: "No PXE on some machines"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-10-26
I have a PXE server with syslinux 6 and tftpd-hpa working properly, however I am not able to boot with pxe on some machines.  I suspect  that since these are newer models machines, that EUFI has something to do with it.  However, when I disable UEFI and boot in legacy mode, the client machine still does not PXE boot.
The DHCP offer goes out to the client but it is not received.

dhcpd: DHCPOFFER on 192.168.1.208 to 5c:f9:dd:df:44:70 via em1 
 
any advice

---

