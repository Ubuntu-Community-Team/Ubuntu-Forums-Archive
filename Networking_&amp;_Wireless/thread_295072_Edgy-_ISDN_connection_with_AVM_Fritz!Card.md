---
title: "Edgy- ISDN connection with AVM Fritz!Card"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by pfadfinder on 2006-11-07
Hello, i am having problems with setting up my internet connection over isdn with an AVM Fritz!Card PCI. I installed linux-restricted-modules, avm-fritz-firmware, isdnutils, capiutils and pppdcapiplugin . When i try to start the connection with pon provider, I don't get any connection. The provider-file is properly set up. Here is an extract of /var/log/messages:

Nov 5 14:48:58 ikarus pppd[7455]: Plugin userpass.so loaded.
Nov 5 14:48:58 ikarus pppd[7455]: userpass: $Revision: 1.5 $
Nov 5 14:48:58 ikarus pppd[7455]: Plugin capiplugin.so loaded.
Nov 5 14:48:58 ikarus pppd[7455]: capiplugin: $Revision: 1.36 $
Nov 5 14:48:58 ikarus pppd[7455]: capiconn: 1.13
Nov 5 14:48:58 ikarus pppd[7459]: pppd 2.4.4 started by ikarus, uid 1000
Nov 5 14:48:58 ikarus pppd[7459]: capiplugin: phase serialconn.
Nov 5 14:48:58 ikarus pppd[7459]: capiplugin: dialing (nummer) (hdlc)
Nov 5 14:49:05 ikarus pppd[7459]: capiplugin: connected: "" -> "(nummer)" outgoing (pcli=0x101/ncci=0x10101)
Nov 5 14:49:05 ikarus pppd[7459]: capiplugin: using /dev/capi/0: "" -> "(nummer)" outgoing (pcli=0x101/ncci=0x10101)
Nov 5 14:49:06 ikarus pppd[7459]: Using interface ppp0
Nov 5 14:49:06 ikarus pppd[7459]: Connect: ppp0 <--> /dev/capi/0
Nov 5 14:49:06 ikarus pppd[7459]: capiplugin: phase establish (was serialconn).
Nov 5 14:49:06 ikarus pppd[7459]: capiplugin: phase authenticate (was establish).
Nov 5 14:49:07 ikarus pppd[7459]: capiplugin: phase terminate (was authenticate).
Nov 5 14:49:07 ikarus pppd[7459]: capiplugin: phase establish (was terminate).
Nov 5 14:49:09 ikarus pppd[7459]: capiplugin: disconnect(remote): "" -> "(nummer)" outgoing (pcli=0x101/ncci=0x10101) 0x3490 (0x3301) - Normal call clearing
Nov 5 14:49:09 ikarus pppd[7459]: Hangup (SIGHUP)
Nov 5 14:49:09 ikarus pppd[7459]: Modem hangup
Nov 5 14:49:09 ikarus pppd[7459]: capiplugin: phase disconnect (was establish).
Nov 5 14:49:09 ikarus pppd[7459]: Connection terminated.
Nov 5 14:49:09 ikarus kernel: [17179651.616000] kcapi: appl 1 ncci 0x10101 down
Nov 5 14:49:10 ikarus pppd[7459]: capiplugin: phase dead (was disconnect).
Nov 5 14:49:10 ikarus pppd[7459]: capiplugin: exit
Nov 5 14:49:10 ikarus pppd[7459]: Exit.
Nov 5 14:51:16 ikarus gconfd (felix-4671): Exiting
Nov 5 14:51:30 ikarus kernel: [17179792.892000] kcapi: card 1 down.
Nov 5 14:51:30 ikarus kernel: [17179792.896000] fcpci: Removing...
Nov 5 14:51:30 ikarus kernel: [17179792.896000] kcapi: Controller 1: fcpci-d400-12 unregistered
Nov 5 14:51:30 ikarus kernel: [17179792.896000] fcpci: Removed.
Nov 5 14:51:30 ikarus kernel: [17179792.896000] fcpci: Driver 'fcpci' detached
Nov 5 14:51:30 ikarus kernel: [17179792.980000] capi: Rev 1.1.2.7: unloaded
Nov 5 14:51:32 ikarus exiting on signal 15 

Does anyone know how to fix the problem?

Greetings

---

### Post by flaimo on 2006-11-15
*push*

i would like to know that too

---

