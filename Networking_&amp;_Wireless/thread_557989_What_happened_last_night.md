---
title: "What happened last night?"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by eamonn on 2007-09-23
I was on my laptop last night when FireStarter got that angry thunderbolt. I went to firestarter to see what the deal was and I found out that somebody with the IP address 192.168.0.1 was the problem.  FireStarter said that the service they were running was DNS. 

Now does DNS in Firestarter stand for Denial of Service?

Also, I went into Network Tools (System>Administration>) and looked up that IP address to see who this person might be but the information I got doesn't seem to work out:

> 
OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    
RegDate:    1994-03-15
Updated:    2002-09-16

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

# ARIN WHOIS database, last updated 2007-09-22 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


I used the "whois" function for that. The "lookup" information gave me somehing completly different though:

> min.dns.01.inet.qwest.net. dns-admin.qwestip.net 2007071001 3600 1200 604800 10800'

So I figure that if Qwest is part of the address that I get in the "lookup" section then this probably originated in the Northwest. But, the "whois" thing told me it's from California.

So where did this come from?  Are there any tutorials that can walk me through Network Tools so I know what I'm doing because right now I'm really just plugging the IP into everything and seeing what comes up. I don't really know what I'm doing with it and I'd like to learn.

---

### Post by noob12 on 2007-09-23
I don't know how you are interpreting all of that.

All of the addresses beginning 192.168.x.x  are part of a reserved range that can be used by private networks on LANs.  This address is on your own LAN, probably your router's address.

---

### Post by eamonn on 2007-09-23
Well, I'm stealing my neighbors internet, but why would their router make firestarter go nuts? And is there a tutorial anywhere on Network Tools.

---

### Post by dasunst3r on 2007-09-23
DNS = Domain Name Service
DoS = Denial of Service

Indeed, 192.168.*.* is reserved for LANs.  Also, using your neighbor's Internet is not a very nice thing to do.  Please get your own line.

---

### Post by eamonn on 2007-09-23
I'll get right on top of that dasunst3r. But are there not tutorials kicking around for Network Tools?

---

### Post by SpiritIsReality on 2007-09-23
howdy
some help here maybe
[http://www.google.ca/search?hl=en&q=qwest.net&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=qwest.net&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=iana.org&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=iana.org&btnG=Google+Search&meta=)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=security&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=security&titlesearch=Titles)
[http://ubuntuforums.org/showthread.php?&t=510812](http://ubuntuforums.org/showthread.php?&t=510812)
firestarter
[http://www.google.ca/search?hl=en&q=firestarter+%28tutorials+%7C+guides%29&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=firestarter+%28tutorials+%7C+guides%29&btnG=Google+Search&meta=)
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)
I get the same whois, different lookup.
edit:clicked on help online in network tools, 
[https://launchpad.net/ubuntu/feisty/+sources/gnome-nettool/+gethelp](https://launchpad.net/ubuntu/feisty/+sources/gnome-nettool/+gethelp)
edit:google search network tools
[http://www.google.ca/search?hl=en&q=linux+%22network+tools%22+%2B%28guide+%7C+tutorials%29&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+%22network+tools%22+%2B%28guide+%7C+tutorials%29&btnG=Search&meta=)
trails

---

### Post by bapoumba on 2007-09-23
Answers have been given. Please do not ask for help if doing illegal activities. Stealing someone network is not going to be supported on UF. Sorry, thread closed.

---

