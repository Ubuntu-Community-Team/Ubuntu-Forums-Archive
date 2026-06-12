---
title: "Wireshark, Whois &amp; Internet Assigned Numbers Authority"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by happytimelogan on 2010-04-22
Hi People,

I got turned onto a great sniffing program called wireshark.
After running it and looking at all the traffic going through my computer (very interesting)
I found there was this strange anomoly coming from
192.168.1.65 on my network, now I'm fairly sure this is an internal network address... but I was investigating in the terminal and when i type whois 192.168.1.65 I got back this address:

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

Does anyone know what this means??
I was googling and found loads of people who think this is some kind of Government organisation spying on them or something, but I'm not one to jump to conclusions... especially since it seems to originate from within my network.

Has anyone out there come across something like this before?
Or is it something to be concerned about..?

Thanks in advanced!

---

### Post by jerome1232 on 2010-04-22
IANA are the guys that say that the 192.x.x.x addresses are private addresses.

Actually if you read the whole whois output it kinda explains it


```
whois 192.168.1.64

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    PRIVATE-ADDRESS-CBLK-RFC1918-IANA-RESERVED
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
[B]Comment:    This block is used as private address space.
Comment:    Addresses from this block can be used by
Comment:    anyone without any need to coordinate with
Comment:    IANA or an Internet registry. Addresses from
Comment:    this block are used in multiple, separately
Comment:    operated networks.
Comment:    This block was assigned by the IETF in the
Comment:    Best Current Practice document, RFC 1918
Comment:    which can be found at:
Comment:    http://www.rfc-editor.org/rfc/rfc1918.txt[/B]
RegDate:    1994-03-15
Updated:    2010-03-15

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  abuse@iana.org
```

---

### Post by kingpoiuy on 2010-04-22
Anyone know how they are establishing this IP on a LAN? I noticed this on my friend's LAN as well. It must be coming from the local ISP. Does the "modem" create it?

---

### Post by The Cog on 2010-04-22
IANA have guaranteed never to allocate addresses starting with 192.168 to anyone, so you will never want to talk to one of these adresses over the internet. This means you are free to use these addresses internally and know they will not conflict with anything outside that you might want to talk to. It does mean however that you will have to use address translation when you talk to the outside. Many broadband routers automatically allocate addresses from this range to local PCs when they boot.

Two other address ranges that are also reserved for private use are 172.16.x.x-172.31.x.x and 10.x.x.x.

---

