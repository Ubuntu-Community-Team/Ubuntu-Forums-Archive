---
title: "BIND9 - Subdomain forwarding."
date: 2023-11-19
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2023-11-19
Sorry,
I know this a stupid question. 
I searched a lot - but I don't get the answer.
I've got BIND9 and kea dhcp running.
The target is  to stetup ORACLE GNS.
[https://docs.oracle.com/en/database/oracle/oracle-database/19/cwlin/configuring-dns-for-cluster-domain-delegation-to-grid-naming-service.html#GUID-F70FF3DD-7931-4B4A-94F0-FB6C51DA7DA5](https://docs.oracle.com/en/database/oracle/oracle-database/19/cwlin/configuring-dns-for-cluster-domain-delegation-to-grid-naming-service.html#GUID-F70FF3DD-7931-4B4A-94F0-FB6C51DA7DA5)

They say:
***In the DNS, create an entry for the GNS virtual IP address, where the address uses the form gns-server.clustername.domainname.***
***For example, where the cluster name is mycluster, and the domain name is example.com, and the IP address is 192.0.2.1, create an entry similar to the following:***
[I][B][COLOR=#ff0000]>> mycluster-gns-vip.example.com  A  192.0.2.1 <<[/COLOR]
[/B][/I]
***Set up forwarding of the GNS subdomain to the GNS virtual IP address, ***
***so that GNS resolves addresses to the GNS subdomain.***
***To do this, create a BIND configuration entry similar to the following for the delegated domain, ***
[I][B]where cluster01.example.com is the subdomain you want to delegate:
[/B][/I]
[COLOR=#ff0000]***>> cluster01.example.com  NS  mycluster-gns-vip.example.com  <<***[/COLOR]

[SIZE=1][SIZE=3]This does not work (Lookup Host to IP failes)[/SIZE]

[/SIZE][SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   PRVF-5218 : Domain name "node2-vip.RCA.cluster01.darkwing.net" did not[/SIZE]
[SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   resolve to an IP address.[/SIZE]
[SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   PRVF-5218 : Domain name "RCA-scan.RCA.cluster01.darkwing.net" did not resolve[/SIZE]
[SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   to an IP address.[/SIZE]
[SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   PRVF-5218 : Domain name "node1-vip.RCA.cluster01.darkwing.net" did not[/SIZE]
[SIZE=1]INFO:  [Nov 19, 2023 11:37:07 PM]   resolve to an IP address.[/SIZE]



So I changed to this:

$ORIGIN .
$TTL 604800     ; 1 week
darkwing.net            IN SOA  dnsdcp.darkwing.net. admin.darkwing.net. (
                                46         ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )
                        NS      dnsdcp.darkwing.net.
$ORIGIN darkwing.net.
BASIS                   A       192.168.50.51


**cluster-gns-vip         A       192.168.100.100**

dnsdcp                  A       192.168.50.41
ISCSI                   A       192.168.50.45
ISCSI-SAN1              A       192.168.51.101
ISCSI-SAN2              A       192.168.51.102
LinuxWS                 A       192.168.50.50
NODE1-SAN               A       192.168.51.111
NODE2-PRIV              A       192.168.52.112
NODE2-SAN               A       192.168.51.112

**$ORIGIN cluster01.darkwing.net.**
**@       IN      NS      cluster-gns-vip.darkwing.net.**


Is this the right way tp make an deligation?
 Can anyone give me a helping hand
Thx
Christian

---

