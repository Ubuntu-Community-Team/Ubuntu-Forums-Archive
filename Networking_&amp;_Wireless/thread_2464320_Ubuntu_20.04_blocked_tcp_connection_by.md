---
title: "Ubuntu 20.04 blocked tcp connection by?"
date: 2021-06-29
forum: Networking &amp; Wireless
---

### Post by davidmartib on 2021-06-29
Dear community,

I have an Ubuntu 20.04 server with iRedAdmin installation (postfix, dovecot, fail2ban ...) and Zabbix server.

My goal is open 10051/tcp port and remote agents can connect to my Zabbix Server. UFW is active, rule to allow 10051/tcp connections is enabled, but I can't connect from any remote address (for example, using telnet MY_PUBLIC_IP 10051).

If I try to connect from inside the server (using telnet localhost 10051) I can connect to my Zabbix Server.

If I disable UFW, I'm still unable to connect from remote locations ....

Other ports, like HTTP, HTTPS, IMAP, SMTP are working with no problems.

What kind of filter or process can be blocking 10051/tcp? Can be fail2ban??

Thanks in advance for your help!!

---

### Post by davidmartib on 2021-06-29
The problem is nftables is in action too. I've disabled nftables and all is working.

Thanks!

---

