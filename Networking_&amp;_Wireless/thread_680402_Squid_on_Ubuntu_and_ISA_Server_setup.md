---
title: "Squid on Ubuntu and ISA Server setup"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by ian.gutsy on 2008-01-27
For now, our academy network setup looks like this:

   NET(Router Modem)<------- M$ ISA Server------
                                                                  |
                                                                  |
                                M$ SQL Server -------Switch ------- M$ Web Server
                                   M$ FTP Server ____ /  |  \____ M$ PDC Server
                                                                  |
                                                                LAN

Kindly refer to the attached picture for a clearer network setup image.

and im planning to use another PC with ubuntu gutsy and squid as my caching machine and not the ISA. Where in my network would i probably place my gutsy PC so that it would be my caching server. What other ISA configuration changes would it need so as to direct all caching services to the Ununtu machine still giving the ISA its firewall functions.

Note: The SQL, Web, and FTP servers are only used inside the LAN applications.

Thank You

---

