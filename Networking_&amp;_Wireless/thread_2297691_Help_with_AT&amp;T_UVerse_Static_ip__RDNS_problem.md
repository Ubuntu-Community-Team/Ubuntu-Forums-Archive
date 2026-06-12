---
title: "Help with AT&amp;T UVerse Static ip / RDNS problem"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by Robert_Boutin on 2015-10-06
Hello everyone, looking for some expertise as mine is extremely limited.

I  have an email server in my basement running Ubuntu 12.04.  I had a  static ip with WOW which, except for the frequent internet outages,  seemed to work well.

I made a regrettable decision to switch from  WOW to UVerse and I can't switch back as WOW no longer offers a static  ip.  Please bear with me, I'm no networking specialist so I'll probably  misspeak on some of this.  But I really need some help, so here goes...

I  received a static ip address from AT&T, I'll call it ip address X.   AT&T is not able to set up RDNS for X so that X resolves to my  domain name.  X is only permitted to resolve to X.lightspeed.livnmi.sbcglobal.net,  AT&T can't or won't change the DNS to resolve to my domain.  When I  send an e-mail to a gmail account, it gets bounced because of RDNS  failure (the header says sent from ip address X which resolves to  sbcglobal and not my domain), verified by performing an email  deliverability test at mxtoolbox.com.  However, I also received a block  of 8 static ip addresses of which 5 are usable.  The way I understand it  is that X is my public ip for my gateway and the other five addresses  (including Y) can be assigned to devices inside my network, such as my  email server.  AT&T customer support set up one of these address  (we'll call it Y) so that Y properly resolves to my domain (verified at  mxtoolbox.com). 

What I want to do is assign static ip address Y  to my email server such that emails sent from my server show as coming  from ip address Y instead of ip address X.  This would resolve my RDNS  failures (I think).

I am sending emails via port 25 because I  don't wish to use AT&T servers to relay email.  I know that's an  easy solution but for certain reasons, I need to be able to log the  actual handoff of e-mail between my sending server and the recipient's  server.

I can't figure out if this is set up through the gateway  settings or through Ubuntu, or both. In the gateway I tried "IP  Allocations" to assign static address Y to my server, but that seemed to  do nothing.

Does anyone have experience with AT&T UVerse and  this kind of problem?  Thanks for your assistance, and for not laughing  at my inexperience.

---

### Post by SeijiSensei on 2015-10-06
Do you have a router to which address X is assigned?  Is it the type of router typically used in home networking with a single connection that points to the Internet (typically labelled the "WAN" connection), and other Ethernet ports designated for the local network ("LAN" connections).  Can you configure the router to use address Y as its public address instead of address X? If so, the easiest solution is to connect the server to the "LAN" side of the router, then go into the router's configuration and set up "port forwarding" for port 25.  Tell the router to pass its port 25 back to port 25 on the server.  

However AT&T may have provided you with a different type of router that is designed to handle a network subnet rather than just a single address.  If so, how many ports does this router have?  One to connect upstream and another to which address X is assigned?  If so, the solution might be to buy a [cheap network switch](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704179) and connect both the router and the server to it, then assign the router address Y with X specified as its "gateway" address.  AT&T should be able to help you determine what kind of router you have.

If you're asking about how to assign a static IP to the server, read [https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing).

---

### Post by Robert_Boutin on 2015-10-06
Thanks, I will look at this tonight after I get home.  I know some of what you asked, but not all without having the equipment in front of me.  I'd rather provide the information in a single post.  Thanks for responding, I'm hopeful now this won't be a huge ordeal.

---

### Post by oldos2er on 2015-10-06
Moved to Networking & Wireless.

---

### Post by Robert_Boutin on 2015-10-09
Sorry for the delay.  Apparently I'm not the only one with this problem but the AT&T forum still doesn't provide a definitive solution.

So here is where I stand currently.  My Uverse gateway is a Motorola NVG589 with four ports.  I went out and bought a Netgear GS605 5 port gigabyte unmanaged switch.  I also have a Netgear WNR2000 wireless router that was decommissioned when AT&T installed the NVG589.

The way I understand it is a switch will extend the existing network while a router will connect two networks.  If this is correct, I'm not sure how the switch benefits me since I have an open port remaining on the NVG589 that I could just plug my mail server into.  I also understand that a switch is not assigned an ip address while a router does get an ip address.

So I guess I need to ask this question before I go farther.  When I send an e-mail from my server, how is the sending ip address attached to the message header?  Right now everything leaves with ZZ.Z.121.184 (ip address X in my original post).  But I need my static ip address NNN.N.236.17 from my block of 5 usable to be on the header instead.  Maybe knowing how the ip address gets attached to the message might help point me in the right direction.

Thanks

---

### Post by Robert_Boutin on 2015-10-18
Problem solved.  After 3 hours with AT&T's ConnecTech service, it  was determined that the NVG589 gateway does not have the functionality  required to permit email messages to be sent with the originating static  ip intact.  The tech stated I needed a two-wire gateway.



After  calling AT&T customer service and explaining the situation,the  service guy came to the house and installed their newest gateway, a Pace  5268AC.  Apparently my home has a bonded pair coming into it because of  distance and bandwidth requirements.  This meant the couldn't use the  two-wire gateway the tech was referring to.  So the 5268AC was my only  option.



After three more hours with ConnecTech to set it up, it now works properly.



So  just to recap, I have an Ubuntu mail/web server plugged directly into  the AT&T gateway (no separate router).  I purchased a block of 8  static ip addresses (5 usable).  My messages to Gmail accounts were  getting bounced as spam because of rDNS failure.  I went here first to  set up rDNS for one of my static ip address, it took about a day:



[https://www.att.com/gen/general?pid=17307&cdvn=formbuilder&formName=ATT_DSL_Uverse_DNS_Request_Form_1600](https://www.att.com/gen/general?pid=17307&cdvn=formbuilder&formName=ATT_DSL_Uverse_DNS_Request_Form_1600)


However,  my emails would not pass through the gateway without the dynamic ip address of the  gateway being inserted as the originating ip.  By replacing the Arris NVG589 gateway with the Pace 5268AC  gateway, my emails now pass through the gateway intact and arrive at  their destination with the static originating ip intact.

---

### Post by SeijiSensei on 2015-10-19
I hate stories like this one.  You have invested hours to resolve a problem having to do with the provider's hardware.  And we have spent our time trying to resolve a problem that is beyond our control.  I'm just so glad you got everything worked out.

I long ago abandoned trying to manage servers on a connection to my home.  I had a business account from Verizon FiOS that worked flawlessly, but was over $100/month.  Then there's the problem of keeping the hardware up and running and sufficiently backed up in case disaster strikes. I've since moved all my public services to servers at [Linode]("http://www.linode.com/").  For $10-20 month I get enormous bandwidth, daily snapshot backups, and no hardware to maintain.  If the time comes when you need to change providers, I suggest giving them a try.

---

### Post by Robert_Boutin on 2015-10-19
Thanks, I will keep them in mind. I built my own server because I was with Network Solutions on a shared server that was blacklisted and they refused to move me to another server.

I understand this wasn't a case with an Ubuntu solution. I just wanted to close the loop and save somebody else from my pain. I figure I can't be the only person running a server behind U-verse. I don't have the knowledge to be a contributor here but hopefully this will help someone.

---

### Post by Sam_Trevino on 2015-12-18
> **Robert_Boutin said:**
> Problem solved.  After 3 hours with AT&T's ConnecTech service, it  was determined that the NVG589 gateway does not have the functionality  required to permit email messages to be sent with the originating static  ip intact.  The tech stated I needed a two-wire gateway.



After  calling AT&T customer service and explaining the situation,the  service guy came to the house and installed their newest gateway, a Pace  5268AC.  Apparently my home has a bonded pair coming into it because of  distance and bandwidth requirements.  This meant the couldn't use the  two-wire gateway the tech was referring to.  So the 5268AC was my only  option.



After three more hours with ConnecTech to set it up, it now works properly.



So  just to recap, I have an Ubuntu mail/web server plugged directly into  the AT&T gateway (no separate router).  I purchased a block of 8  static ip addresses (5 usable).  My messages to Gmail accounts were  getting bounced as spam because of rDNS failure.  I went here first to  set up rDNS for one of my static ip address, it took about a day:



[https://www.att.com/gen/general?pid=17307&cdvn=formbuilder&formName=ATT_DSL_Uverse_DNS_Request_Form_1600](https://www.att.com/gen/general?pid=17307&cdvn=formbuilder&formName=ATT_DSL_Uverse_DNS_Request_Form_1600)


However,  my emails would not pass through the gateway without the dynamic ip address of the  gateway being inserted as the originating ip.  By replacing the Arris NVG589 gateway with the Pace 5268AC  gateway, my emails now pass through the gateway intact and arrive at  their destination with the static originating ip intact.

Hello Robert (or anyone else),

I've been having issues with this same device (Pace 5268 AC Residential Gateway). It took me forever to get my Samsung MyCloud to finally work on this device (5268 AC RG). From what I understand it's in a DMZ, which does impact the MyCloud's full functionality. Seriously at this point I'm considering dropping AT&T and going with Time Warner just for ease of use with hardware.   

I'm not sure if it allows for port forwarding on this device (I can't figure it out). I wanted to host a simple WordPress blog and redirect a domain I own (at Godaddy) to it. Is there a way for port forwarding or do I have to purchase Static IP Addresses, or do something else? 

Thanks,

Sam Trevino

---

