---
title: "[SOLVED] dhclient persists on disconnected network"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by lavinog on 2007-02-04
I have just installed the 32bit version of ubuntu edgy on my laptop after using the 64 bit for a couple of months.
the problem I am having is that there is a delay in the boot up and i have narrowed it down to dhclient trying to obtain a lease on eth0 when there is no cable connected. Not only that but in my syslog it seems to continue to try every 5 mins.

is there a way to tell dhclient not to bother if no cable is connected?
I didn't have this problem when I installed the 64 bit version.

> Feb  4 11:47:06 lavinog-laptop dhclient: No working leases in persistent database - sleeping.
Feb  4 11:50:33 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb  4 11:50:41 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb  4 11:50:55 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb  4 11:51:10 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Feb  4 11:51:31 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb  4 11:51:34 lavinog-laptop dhclient: No DHCPOFFERS received.
Feb  4 11:51:34 lavinog-laptop dhclient: No working leases in persistent database - sleeping.
Feb  4 11:58:29 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb  4 11:58:35 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb  4 11:58:50 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb  4 11:59:07 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb  4 11:59:16 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb  4 11:59:24 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb  4 11:59:30 lavinog-laptop dhclient: No DHCPOFFERS received.
Feb  4 11:59:30 lavinog-laptop dhclient: No working leases in persistent database - sleeping.
Feb  4 12:06:57 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb  4 12:07:00 lavinog-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

---

### Post by Paerez on 2007-02-04
System->Administration->Networking click on Wired Connection, then Properties, then uncheck Enable This Connection and reboot.

---

### Post by lavinog on 2007-02-04
> **Paerez said:**
> System->Administration->Networking click on Wired Connection, then Properties, then uncheck Enable This Connection and reboot.

Thank you for the quick reply.

---

