---
title: "xl2tpd doesn't connect"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by maidantal on 2007-11-10
Please help me to solve this problem
I work with Windows and try now to migrate to Linux, but I am unable to
 connect to Internet (my provider uses l2tp)

xl2tpd-1.1.12 doesn't establish connection under xubuntu 7.10. I got
 the following log 

xl2tpd[5544]: This binary does not support kernel L2TP. 
xl2tpd[5545]: xl2tpd version xl2tpd-1.1.12 started on yurovsky-desktop  PID:5545 
xl2tpd[5545]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc. 
xl2tpd[5545]: Forked by Scott Balmos and David Stipp, (C) 2001 
xl2tpd[5545]: Inherited by Jeff McAdams, (C) 2002 
xl2tpd[5545]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006 
xl2tpd[5545]: Listening on IP address 0.0.0.0, port 1701 
xl2tpd[5545]: get_call: allocating new tunnel for host 62.90.5.3, port 1701. 
xl2tpd[5545]: Connecting to host 62.90.5.3, port 1701 
xl2tpd[5545]: control_finish: message type is (null)(0).  Tunnel is 0, call is 0. 
xl2tpd[5545]: control_finish: sending SCCRQ 

Except of this, the directory /var/run/xl2tpd is removed after each
 system restart (the log above obtained after creation of this directory)

I was able to connect to Internet on the same computer at the same day
 with xl2tpd-1.1.09 under fedora 6. However, I prefer ubuntu, but may be
 that log can help to solve this problem (all configuration files are
 the same)

xl2tpd[3453]: This binary does not support kernel L2TP. 
xl2tpd[3454]: xl2tpd version xl2tpd-1.1.09 started on yurovsky-desktop PID:3454 
xl2tpd[3454]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc. 
xl2tpd[3454]: Forked by Scott Balmos and David Stipp, (C) 2001 
xl2tpd[3454]: Inherited by Jeff McAdams, (C) 2002 
xl2tpd[3454]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006 
xl2tpd[3454]: Listening on IP address 0.0.0.0, port 1701 
xl2tpd[3454]: Connecting to host 62.90.5.2, port 1701 
xl2tpd[3454]: Connection established to 62.90.5.2, 1701.  Local: 42528, Remote: 55771 (ref=0/0). 
xl2tpd[3454]: Calling on tunnel 42528 
xl2tpd[3454]: Call established with 62.90.5.2, Local: 21425, Remote: 5726, Serial: 1 (ref=0/0) 
kernel: CSLIP: code copyright 1989 Regents of the University of California
kernel: PPP generic driver version 2.4.2
pppd[3457]: pppd 2.4.4 started by root, uid 0
pppd[3457]: Using interface ppp0
pppd[3457]: Connect: ppp0 <--> /dev/pts/2
pppd[3457]: PAP authentication succeeded
kernel: PPP Deflate Compression module registered
pppd[3457]: local  IP address 89.1.14.173
pppd[3457]: remote IP address 212.29.206.145
pppd[3457]: primary   DNS address 62.90.42.110
pppd[3457]: secondary DNS address 212.150.49.10

---

