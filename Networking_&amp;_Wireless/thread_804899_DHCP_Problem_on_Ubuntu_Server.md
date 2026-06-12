---
title: "DHCP Problem on Ubuntu Server"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by edd07 on 2008-05-23
Hello, I am having trouble with the network connection of a server (no gui). I configured the eth0 interface to DHCP using the /etc/network/interfaces file like this:
```
auto eth0
iface eth0 inet dhcp
```
When the computer boots, and the modem is turned on, everything's ok. The problem is when it boots and the modem isn't on, it stays waiting for the DHCP response forever, and I need the computer to boot even if the apocalypse is unfolding. 

Is there a way to make it stop waiting for the DHCP response if it fails the first time? Or any other solution to this problem?

Thanks

---

### Post by superprash2003 on 2008-05-23
is the dhcp server installed?

---

### Post by Iowan on 2008-05-24
From **man dhclient.conf**:>        The timeout statement

       timeout time ;

       The timeout statement determines the amount  of  time  that  must  pass between the time that the client begins to try to determine its address and the time that it decides that it’s not going to be able to  contact a  server.  By  default,  this  timeout is sixty seconds. After the timeout has passed, if there are any static leases defined in the  configuration  file, or any leases remaining in the lease database that have not yet  expired,  the client  will  loop  through  these  leases attempting  to  validate  them,  and if it finds one that appears to be valid, it will use that lease’s address. If there are no valid static leases or unexpired  leases  in  the  lease database, the client will restart the protocol after the defined retry interval.

---

### Post by edd07 on 2008-05-24
> **Iowan said:**
> From **man dhclient.conf**:

I love you.

---

