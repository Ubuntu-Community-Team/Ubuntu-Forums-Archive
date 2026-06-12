---
title: "ping: unknown host but can find host name via Places"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by ASolano on 2008-11-05
Within the terminal if I run the command "ping <HOST_NAME>" I get the error "ping: unknown host <HOST_NAME>"

Yet <HOST_NAME> is visible when I then browse to it via Places (Places Menu > Network > windows network > <WORKGROUP_NAME>)

can someone please tell me whats going on.  Why can ubuntu resolve the name via Places but no via the terminal.

Environment Details

* Internet router providing the following services
- DHCP
- DNS

* Host 1
- Windows Server 2003  with SP1
- Static IP Address

* Host 2
- Ubuntu Release 8.04 (Hardy)
- Dynamic IP Address

* Client
- Ubuntu Release 8.04 (Hardy)

NOTE
- the above happens for both the windows and ubuntu hosts
- trying to resolve the names also fails via firefox "http://<HOST_NAME>"

---

### Post by Iowan on 2008-11-05
The "Windows network" name may be resolved by **nmbd**, **winbind**, **WINS**or other netbios protocol.  Ping uses ICMP (IP?). Either the **hosts** file, DNS, or another "mapping" method must link hostnames to IP addresses. *Some* information is available in **man nsswitch.conf**.

---

