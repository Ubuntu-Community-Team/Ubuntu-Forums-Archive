---
title: "System Freezing"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Loki*PI on 2009-04-13
GNOME 2.22.3
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"


The last two days my system has started freezing.  No clear pattern other than firefox is usually up.  Screens lock and I can do nothing but a hard boot.

Current on updates.

User log is full of the following: dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain  - not sure if that is significant.


Syslog has this I think at the time of a freeze:

Apr 13 19:12:31 zero ntpdate[6825]: no servers can be used, exiting
Apr 13 19:12:33 zero avahi-daemon[5672]: Registering new address record for fe80::21e:8cff:fea1:4f11 on eth1.*.
Apr 13 19:12:42 zero kernel: [   59.018111] eth1: no IPv6 routers present
Apr 13 19:12:49 zero NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 13 19:12:49 zero NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Apr 13 19:17:01 zero /USR/SBIN/CRON[7097]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 19:31:49 zero init: tty4 main process (5325) killed by TERM signal
Apr 13 19:31:49 zero init: tty5 main process (5326) killed by TERM signal
Apr 13 19:31:49 zero init: tty2 main process (5328) killed by TERM signal
Apr 13 19:31:49 zero init: tty3 main process (5330) killed by TERM signal
Apr 13 19:31:49 zero init: tty6 main process (5332) killed by TERM signal
Apr 13 19:31:49 zero init: tty1 main process (6774) killed by TERM signal
Apr 13 19:31:50 zero gdm[6239]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Apr 13 19:31:50 zero gdm[6239]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Apr 13 19:31:50 zero avahi-daemon[5672]: Got SIGTERM, quitting.
Apr 13 19:31:50 zero avahi-daemon[5672]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.3.
Apr 13 19:31:53 zero exiting on signal 15

Hardware:
                       system      Computer
/0                     bus         Motherboard
/0/0                   memory      1010MiB System memory
/0/1                   processor   Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00G
/0/1/1.1               processor   Logical CPU
/0/1/1.2               processor   Logical CPU
/0/100                 bridge      82945G/GZ/P/PL Memory Controller Hub
/0/100/1               bridge      82945G/GZ/P/PL PCI Express Root Port
/0/100/1/0             display     RV370 [Sapphire X550 Silent]
/0/100/1/0.1           display     RV370 secondary [Sapphire X550 Silent]
/0/100/1b              multimedia  82801G (ICH7 Family) High Definition Audio Co
/0/100/1c              bridge      82801G (ICH7 Family) PCI Express Port 1
/0/100/1c.1            bridge      82801G (ICH7 Family) PCI Express Port 2
/0/100/1c.1/0  eth1    network     L2 100 Mbit Ethernet Adapter
/0/100/1d              bus         82801G (ICH7 Family) USB UHCI Controller #1
/0/100/1d.1            bus         82801G (ICH7 Family) USB UHCI Controller #2
/0/100/1d.2            bus         82801G (ICH7 Family) USB UHCI Controller #3
/0/100/1d.3            bus         82801G (ICH7 Family) USB UHCI Controller #4
/0/100/1d.7            bus         82801G (ICH7 Family) USB2 EHCI Controller
/0/100/1e              bridge      82801 PCI Bridge
/0/100/1f              bridge      82801GB/GR (ICH7 Family) LPC Interface Bridge
/0/100/1f.1            storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.2            storage     82801GB/GR/GH (ICH7 Family) SATA IDE Controll
/0/100/1f.3            bus         82801G (ICH7 Family) SMBus Controller

don't really know what else might be relevant.  

Anyone have any idea?

Thanks

---

### Post by finer recliner on 2009-04-13
do you have compiz fusion effects enabled? if so, try turning that off. 

system > preferences > appearence > visual effects

---

### Post by Loki*PI on 2009-04-13
HI Thanks - no I don't have any enabled, pretty much vanilla installation.  No bells or whisles.

---

