---
title: "Access Concentrator Did Not Respond"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by arnold.pietersen on 2007-08-23
When I try to setup a PPPoE connection using sudo pppoeconf with a wireless USB modem, I get the message:

Access Concentrator did not respond

Does anyone know how to fix this problem?

Thanks

Arnold

---

### Post by ddrichardson on 2007-08-24
Hi,

Can you post the output of```
sudo tail -f /var/log/messages
```

We also need to know if this is a USB modem and who your ISP is.

---

### Post by arnold.pietersen on 2007-08-25
It is a USB modem and the ISP is iBurst.

The following is some of the output:

PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:08:35 arnold-laptop kernel: [  108.304000] PPP generic driver version 2.4.2
Aug 25 17:08:35 arnold-laptop pppd[5767]: pppd 2.4.4 started by root, uid 0
Aug 25 17:08:35 arnold-laptop pppd[5767]: Using interface ppp0
Aug 25 17:08:35 arnold-laptop pppd[5767]: Connect: ppp0 <--> /dev/pts/1
Aug 25 17:08:53 arnold-laptop kernel: [  126.152000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:08:57 arnold-laptop kernel: [  130.508000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 
Aug 25 17:09:06 arnold-laptop pppd[5767]: LCP: timeout sending Config-Requests 
Aug 25 17:09:06 arnold-laptop pppd[5767]: Connection terminated.
Aug 25 17:09:06 arnold-laptop pppd[5767]: Modem hangup
Aug 25 17:09:10 arnold-laptop pppd[5767]: Exit.
Aug 25 17:09:15 arnold-laptop pppd[7186]: pppd 2.4.4 started by root, uid 0
Aug 25 17:09:15 arnold-laptop pppd[7186]: Using interface ppp0
Aug 25 17:09:15 arnold-laptop pppd[7186]: Connect: ppp0 <--> /dev/pts/1
Aug 25 17:09:19 arnold-laptop kernel: [  153.004000] HDLC line discipline: version $Revision: 4.8 $, maxframe=4096
Aug 25 17:09:19 arnold-laptop kernel: [  153.004000] N_HDLC line discipline registered.
Aug 25 17:09:19 arnold-laptop kernel: [  153.032000] NET: Registered protocol family 24
Aug 25 17:09:24 arnold-laptop kernel: [  157.164000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:09:46 arnold-laptop pppd[7186]: LCP: timeout sending Config-Requests 
Aug 25 17:09:46 arnold-laptop pppd[7186]: Connection terminated.
Aug 25 17:09:46 arnold-laptop pppd[7186]: Modem hangup
Aug 25 17:09:50 arnold-laptop pppd[7186]: Exit.
Aug 25 17:09:55 arnold-laptop kernel: [  188.160000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:09:55 arnold-laptop pppd[8841]: pppd 2.4.4 started by root, uid 0
Aug 25 17:09:55 arnold-laptop pppd[8841]: Using interface ppp0
Aug 25 17:09:55 arnold-laptop pppd[8841]: Connect: ppp0 <--> /dev/pts/1
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): starting (version 2.18.0.1), pid 8854 user 'root'
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 25 17:10:09 arnold-laptop gconfd (root-8854): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 25 17:10:15 arnold-laptop kernel: [  208.228000] NETDEV WATCHDOG: ib0: transmit timed out
Aug 25 17:10:26 arnold-laptop kernel: [  219.160000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:10:26 arnold-laptop pppd[8841]: LCP: timeout sending Config-Requests 
Aug 25 17:10:26 arnold-laptop pppd[8841]: Connection terminated.
Aug 25 17:10:26 arnold-laptop pppd[8841]: Modem hangup
Aug 25 17:10:30 arnold-laptop pppd[8841]: Exit.
Aug 25 17:10:35 arnold-laptop kernel: [  228.228000] NETDEV WATCHDOG: ib0: transmit timed out
Aug 25 17:10:35 arnold-laptop pppd[8871]: pppd 2.4.4 started by root, uid 0
Aug 25 17:10:35 arnold-laptop pppd[8871]: Using interface ppp0
Aug 25 17:10:35 arnold-laptop pppd[8871]: Connect: ppp0 <--> /dev/pts/1
Aug 25 17:10:55 arnold-laptop kernel: [  248.228000] NETDEV WATCHDOG: ib0: transmit timed out
Aug 25 17:10:57 arnold-laptop kernel: [  250.160000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=143 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=123 
Aug 25 17:10:57 arnold-laptop kernel: [  250.508000] IN= OUT=eth0 SRC=169.254.6.164 DST=169.254.255.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 
Aug 25 17:11:06 arnold-laptop pppd[8871]: LCP: timeout sending Config-Requests 
Aug 25 17:11:06 arnold-laptop pppd[8871]: Connection terminated.
Aug 25 17:11:06 arnold-laptop pppd[8871]: Modem hangup
Aug 25 17:11:10 arnold-laptop pppd[8871]: Exit.
Aug 25 17:11:15 arnold-laptop kernel: [  268.228000] NETDEV WATCHDOG: ib0: transmit timed out
Aug 25 17:11:15 arnold-laptop pppd[8894]: pppd 2.4.4 started by root, uid 0
Aug 25 17:11:15 arnold-laptop pppd[8894]: Using interface ppp0
Aug 25 17:11:15 arnold-laptop pppd[8894]: Connect: ppp0 <--> /dev/pts/1

---

### Post by ddrichardson on 2007-08-25
There are a lot of timeouts there. Try increasing the timeout setting in /etc/ppp/pppoe.conf

---

### Post by arnold.pietersen on 2007-08-26
I have increased the timeout settings to 60, but still the same results.

Thanks

Arnold

---

### Post by ddrichardson on 2007-08-26
From the logs, you have it set up correctly - either increase it to 120 secs or contact the ISP.

---

### Post by arnold.pietersen on 2007-09-05
I got my iBurst working.  Maybe it was working all along.

What I did was to disconnect the iBurst and turn the laptop on.  Once everything was loaded, I connected by USB iBurst modem.  I type sudo pppoe-start and then my password.  Guess what: it says connected and I am then able to surf the net and send and receive e-mails.

Thanks for everyone

Arnold

---

