---
title: "Problem with Marvell 88E8038 ethernet"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by computerman413 on 2008-01-23
When I try to run a DHCP server on my computer, I get the following errors from syslog. Any thoughts? I'm running 7.10, with kernel 2.6.22-14-generic. Thanks a lot.

From lspci:
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)

From syslog:
Jan 22 23:25:57 williamsnotebook kernel: [ 4185.736000] device eth0 entered promiscuous mode
Jan 22 23:25:57 williamsnotebook kernel: [ 4185.736000] audit(1201062357.428:12): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jan 22 23:26:07 williamsnotebook kernel: [ 4195.576000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:26:14 williamsnotebook kernel: [ 4202.868000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:26:22 williamsnotebook kernel: [ 4210.416000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:26:28 williamsnotebook kernel: [ 4216.260000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:26:39 williamsnotebook kernel: [ 4227.804000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:26:47 williamsnotebook kernel: [ 4235.804000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:27:15 williamsnotebook kernel: [ 4263.740000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:27:17 williamsnotebook kernel: [ 4265.800000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:27:18 williamsnotebook ntpd[8951]: Listening on interface #7 eth0, 192.168.1.1#123 Enabled
Jan 22 23:27:25 williamsnotebook kernel: [ 4273.736000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:27:34 williamsnotebook kernel: [ 4282.800000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:27:52 williamsnotebook kernel: [ 4300.108000] sky2 eth0: rx error, status 0x5c0202 length 92
Jan 22 23:28:04 williamsnotebook kernel: [ 4312.876000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:08 williamsnotebook kernel: [ 4316.904000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:28:10 williamsnotebook kernel: [ 4318.736000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:28:14 williamsnotebook kernel: [ 4322.872000] sky2 eth0: rx error, status 0x710202 length 113
Jan 22 23:28:20 williamsnotebook kernel: [ 4328.592000] sky2 eth0: rx error, status 0x1570202 length 343
Jan 22 23:28:24 williamsnotebook kernel: [ 4332.872000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:34 williamsnotebook kernel: [ 4342.872000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:44 williamsnotebook kernel: [ 4352.028000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:53 williamsnotebook kernel: [ 4361.824000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:54 williamsnotebook kernel: [ 4362.636000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:54 williamsnotebook kernel: [ 4362.696000] sky2 eth0: rx error, status 0x620202 length 98
Jan 22 23:28:55 williamsnotebook kernel: [ 4363.508000] sky2 eth0: rx error, status 0x620202 length 98

---

