---
title: "Send message to ip address?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-01-03
i see on my firewall that i am being hit by various overseas computers. i read on another thread that the good thing to do would be send a message to them to inform them that their computer is probably infected. how can i do this safely? thanks for all help.

---

### Post by scorp123 on 2009-01-03
> **mjheagle8 said:**
> that the good thing to do would be send a message to them to inform them that their computer is probably infected. You completely misunderstood that.

"sending a message" here means: You find out who their Internet Service Provider is and you notify that ISP that they have infected computers in their network.

So now your next question most likely will be: 
[INDENT]"How in the world am I supposed to know who their ISP is???"[/INDENT]

There is a program called "**whois**" which does precisely that.

Let's suppose you were attacked by this IP address: "**192.123.123.34**" ... so if we feed that to "whois" it will tell us who the ISP of that IP is: 
```
 > whois 192.123.123.34

OrgName:    Kraft General Foods, Inc. 
OrgID:      KGF
Address:    Information Technology Systems
Address:    Kraft Ct.
City:       Glenview
StateProv:  IL
PostalCode: 60025
Country:    US

NetRange:   192.123.0.0 - 192.123.255.255 
CIDR:       192.123.0.0/16 
NetName:    KGF-CNETS
NetHandle:  NET-192-123-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    Direct Assignment
Comment:    
RegDate:    1991-08-14
Updated:    2004-06-04

OrgTechHandle: SMA53-ARIN
OrgTechName:   Mavraganes, Sam 
OrgTechPhone:  +1-847-646-2141
OrgTechEmail:  sam.mavraganes@altria.com

# ARIN WHOIS database, last updated 2009-01-02 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database
```

Bingo! That IP address would belong to **KRAFT Corporation** ... And "whois" also spits out whom you are supposed to contact (see above! It's all there!!).

So in this example if you had been attacked by the IP in my example above you'd now give Mr. Sam Mavraganes up there a phone call or send him an e-mail with your logs attached so he could take care of the problem on his end.

That's how you are supposed to do it.

BUT:  Please be aware that some ISP's in South East Asia (e.g. China, India, Korea) don't really care one little bit. You can send them e-mails as much as you want, they will not react or even acknowledge that they received a mail from you. And please be aware that they might sell your contact details to spammers ... it wouldn't surprise me if the number of spam mails increased drastically after you sent them an e-mail .... 

So keep your expectations on a realistic level please. Some ISP's are nice and will react, some have competent people and they will even do something about your complaint .... and others won't care at all.

---

