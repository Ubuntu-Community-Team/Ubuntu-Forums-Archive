---
title: "confusing nameserver - resolv.conf conventions"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-17
regarding dns... and the resolv.conf - the set up always puzzles me.

lets say I register my site 'my-domain.com' with netsol.com, 

then, I sign up with another provider called 'dnsprovider.com' for dns server for my site 'my-domain.com', 

and another provider to host my site, which is a virtual private server company.  Lets call this company 'vpshosting.com'

Lets say virtual private server company insists that I use their dns.  However, I believe the dnsprovider.com would be better, due to many switches and hubs.  And the dns company has a better infrastructure, and awesome dns provisioning.  

I simply went to netsol.com, which is the domain registration holder, and put dnsprovider.com's nameservers. 

Then, on my virtual private server, I put their vpshosting domain, search conventions.  And then, for nameserver's I put dnsprovider nameserver IPs........
> 
/etc/resolv.conf
domain members.vpshosting.com
search members.vpshosting.com
nameserver 4.4.4.1
nameserver 4.4.4.2
nameserver 4.4.4.3
nameserver 4.4.4.4
options rotate


How would you go about it?  What are the pros and cons of this set up?

---

### Post by scorp123 on 2011-08-17
For starters: You can't use more than **3 x** nameservers in **/etc/resolv.conf** .... It's a fact. You can look it up in the manual. Command: ```
man resolv.conf
``` ... The manual will also explain the possible configuration options and their syntax.

---

### Post by ofnuts on 2011-08-17
> **007casper said:**
> regarding dns... and the resolv.conf - the set up always puzzles me.

lets say I register my site 'my-domain.com' with netsol.com, 

then, I sign up with another provider called 'dnsprovider.com' for dns server for my site 'my-domain.com', 

and another provider to host my site, which is a virtual private server company.  Lets call this company 'vpshosting.com'

Lets say virtual private server company insists that I use their dns.  However, I believe the dnsprovider.com would be better, due to many switches and hubs.  And the dns company has a better infrastructure, and awesome dns provisioning.  

I simply went to netsol.com, which is the domain registration holder, and put dnsprovider.com's nameservers. 

Then, on my virtual private server, I put their vpshosting domain, search conventions.  And then, for nameserver's I put dnsprovider nameserver IPs........



How would you go about it?  What are the pros and cons of this set up?

All this looks fairly academic... a given name should resolve to the right addresses whatever the DNS you use (given some time fro propagation)(and let's forget the VPN issues for a while). The "registration" of an internet name/address makes it available from all DNS worldwide (otherwise your expected visitors wouldn't find you).

Or am I missing something?

---

### Post by scorp123 on 2011-08-17
> **ofnuts said:**
>  Or am I missing something? Nope, you're right. If the DNS entry is made correctly then the host should be resolvable no matter which DNS server is used. @OP: you can use Google's public DNS server if you want to. It's IP is --no kidding!!-- **8.8.8.8**  ... 
```

> nslookup 8.8.8.8
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
**8.8.8.8**.in-addr.arpa	name = **google-public-dns-a.google.com**.
```

---

### Post by 007casper on 2011-08-17
@ scorp123 - I looked at the manual.  It does state currently 3 nameservers may be listed.

Then, what happens to additional nameservers.  If the dns provider has five, the other two doesnt see the light.  Why would they have it? ns4, and ns5 - Are they just failover?

I totally agree.  It shouldnt have a problem.  However, this is not the first time a host provider insisted that I use their DNS vs. outside DNS.  

Why would they insist on this?  They act like it wont work, thats more puzzling.

---

### Post by pi.boy.travis on 2011-08-17
The other servers are probably for fault tolerance. I use Google's DNS, never failed yet.

---

### Post by scorp123 on 2011-08-18
> **007casper said:**
>  this is not the first time a host provider insisted that I use their DNS vs. outside DNS.  

Why would they insist on this? To avoid unfounded complaints maybe?

What I mean is this: Let's suppose you configure a new hostname but you use someone else's DNS server. The update of the DNS tables all around the globe might take a few hours (this is assuming that the more professionally configured DNS servers will do some sort of caching instead of constantly bombarding other servers with their requests). No problem if you're aware of this. So you check on your new hostname ... it doesn't work ... OK, the update hasn't reached all servers around the globe yet. Let's try again tomorrow....

But other users who might not know this might then get the impression that it isn't working (because the update hasn't yet reached every DNS server on this planet and some caches still have the old entries) and they may open support tickets, file complaints, threaten them with lawsuits and what not .... So because it's rather boring to explain again and again *"Please use our own server when you check your new hostname ... other servers might not have received the DNS update yet ..." * they simply say *"You must use our DNS servers. End of discussion."*

I've had similar (tiring!) discussions with some of my own customers and whenever one of them complains about one of their hosts not being up it's usually because they use someone else's DNS server ... so I can totally understand why your provider might insist on this clause.

---

### Post by 007casper on 2011-08-18
thank you.  

It is strange, if I use dnsprovider's nameserver on resolv.conf, it doesnt work.  I cant even apt-get update on the server. If I use theirs it works.

---

### Post by ofnuts on 2011-08-18
> **scorp123 said:**
> To avoid unfounded complaints maybe?

What I mean is this: Let's suppose you configure a new hostname but you use someone else's DNS server. The update of the DNS tables all around the globe might take a few hours (this is assuming that the more professionally configured DNS servers will do some sort of caching instead of constantly bombarding other servers with their requests). No problem if you're aware of this. So you check on your new hostname ... it doesn't work ... OK, the update hasn't reached all servers around the globe yet. Let's try again tomorrow....

But other users who might not know this might then get the impression that it isn't working (because the update hasn't yet reached every DNS server on this planet and some caches still have the old entries) and they may open support tickets, file complaints, threaten them with lawsuits and what not .... So because it's rather boring to explain again and again *"Please use our own server when you check your new hostname ... other servers might not have received the DNS update yet ..." * they simply say *"You must use our DNS servers. End of discussion."*

I've had similar (tiring!) discussions with some of my own customers and whenever one of them complains about one of their hosts not being up it's usually because they use someone else's DNS server ... so I can totally understand why your provider might insist on this clause.
OTOH if you use a name in a DNS it because you want the whole planet to find you, and you  can't really control which DNS they use.

---

### Post by scorp123 on 2011-08-19
> **ofnuts said:**
> OTOH you  can't really control which DNS they use. That's not the point. From a technical POV don't care which DNS server they use -- and you are right: It should not matter. What I do care about is unfounded accusations, unnecessary support tickets and threats with lawsuits. Discussions like *"... but my server is still not reachable!! You promised it will be configured by 12 o'clock!! Aaaarrrggghhhhh ... I am going to sue you... !!"* -- and all this because some customer does not really understand how DNS works and that he's probably using a server that has not received an update yet.

So the reason why hosters might insist you use their DNS server has nothing to do with how the technology works (yes, it should work at some point no matter whose DNS server you use!) but it's more of a legal technicality: if you can reach your web site on my server using my DNS then it means I've fulfilled my end of the deal and you have no grounds to sue me and we don't need to spend hours on the phone together on why the web site supposedly isn't reachable ...

See what I mean?

Yeah, later on when the site is up and running day in and day out and reachable world-wide ... it should not matter. DNS is DNS, and each DNS server should be able to correctly resolve stuff.

---

### Post by 007casper on 2011-08-19
you know I agree with both of you.  

you use DNS so the world finds you.
 
I also came across a few people that complained why their site didn't work.  And, if you tell them it is because of DNS.  They get upset.  And treat the situation as you know the problem, and not fixing it.

If you try to explain to them, how it works.  They still think you are not fixing the DNS situation. Sometimes, they really get confused when they find out they cant really find someone to fix the situation.

However, I started to get confuse myself, when I came across an hosting company insisting that I only use their DNS. :)

I said - ah it is okay.  They were so firm about it, that I wondered what the big deal was...

And recently, when I came across another hosting company that has nothing to do with the first one, reacted like end of the world if I use another DNS provider. I was surprised.  I just didn't get it.  And, wondered what is the deal?  I can really see the DNS provider had more connection than the hosting company.  I figured more connection, the better it is...

So, you got the caches, and old entries.  Everyone knows that.... 

Still, something puzzled me this time.  

So, I put the dnsproviders nameservers on the registering company.  

Then, I inserted all the proper information on the dnsprovider regarding my ip, hostname, A record, CNAME etc.  I waited over 72 hours.  It wont load.  And sometimes it would.  Then, after 72 hours it wont load at all.  

So, I just got this gut feeling.  On registering companies panel, besides dnsprovider's nameservers I also added A record for the server IP.  Split second everything worked.  I was surprised.  Nameservers hicks up, and if you enter A record in addition to the nameservers on the site registering company it resolves immediately.

Then, I tried this on the same domain, with different subdomains.  One with dnsprovider's nameservers, then the other with hosting companies nameservers providers.  If you put A record on the registrar servers, it resolves fast.  Usually under five minutes.  

Then, on both servers, I switched to hosting companies dns servers, and deleted the dnsprovider's nameservers all together on the servers.  Remember, I still have the A record, the server IP, and nameservers of the dnsprovider on the site registrar's panel. It worked without a flaw.  Not much of a surprise there.  It is reading the A record.

I decided to check thednsrepot.com, same set up on two different servers.  Both subdomains have dnsprovider's nameservers, and A record for the server.  I totally get more errors on one, compare to the other.  This is really weird. :shock:

Then, I wanted to try one more thing.  If I use hosting companies dns servers, I get connection right away to update the server.  If I use dnsprovider's namservers, I cant get update.  I thought this is strange.  The server is connected to online, and doesn't need nameservers to pull information from outside.  Am I wrong? 8-[

---

### Post by ofnuts on 2011-08-19
> **scorp123 said:**
> 
So the reason why hosters might insist you use their DNS server has nothing to do with how the technology works (yes, it should work at some point no matter whose DNS server you use!) but it's more of a legal technicality: if you can reach your web site on my server using my DNS then it means I've fulfilled my end of the deal and you have no grounds to sue me and we don't need to spend hours on the phone together on why the web site supposedly isn't reachable ...
Yes, but doing so, they say: "Mr Customer, your site is only available to the happy few who use our DNS". So you can open a dodgy registration company, and happily add away whatever names your customers want to your little DNS in your corner of the net. You will have fulfilled your side of the contract. "microsoft.com" is available on my DNS, wanna make an offer?

---

### Post by 007casper on 2011-08-19
> Yes, but doing so, they say: "Mr Customer, your site is only available to the happy few who use our DNS". So you can open a dodgy registration company, and happily add away whatever names your customers want to your little DNS in your corner of the net. You will have fulfilled your side of the contract. "microsoft.com" is available on my DNS, wanna make an offer?

I am not sure what you mean... so, hosting company figures the customer isnt going to know any better, and make statements like 'only if you use our DNS, it will work.  Otherwise, all else fails.' and you figure before you know it, someone is going to make an offer on the hosting company since their DNS works?

---

### Post by scorp123 on 2011-08-21
> **ofnuts said:**
> Yes, but doing so, they say: "Mr Customer, your site is only available to the happy few who use our DNS".  Nope, that's not what I said.

It's not *"only available to the happy few who use our DNS"* ... If anything then the message should say: ***"Before you open idiotic tickets about non-issues and before you threaten to sue us, would you please check your site using our DNS servers? Thank you."***

And that makes sense because as DNS and/or hosting provider you have no control over other people's DNS servers. The only thing you control is your own stuff. Hence why your customers should check with your servers first before they file a complaint. Everything else is just a matter of DNS updates getting through or not.


> **ofnuts said:**
>  
So you can open a dodgy registration company, and happily add away whatever names your customers want to your little DNS in your corner of the net. You will have fulfilled your side of the contract. "microsoft.com" is available on my DNS, wanna make an offer? That's NOT what I meant, NOT what I said, and NOT how it works. What you are writing up there is bad science-fiction. If it were so easy and possible like that then people would do it all the time. But they don't: Inserting fake DNS updates into the Internet will sooner or later throw an error, e.g. with your provider, and then someone will take a look into those logs and then discover what you are doing. **It's a guaranteed way to get the attention of Microsoft's legal department.**

And if you read the fineprint in your contract it will surely say something about illegal and disruptive activities ... BAAAAM!! your own provider disconnects you from the Internet. And that would be the end of your dodgy activities.

Again: this is NOT what I meant.

---

