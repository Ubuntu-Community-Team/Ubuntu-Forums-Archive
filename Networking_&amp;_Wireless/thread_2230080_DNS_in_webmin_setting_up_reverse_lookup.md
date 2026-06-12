---
title: "DNS in webmin setting up reverse lookup"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by vrghost on 2014-06-17
So been struggling with this a bit, trying to set up the DNS, and so far it is working quite OK, but the reverse lookup is just not populating from the zone. What I have done so far is:

Set up master zone, lest call it master.local
Set up a second master zone as reverse backup. Its on 192.168.0
I have attached my laptop as a test, and it can do lookups against master.local, including forwarding to the ISP DNSs all nice.
I then tried reverse lookup, and non (not even the DNS own IP) worked and I get:
> > 192.168.0.173Server:        192.168.0.173
Address:    192.168.0.173#53


** server can't find 173.0.168.192.in-addr.arpa.: NXDOMAIN

I then tried to add a record manually to the zone 192.168.0 and I get the correct response, so the zone seems to work for reverse lookups. 
> > 192.168.0.19Server:        192.168.0.173
Address:    192.168.0.173#53


19.0.168.192.in-addr.arpa    name = PreBBX.

So, what am I missing, is there an obvious option that I have just overlooked, the one part I don't seem to be able to figure out is, where do I tell the reverse lookup zone that it should populate from the normal zone (master.local)

Here are my config files (names and keys changed to protect the innocent:) )

/etc/bind/named.conf.local
> 
//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "master.local" {
	type master;
	file "/var/lib/bind/master.local.hosts";
	};
zone "0.168.192.in-addr.arpa" {
	type master;
	file "/var/lib/bind/192.168.0.rev";
	};


/var/lib/bind/192.168.0.rev
> 
$ttl 38400
0.168.192.in-addr.arpa.	IN	SOA	U01.master.local. bengt\.bjrkerg.db
fs.co.uk. (
			1402933810
			10800
			3600
			604800
			38400 )
0.168.192.in-addr.arpa.	IN	NS	U01.dbfs.local.
19.0.168.192.in-addr.arpa.	IN	PTR	PreBBX.
0.168.192.in-addr.arpa.	IN	DNSKEY	257 3 5 AwEAAb9AnbaEpOb2WMyocqvXIosJschl
WE8N4Q5HNmCakZzcaVlGcwbN ZmIEZXXXXXXXXXXXXXXXXXXXX1gnDDOSD0+XJz8gYCdck9J
i FUzzWLDpVoR1oaSP5LXXXXXXXXXXXXSgfYImnRpYB5w1/K 9VHL554wPFPUItkfDfzvg
FoBQpd9Wx6pmphyWl8nAuvbkpQYF88=
0.168.192.in-addr.arpa.	IN	DNSKEY	256 3 5 AwEAAeIz+XXXXXXXXXXXYRteH+H2Ji9l5QL0
UAWUV9zDZO/6vBZhjg4HyvVH YFXXXXXXXXXXXXXXXXXkjlRkbl/sh0l5HGFAKV7bhmsCGEiZu+8
F Cysx1I04jlkPcXXXXXXXXXX/hivbRPrTRVxlmrSnHBBrg0b 8luWF7USrKh8ucY2Ky5DS
IU9bjf+Egtb+/FyTXSHglxVHl1/te0=
0.168.192.in-addr.arpa.	38400	IN	RRSIG	SOA 5 5 38400 20140717084936 201
40617084936 23931 0.168.192.in-addr.arpa. quF0MAgHva7f0cKPLmNeHi4UEzvn/mlxzRa2 3
MBysacsXXXXXXXXXXXXXXXXX0UnepBu3sR2jpW2XXXXXXXXXXXXXXXXXXXQ0wwTNPM7j tv+SvKi
ymQI7/vWyGDQ8pxmlZA9QHzX1gNTy lKW0xXXXXXXXXXXXXXKFiWto/bjneL4UpQ Jh+XY7wBIsNti
P1ijBnmuQS0V0Gvd6EpWQ==
0.168.192.in-addr.arpa.	38400	IN	RRSIG	NS 5 5 38400 20140716145949 2014
0616145949 23931 0.168.192.in-addr.arpa. gqenNCK+NYJhzzbA0a5RSa79df5mRe6Z3J2i 4C
lFjmICSWDhUdafSpNKbwbaue2NzksXXXXXXXXXXXXXXXXXdX20InG6wJuLymJHhikqu63 KZrcTK3K
GM+GqHKv9YJ1fl6gMSbqiog0XXXXXXXXXXXXXXX0PH2aMouu5JvWYXDGMvZ0aq4+v el9RIskESL8iPl
lHR5612BI2VGy1Wd/EIA==
0.168.192.in-addr.arpa.	38400	IN	NSEC	19.0.168.192.in-addr.arpa. NS SO
A RRSIG NSEC DNSKEY
0.168.192.in-addr.arpa.	38400	IN	RRSIG	NSEC 5 5 38400 20140716145949 20
140616145949 23931 0.168.192.in-addr.arpa. aoXMv2RD5TNpQhGyDPm4SHeXMtHejqYrK+AQ
i2w3Iye0YMfDFxRXkxu4TICXXXXXXXXXXXXXXXXXXXXXXXXXXXXXqDyq3obBqKFN23HYTm3F+d4kbLM +uNtVaehB8HU
pg72qe/x7jR3+qj+QyvVCg==
0.168.192.in-addr.arpa.	38400	IN	RRSIG	DNSKEY 5 5 38400 20140716145949
20140616145949 23931 0.168.192.in-addr.arpa. N8hCAp4mxjc/x7lfgveWhTodcqlYaX51J1A
i 5ce+OrOZ4/J0uQXXXXXXXXXXXXXXXXXXXXOKR6eGRiKi62mf1AUK19OprHXY6W1dAScJ+V BQUH
fYgi2b2HqhjMivFQ829XhI9IV7S2p6qf XJEMP5Zoi8qR1fkI4g5vqWK3XBQfgqgrgBw/ n7XyCcAsu6
4WnfIZNvlDSkYeXmiOuHIChg==
0.168.192.in-addr.arpa.	38400	IN	RRSIG	DNSKEY 5 5 38400 20140716145949
20140616145949 55543 0.168.192.in-addr.arpa. Tf5TdBFMoSkDhGQ7QSkjnLACW2pxJVBu0gU
j lqUQvavgcbjmo05nXBXXXXXXXXXXXXXXXXXXXXXXXXXXXXP07dJEZICX1abQLaa6+awNcYRF AV7n
7EBHuWjuQHx761vk27PeSFP2iMUuxsJu GiZN4ZuUzNy2ENpp3CfJI5qU5FAT/FfnsfDp MLrWN3aWLC
EPJN+1asJd96DLnRlRGjX5Tg==
19.0.168.192.in-addr.arpa.	38400	IN	RRSIG	PTR 5 6 38400 2014071614
5949 20140616145949 23931 0.168.192.in-addr.arpa. Ot6I+AZgMyNZcU7ju9jo3by2kvb2ke
rrCzq8 00zz/+kZtL2P7s5UgsJSalcdWgZ7XhpajtgX hFmMViA6qAphcrCjYlrzyqz9yDRnJblN7075
 brwN4nM7ZaBw4iopC9XXXXXXXXXXXXXXXXXXXXXXXXXXXmG9Z66GMb+/SzsxYrpQTwdmzj 4898W
oFBSO/fD4LBaA16zzyY29a/w9nIFw==
19.0.168.192.in-addr.arpa.	38400	IN	NSEC	0.168.192.in-addr.arpa.
PTR RRSIG NSEC
19.0.168.192.in-addr.arpa.	38400	IN	RRSIG	NSEC 5 6 38400 201407170
84936 20140617084936 23931 0.168.192.in-addr.arpa. R3jXT16u4hxvgmEMaRE3O9WfqV7XY
9IMatJj gi4iZXZfnLcdOXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXCliQuk2iLZec7V1DeA4t9mGzlN/M
a qGRuYH1ABTMXyeTClxk0M0jzhdCXwXdTM6mS I2qBlqyoLGoZ5EJEGblmZ/ayQy18LDRxVaAB 2tIg
vGNSgnN4Bg4741yiSGDQ9QQ6Ims1zg==


/var/lib/bind/master.local.hosts
> 
$ttl 38400
master.local.	IN	SOA	DBFS-U01.dbfs.local. bengt\.bjorkberg.dbfs.co.uk
. (
			1402931575
			10800
			3600
			604800
			38400 )
master.local.	IN	NS	U01.master.local.
PBX.master.local.	IN	A	192.168.0.20
PBX-TFTP.master.local.	IN	A	192.168.0.21
Richmond1.master.local.	IN	A	192.168.0.224
............... (loads of records and keys for the records)



Any help would be welcome

---

### Post by vrghost on 2014-06-17
I think I might have solved it.
A bit of a failure on my end about how it works.

For permanent records, both the normal zone and the reverse zone has to be set up before you add hosts. webmin will then update both when you add a host, it is not a automatic feeding or lookup process (which I thought it was)

---

