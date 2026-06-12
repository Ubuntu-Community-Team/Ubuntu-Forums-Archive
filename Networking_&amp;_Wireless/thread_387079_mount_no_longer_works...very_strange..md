---
title: "mount no longer works...very strange."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by Smidley on 2007-03-17
When I would enter " sudo mount -t smbfs //HOME/Desktop /mnt/smb/Desktop" it always worked until now.

Now I get this:

> timeout connecting to 154.6.66.65:445
timeout connecting to 154.6.66.65:139
Error connecting to 154.6.66.65 (Operation already in progress)
5466: Connection to HOME failed
SMB connection failed

I did a Whois search on the IP and got this:

> OrgName:    Performance Systems International 
OrgID:      PSI-2
Address:    1015 31st St NW
City:       Washington
StateProv:  DC
PostalCode: 20007
Country:    US

NetRange:   154.6.0.0 - 154.6.255.255 
CIDR:       154.6.0.0/16 
NetName:    PSINET-B2-6
NetHandle:  NET-154-6-0-0-1
Parent:     NET-154-0-0-0-0
NetType:    Direct Assignment
NameServer: NS.PSI.NET
NameServer: NS2.PSI.NET
Comment:    
RegDate:    1992-02-05
Updated:    1992-02-06

OrgAbuseHandle: COGEN-ARIN
OrgAbuseName:   Cogent Abuse 
OrgAbusePhone:  +1-877-875-4311
OrgAbuseEmail:  [email]abuse@cogentco.com[/email]

OrgNOCHandle: ZC108-ARIN
OrgNOCName:   Cogent Communications 
OrgNOCPhone:  +1-877-875-4311
OrgNOCEmail:  [email]noc@cogentco.com[/email]

OrgTechHandle: IPALL-ARIN
OrgTechName:   IP Allocation 
OrgTechPhone:  +1-877-875-4311
OrgTechEmail:  [email]ipalloc@cogentco.com[/email]

Is it just me, or is that really weird?  Is there a configuration file that I can edit?  I wouldn't begin to know where to search.

I'm running Edgy on a Dell Inspiron E1705 and the two computers are connected through a WRT54GS running DD-WRT v23 SP2.

Any help would be greatly appreciated.  TIA!

:guitar:

---

### Post by Smidley on 2007-03-18
Bump.

---

### Post by Smidley on 2007-03-18
OK...I figured it out.

I don't know why it worked at first, but here's how I did it now:

sudo mount -t smbfs -o username=[removed],password=[removed] \\\\192.168.1.100\\c$ /mnt/smb/c

---

