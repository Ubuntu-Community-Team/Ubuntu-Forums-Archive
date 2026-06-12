---
title: "OpenLDAP samba 8937680 _ldap._tcp.dc._msdcs"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by Belnoctourne on 2008-04-04
I followed the following tutorial [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760) to the letter and I cannot get windows clients to join the domain when attempting to do so i get the following 
```

Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\Windows\debug\dcdiag.txt.

The following error occurred when DNS was queried for the service location (SRV) resource record used to locate an Active Directory Domain Controller for domain yarrrg.net:

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.yarrrg.net

Common causes of this error include the following:

- The DNS SRV records required to locate a AD DC for the domain are not registered in DNS. These records are registered with a DNS server automatically when a AD DC is added to a domain. They are updated by the AD DC at set intervals. This computer is configured to use DNS servers with the following IP addresses:

10.0.0.1

- One or more of the following zones do not include delegation to its child zone:

yarrrg.net
net
. (the root zone)

For information about correcting this problem, click Help.

```
the dns server is correct if on the windows machine I go nslookup blackbeard.yarrrg.net (my DC) it shows the result of 10.0.0.1 which is correct,

I think I just need to add a srv record somehow but im not real sure how to do it im running ubuntu server 7.10 right now with bind 9 I don't think it's a firewall problem cause normal dns (web browsing) works find using that server as a router, if you guys need error logs or config files let me know and I'll post them,

Thanks
Shawn Dixson

---

### Post by Belnoctourne on 2008-04-08
anyone?

---

### Post by sangamc on 2008-06-14
i am having a similar issue. with FDS and samba domain. it turns out you need your dns server to provide specific information to windows clients so that they can join the domain. the how to i was reading had the following dns settings (note the author didnt go into enough detail on setting up dns)

> ]
DNS for the network. For this I used BIND 9.5.0-23, which was the latest. Prior to starting configuring the PDC I needed to set this up. This bit is fairly significant. It allows the Windows workstations to access the domain controller without requiring a third party modifications such as pGina. You will see from the list below that my domain is called "home" (imaginative) and uses the 192.168.1 addresses. The service records are there to enable Windows to identify and talk to the domain controller. This is the data that I used:

@ SOA seagoon root.seagoon.home. ( 7
3H
1H
1W
1H )
NS seagoon
seagoon IN 1H A 192.168.1.2
bloodnock IN 1H A 192.168.1.120
minnie IN 1H A 192.168.1.150
eccles IN 1H A 192.168.1.100
bluebottle IN 1H A 192.168.1.5
_ldap._tcp.dc._msdcs IN 1H SRV 0 100 389 seagoon
_ldap._tcp.pdc._msdcs IN 1H SRV 0 100 389 seagoon
IN 1H SRV 0 100 389 seagoon.home
_ldap._tcp IN 1H SRV 0 100 389 seagoon
_ldap._tcp.home-site._sites IN 1H SRV 0 100 389 seagoon
_ldap._tcp.home_site._sites.dc_msdcs IN 1H SRV 0 100 389 seagoon
_ldap._tcp.gc._msdcs IN 1H SRV 0 100 389 seagoon
_gc._tcp IN 1H SRV 0 100 3268 seagoon
_gc._tcp.home-site._sites IN 1H SRV 0 100 3268 seagoon 



---

