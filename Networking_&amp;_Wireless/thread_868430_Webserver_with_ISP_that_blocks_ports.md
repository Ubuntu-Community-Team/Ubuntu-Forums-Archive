---
title: "Webserver with ISP that blocks ports?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2008-07-23
I would like to run a server at home.  I have a fast residential package that has 15mbps (35 burstable) and 764Kbps upstream.  I have a web hosting service that runs Linux.  It  currently hosts 15 domains of mine that receive very little traffic.  They are basically parked there waiting to be sold.  One or two might get a small amount of traffic. 


I'm guessing my ISP blocks port 80, 25, 110 and other “server/services” ports.  So what I was thinking was setting up those services on alternate unused ports.  Then I would have the incoming traffic directed to the standard ports on my linux web hosting service and it would forward them to the non-standard ports on my local machine.   So web traffic could be sent to my webserver and it it is destined for a domain that is hosted at my home box, it is forwarded to a different port.  Is this possible?  If not what would be an alternative solution (other than paying 3 times more and get ½ the speed for a business line?).

I dont' want to run this very long, maybe a couple months.  Basically I just want the experience setting this up and configuring it.  Once it is working the way I want it, I'll then buck up and buy the business cable connection.  

Can someone please help me out?

Thanks.

---

### Post by AVT- on 2008-07-23
Are you sure your ISP blocks those ports? As far as I'm concerned, with most ISP's, the difference between residential and business lines is whether you have a static IP or not.

If that's the main problem, you could theoretically work around it by storing your home server's current ip at the second server, updating it any time it changes, and having it redirect to the home server's ip.

---

### Post by Njem on 2008-07-24
Yes, some ISPs block at least port 25 so they don't have client systems flooding spam thru them. But in that case you can certainly ask what they block and in some cases they will unblock on request. Or they may want to sell you a better package.

---

### Post by superprash2003 on 2008-07-24
well if port 80 is blocked then people trying to connect would have to do [http://domainname.com:xx](http://domainname.com:xx) where xx is the alternative port no.. that is possible.. another way to do this is through no ip which allows you to forward domainname.com to domainname.com:80

---

