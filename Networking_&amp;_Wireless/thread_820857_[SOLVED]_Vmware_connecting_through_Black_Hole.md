---
title: "[SOLVED] Vmware connecting through Black Hole"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by cariboo on 2008-06-06
Does anybody know why this is happening:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.161.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.217.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

This is the output of whois:

```
jimk@intrepid:~$ whois 172.16.161.0 

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   172.16.0.0 - 172.31.255.255 
CIDR:       172.16.0.0/12 
NetName:    IANA-BBLK-RESERVED
NetHandle:  NET-172-16-0-0-1
Parent:     NET-172-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    http://www.arin.net/reference/rfc/rfc1918.txt
RegDate:    1994-03-15
Updated:    2007-11-27

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  abuse@iana.org

# ARIN WHOIS database, last updated 2008-06-05 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.
```

As you can see VMNET8 and VMNET1 are connecting through Black Hole servers. Why is Vmware doing this?

JIm

---

### Post by PilotJLR on 2008-06-06
This is because 172.16.x.x - 172.31.x.x are a range of private Class B addresses, and are not routable over the Internet.

---

