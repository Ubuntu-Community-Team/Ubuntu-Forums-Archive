---
title: "Ubuntu VPN"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by livestockPimp on 2007-08-22
Hey, I have been trying to set up a vpn for windows clients to log into a work network, I have installed pptpd, configured it correctly and ensured the ppp_mppe module is loaded.
When I try to connect in from a windows machine it attempts, takes under 2 seconds and throws an error 619. below i have copied the linux logs (ip addresses have been removed).

Thanks.

Aug 23 00:28:31 server pptpd[5399]: CTRL: Client x.x.x.x control connection started
Aug 23 00:28:31 server pptpd[5399]: CTRL: Starting call (launching pppd, opening GRE)
Aug 23 00:28:31 server pppd[5400]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.3, this is 2.4.4
Aug 23 00:28:31 server pptpd[5399]: GRE: read(fd=6,buffer=8058640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Aug 23 00:28:31 server pptpd[5399]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Aug 23 00:28:31 server pptpd[5399]: CTRL: Reaping child PPP[5400]
Aug 23 00:28:31 server pptpd[5399]: CTRL: Client x.x.x.x control connection finished

---

