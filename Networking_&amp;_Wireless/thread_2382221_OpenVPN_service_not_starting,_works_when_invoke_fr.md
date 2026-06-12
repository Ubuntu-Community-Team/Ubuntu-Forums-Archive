---
title: "OpenVPN service not starting, works when invoke from command line"
date: 2018-01-10
forum: Networking &amp; Wireless
---

### Post by fmeehan on 2018-01-10
Hi all,

I moved an OpenVPN instance to another server (Ubuntu 16.04). restored OpenVPN directory from old server /etc/openvpn. 

OpenVPN works only when invoked on the command line (sudo or as root): sudo openvpn --config /etc/openvpn/openvpn.conf

When starting with systemctl, no error are displayed, it just won't start. Verbose is set to 6 in the config file, all I can see in syslog is this: 

Jan 10 13:46:06 mtlsrv systemd[1]: Starting OpenVPN service...
Jan 10 13:46:06 mtlsrv systemd[1]: Started OpenVPN service.

No tun interface appears in ifconfig. 

Any ideas?

Thanks in advance, 

François

---

### Post by TheFu on 2018-01-10
What is the exact systemctl command used?

Mine works and is:
```
$ sudo systemctl restart openvpn@vpnserver.service

```
BTW, vpnserver.conf is the name of my conf file.

---

