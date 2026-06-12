---
title: "OpenVPN to secure an SQL-Server"
date: 2022-10-13
forum: Networking &amp; Wireless
---

### Post by wurzelsepp1 on 2022-10-13
Good morning experts :)

Let me as a beginners question:

I'd like to secure the access to an sql server by setting up a vpn server on the server and tell the Windows clients to route their communications with only the sql server through the vpn.

What I did:

Ubuntu Server 20 LTS with latest stable of open VPN installed. Client on Win installed. Connection and routing of all traffic (only for testing) works fine.

Now, I want the configuration to route only the sql traffic through the vpn and all other date through the existing ethernet / wifi connection.

For that, I removed the options for pushing DNS to the client. even the option to override the dhcp on the client side was removed. Now the traffic is routet through the wifi on the client.

Now I added this lines to the client.ovpn:

```
route-nopull
route 85.214.nn.nn 255.255.255.255

```
The IP is the public IP of ther ubuntu server, where the sql is running.

Unfortunately, the server is not reachable through this config. Pings says "not reachable".

Could someone give me a hint on the correct syntax?

The sql is listening on 1433. This port is blocked on UFW, as I think, the traffic through VPN does not need an ectra rule here.

Thanks in advance,
Alex

---

### Post by TheFu on 2022-10-15
[https://www.cyberciti.biz/faq/ubuntu-22-04-lts-set-up-openvpn-server-in-5-minutes/](https://www.cyberciti.biz/faq/ubuntu-22-04-lts-set-up-openvpn-server-in-5-minutes/) how-tos have always been short and too the point.

Not that it matters, but which sql-server are you using?  PostgreSQL, MariaDB, Oracle, DB2?

I think most of those have a TLS connection method which is as secure as the TLS we use with HTTPS, assuming TLS v1.3 or later are used.  TLS v1.2 and earlier are all hacked at this point.  Some web searches say that Windows ovpn clients don't support TLS v1.3, so be certain the clients are compatible with the server.  TLS v1.3 has been the default cipher for a few years in openvpn.

Using a full VPN seems like an unnecessary complication.  Some instructions for different SQL Servers using TLS 1.3 connections::
[https://www.postgresql.org/docs/current/ssl-tcp.html](https://www.postgresql.org/docs/current/ssl-tcp.html)
[https://mariadb.com/kb/en/securing-connections-for-client-and-server/](https://mariadb.com/kb/en/securing-connections-for-client-and-server/)
[https://docs.oracle.com/en/database/oracle/oracle-database/19/dbseg/configuring-secure-sockets-layer-authentication.html](https://docs.oracle.com/en/database/oracle/oracle-database/19/dbseg/configuring-secure-sockets-layer-authentication.html)
[https://www.ibm.com/docs/en/db2/11.5?topic=db2-configuring-tls-support-instance](https://www.ibm.com/docs/en/db2/11.5?topic=db2-configuring-tls-support-instance)
Heck, even MS-SQL 2019 supports TLS [https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine?view=sql-server-ver16](https://learn.microsoft.com/en-us/sql/database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine?view=sql-server-ver16)  though it appears to be v1.2 only (don't trust me).  In the article, they suggest using IPSec for the VPN which is supported by Linux through a few IPSec implementations (FreeSwan and LibreSwan). IPSec is considered more secure than SSL/TLS-based VPNs by security professionals.  Plus, in an IPv6 environment, IPSec should be built into the network stack.  I think IPSec is easier for MacOS clients than openVPN, but I don't know.

I switched to wireguard a few years ago - it is a much simpler VPN without all the complexities that openvpn supports.  When it comes to openvpn, I found that using the default config was the only way to get things working, then I'd tweak from that, maintaining careful config versions, so when I broke it, I could always fall back to the last working setup.  I don't know if wireguard has a MS-Windows client. I know it didn't initially, but that was a few years ago.

The main trick with getting VPNs to connect is always to get the iptables rules correct for inbound forwarding.  Pay attention to those in the first link.

---

