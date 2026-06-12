---
title: "where this ip adreess is coming from?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-10
whenever i start running firefox it seems that im getting connections from 204.152.184.113.can anyone indentify this adreess?

---

### Post by studavis on 2009-07-10
Google whois then the ip address

---

### Post by hansdown on 2009-07-10
Hi heyyy.

You can open a terminal and ....```
 whois 204.152.184.113
```

---

### Post by Peter09 on 2009-07-10
using th command

```
whois 204.152.184.113
```

in a terminal suggests that this is a nameserver, (which is what you would expect to be talking to)

---

### Post by yeats on 2009-07-10
Reverse DNS lookup shows:

```
$ host 204.152.184.113
113.184.152.204.in-addr.arpa domain name pointer mozilla.isc.org.
```

---

### Post by studavis on 2009-07-10
Nice one, never fails to amaze me what can be done from Terminal....

---

### Post by wojox on 2009-07-10
Resolve

    204.152.184.113 resolves to mozilla.isc.org

DNS Query Results:

    ; <<>> DiG 9.5.0-P2 <<>> any mozilla.isc.org
    ;; global options:  printcmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11142
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mozilla.isc.org.		IN	ANY

    ;; ANSWER SECTION:
    mozilla.isc.org.	40630	IN	AAAA	2001:4f8:0:2::1f
    mozilla.isc.org.	42143	IN	A	204.152.184.113

    ;; Query time: 14 msec
    ;; SERVER: 68.87.74.166#53(68.87.74.166)
    ;; WHEN: Fri Jul 10 07:29:44 2009
    ;; MSG SIZE  rcvd: 77


WWWhois Results:

    % CORE - [Internet Council of Registrars]
    %
    % NOTICE: Access to the domains information is provided to assist in
    % determining the contents of a domain name registration record in the
    % CORE database. The data in this record is provided by CORE for
    % informational purposes only, and CORE does not guarantee its
    % accuracy. This service is intended only for query-based access. You
    % agree that you will use this data only for lawful purposes and that,
    % under no circumstances will you use this data to: (a) allow, enable,
    % or otherwise support the transmission by e-mail, telephone, or
    % facsimile of unsolicited, commercial advertising or solicitations; or
    % (b) enable , automated, electronic processes that send queries or data
    % to the systems of CORE, except as reasonably necessary to register
    % domain names or modify existing registrations. All rights reserved.
    % CORE reserves the right to modify these terms at any time. By submitting
    % this query, you agree to abide by this policy.
    %
    % The requested domain "isc.org" is not registered through CORE.
    % Therefore the following whois server "whois.pir.org" is asked instead.
    %
    % **** Start of data fetched from referral whois ****

    [whois.pir.org]
    NOTICE: Access to .ORG WHOIS information is provided to assist persons in 
    determining the contents of a domain name registration record in the Public Interest Registry
    registry database. The data in this record is provided by Public Interest Registry
    for informational purposes only, and Public Interest Registry does not guarantee its 
    accuracy.  This service is intended only for query-based access.  You agree 
    that you will use this data only for lawful purposes and that, under no 
    circumstances will you use this data to: (a) allow, enable, or otherwise 
    support the transmission by e-mail, telephone, or facsimile of mass 
    unsolicited, commercial advertising or solicitations to entities other than 
    the data recipient's own existing customers; or (b) enable high volume, 
    automated, electronic processes that send queries or data to the systems of 
    Registry Operator or any ICANN-Accredited Registrar, except as reasonably 
    necessary to register domain names or modify existing registrations.  All 
    rights reserved. Public Interest Registry reserves the right to modify these terms at any 
    time. By submitting this query, you agree to abide by this policy. 

    Domain ID:D2338103-LROR
    Domain Name:ISC.ORG
    Created On:04-Apr-1994 04:00:00 UTC
    Last Updated On:14-Dec-2008 00:49:59 UTC
    Expiration Date:05-Apr-2012 04:00:00 UTC
    Sponsoring Registrar:CSL Computer Service Langenbach GmbH d/b/a joker.com a German GmbH (R25-LROR)
    Status:CLIENT TRANSFER PROHIBITED
    Registrant ID:CORG-229619
    Registrant Name:Internet Systems Consortium, Inc.
    Registrant Street1:950 Charter Street
    Registrant Street2:
    Registrant Street3:
    Registrant City:Redwood City
    Registrant State/Province:--
    Registrant Postal Code:94063
    Registrant Country:US
    Registrant Phone:+1.6507797000
    Registrant Phone Ext.:
    Registrant FAX:+1.6507797055
    Registrant FAX Ext.:
    Registrant Email:domain-admin@isc.org
    Admin ID:CORG-229618
    Admin Name:Internet Systems Consortium, Inc.
    Admin Street1:950 Charter Street
    Admin Street2:
    Admin Street3:
    Admin City:Redwood City
    Admin State/Province:CA
    Admin Postal Code:94063
    Admin Country:US
    Admin Phone:+1.6504231300
    Admin Phone Ext.:
    Admin FAX:+1.6504231355
    Admin FAX Ext.:
    Admin Email:hostmaster@isc.org
    Tech ID:CORG-229620
    Tech Name:Internet Systems Consortium, Inc.
    Tech Street1:950 Charter Street
    Tech Street2:
    Tech Street3:
    Tech City:Redwood City
    Tech State/Province:CA
    Tech Postal Code:94063
    Tech Country:US
    Tech Phone:+1.6507797000
    Tech Phone Ext.:
    Tech FAX:+1.6507797055
    Tech FAX Ext.:
    Tech Email:hostmaster@isc.org
    Name Server:NS-EXT.NRT1.ISC.ORG
    Name Server:SFBA.SNS-PB.ISC.ORG
    Name Server:ORD.SNS-PB.ISC.ORG
    Name Server:AMS.SNS-PB.ISC.ORG
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 
    Name Server: 

    % **** End of data fetched from referral whois ****


RIR Whois Results:

    OrgName:    Internet Systems Consortium, Inc. 
    OrgID:      ISC-94-Z
    Address:    950 Charter Street
    City:       Redwood City
    StateProv:  CA
    PostalCode: 94063
    Country:    US

    NetRange:   204.152.184.0 - 204.152.191.255 
    CIDR:       204.152.184.0/21 
    OriginAS:   AS1280
    NetName:    ISC-NET2
    NetHandle:  NET-204-152-184-0-1
    Parent:     NET-204-0-0-0-0
    NetType:    Direct Allocation
    NameServer: SFBA.SNS-PB.ISC.ORG
    NameServer: AMS.SNS-PB.ISC.ORG
    NameServer: ORD.SNS-PB.ISC.ORG
    Comment:    
    RegDate:    1997-02-26
    Updated:    2009-02-20

    RAbuseHandle: ISCAT-ARIN
    RAbuseName:   Internet Systems Consortium Abuse Team 
    RAbusePhone:  +1-650-423-1300
    RAbuseEmail:  [email]abuse@isc.org[/email] 

    RNOCHandle: ISCN-ARIN
    RNOCName:   Internet Systems Consortium NOC 
    RNOCPhone:  +1-650-423-1310
    RNOCEmail:  [email]noc@isc.org[/email] 

    RTechHandle: JDA87-ARIN
    RTechName:   Damas, Joao 
    RTechPhone:  +1-650-423-1312
    RTechEmail:  [email]Joao_Damas@isc.org[/email] 

    OrgAbuseHandle: ISCAT-ARIN
    OrgAbuseName:   Internet Systems Consortium Abuse Team 
    OrgAbusePhone:  +1-650-423-1300
    OrgAbuseEmail:  [email]abuse@isc.org[/email]

    OrgNOCHandle: ISCN-ARIN
    OrgNOCName:   Internet Systems Consortium NOC 
    OrgNOCPhone:  +1-650-423-1310
    OrgNOCEmail:  [email]noc@isc.org[/email]

    OrgTechHandle: JDA87-ARIN
    OrgTechName:   Damas, Joao 
    OrgTechPhone:  +1-650-423-1312
    OrgTechEmail:  [email]Joao_Damas@isc.org[/email]

    # ARIN WHOIS database, last updated 2009-07-09 20:00
    # Enter ? for additional hints on searching ARIN's WHOIS database.

Check Port:

    Port 80 is open

Ping Results:

    PING 204.152.184.113 (204.152.184.113) 56(84) bytes of data.
    64 bytes from 204.152.184.113: icmp_seq=1 ttl=50 time=94.1 ms
    64 bytes from 204.152.184.113: icmp_seq=2 ttl=50 time=95.4 ms
    64 bytes from 204.152.184.113: icmp_seq=3 ttl=50 time=92.8 ms
    64 bytes from 204.152.184.113: icmp_seq=4 ttl=50 time=95.1 ms
    64 bytes from 204.152.184.113: icmp_seq=5 ttl=50 time=94.8 ms

    --- 204.152.184.113 ping statistics ---
    5 packets transmitted, 5 received, 0% packet loss, time 4034ms
    rtt min/avg/max/mdev = 92.803/94.481/95.440/0.957 ms

Traceroute Results:

    traceroute to 204.152.184.113 (204.152.184.113), 30 hops max, 40 byte packets
     1  192.168.1.1 (192.168.1.1)  1.283 ms  2.063 ms  1.298 ms
     2  96.131.129.1 (96.131.129.1)  10.645 ms  10.769 ms  11.943 ms
     3  ge-2-41-ur01.portcharlott.fl.westfl.comcast.net (68.85.213.137)  13.678 ms  13.805 ms  13.951 ms
     4  te-8-2-ur01.northport.fl.westfl.comcast.net (68.87.238.65)  16.591 ms  16.745 ms  17.120 ms
     5  te-8-4-ar02.venice.fl.westfl.comcast.net (68.87.238.25)  17.275 ms  17.331 ms  17.465 ms
     6  te-7-1-ar01.bonitasprngs.fl.naples.comcast.net (68.85.229.249)  22.882 ms  11.113 ms  11.580 ms
     7  te-9-1-ar02.bonitasprngs.fl.naples.comcast.net (68.87.236.106)  11.097 ms  11.529 ms  15.643 ms
     8  te-0-2-0-5-ar03.northdade.fl.pompano.comcast.net (68.85.229.253)  21.635 ms  21.786 ms  22.092 ms
     9  pos-0-5-0-0-cr01.miami.fl.ibone.comcast.net (68.86.91.81)  21.072 ms  26.573 ms  26.729 ms
    10  pos-2-3-0-0-cr01.atlanta.ga.ibone.comcast.net (68.86.85.193)  39.814 ms  39.966 ms  40.115 ms
    11  pos-1-14-0-0-cr01.dallas.tx.ibone.comcast.net (68.86.85.153)  60.133 ms  60.284 ms  52.847 ms
    12  pos-0-12-0-0-cr01.losangeles.ca.ibone.comcast.net (68.86.86.117)  91.458 ms  91.614 ms  87.536 ms
    13  pos-1-15-0-0-cr01.sanjose.ca.ibone.comcast.net (68.86.85.81)  101.961 ms  102.108 ms  102.244 ms
    14  comcast-isc.pao1.isc.org (68.86.88.222)  99.671 ms  100.080 ms  100.246 ms
    15  mozilla.isc.org (204.152.184.113)  105.182 ms  105.334 ms  105.478 ms

---

### Post by credobyte on 2009-07-10
Automatic updates for Mozilla ( that's why it shows up on start, not somewhere in the middle ).

---

### Post by heyyy on 2009-07-10
thank you all

---

