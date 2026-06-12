---
title: "pptp server bug"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by ezacon on 2007-01-10
I need to configure a pptp server in my firewall based on edgy (server).
I know there is a bug i pptpd package in ubuntu and debian that produces this error when you try to connect:

Jan 10 20:20:56 tip pppd[21039]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.3, this is 2.4.4
Jan 10 20:20:56 tip pptpd[21038]: GRE: read(fd=6,buffer=8058640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs

Does anybody know how to solve this?

---

### Post by ezacon on 2007-01-13
I found that remarking line "logwtmp" in /etc/pptpd.conf solve the problem.
Does anybody know what is logwtmp module for?

---

