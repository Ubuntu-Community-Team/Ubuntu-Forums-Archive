---
title: "Why does Postfix need to use an SMTP relay?"
date: 2021-05-04
forum: Networking &amp; Wireless
---

### Post by jcdenton1995 on 2021-05-04
Hello all, 

So I'm trying to get a new graphics card, and I'm looking to set up [inventory-hunter]("https://github.com/EricJMarti/inventory-hunter") so it can email me when a retailer gets stock. I've been learning about email, SMTP servers etc., but there is something fundamental that I can't wrap my head around.

The inventory-hunter script can send an email to a configured address, but the readme says that it requires an SMTP server to be running on the local machine, fine. The guide for configuring postfix for this purpose, that the readme references, details how to configure Googles SMTP servers as a relay host. What I don't understand is *why *a relay host is needed in this situation. Would it not be the case that without using the relay, the local instance of Postfix would contact the configured DNS and discover the IP address for the target domains MX server and then simply send the packet to that address?

Another question is why does the script need an SMTP server to run on the local machine anyway? If email clients can be configured to forward mail to a remote SMTP server then why can't whatever utility that the script uses to send the email *also *be configured to do so?

Any guidance would be much appreciated!


[B]Edit: I'm kind of getting the feeling that the answer is something to do with spam prevention and ISPs, I found the following quote on this [Wikipedia page]("https://en.wikipedia.org/wiki/Smart_host"), but it doesn't go into any more detail, I still don't understand...
[/B]
> When a host runs its own local mail server, a smart host is often used  to transmit all mail to other systems through a central mail server.  This is used to ease the management of a single mail server with  aliases, security, and Internet access rather than maintaining numerous  local mail servers.

---

### Post by rsteinmetz70112 on 2021-05-04
I don't know any reason postfix actually requires a relay but the google mail servers are pretty picky about what mail they will handle.

---

### Post by TheFu on 2021-05-04
> **jcdenton1995 said:**
> Hello all, 

So I'm trying to get a new graphics card, and I'm looking to set up [inventory-hunter]("https://github.com/EricJMarti/inventory-hunter") so it can email me when a retailer gets stock. I've been learning about email, SMTP servers etc., but there is something fundamental that I can't wrap my head around.

The inventory-hunter script can send an email to a configured address, but the readme says that it requires an SMTP server to be running on the local machine, fine. The guide for configuring postfix for this purpose, that the readme references, details how to configure Googles SMTP servers as a relay host. What I don't understand is *why *a relay host is needed in this situation. Would it not be the case that without using the relay, the local instance of Postfix would contact the configured DNS and discover the IP address for the target domains MX server and then simply send the packet to that address?

Another question is why does the script need an SMTP server to run on the local machine anyway? If email clients can be configured to forward mail to a remote SMTP server then why can't whatever utility that the script uses to send the email *also *be configured to do so?

Any guidance would be much appreciated!


[B]Edit: I'm kind of getting the feeling that the answer is something to do with spam prevention and ISPs, I found the following quote on this [Wikipedia page]("https://en.wikipedia.org/wiki/Smart_host"), but it doesn't go into any more detail, I still don't understand...
[/B]

In the beginning, MTAs would talk directory to each other.  People running MTAs were good, so there MTAs were configured to be nice and follow standards. Nobody got spam. SMTP is the protocol used by MTAs to talk server-to-server.  That and SMTPS (the TLS encrypted connection), but many MTAs aren't setup to use TLS - it is still optional.  Lots of email was exchanged by end-users on different systems and dog saw that it was good.

Then "bad people" got connected to the internet and decided to play jokes, crack into remote systems, and send spam emails to everyone on every server they knew.  For many years, each MTA (like postfix, sendmail, exim) would fight against these "bad people" on their own.  More and more people, often clueless, would get connected to the internet and want to send email.  ISPs all had DNS and email servers to make it so the clueless crowds would use the internet and email each other.  In the background, the spam was flying and bouncing.  The standard for SMTP is to try 4 delivery attempts over 4 days. This was because SMTP was designed to work with servers that would connect up 1-2 time a day to exchange SMTP and NNTP traffic.  Sending an email from Rural NY to rural Nepal might take 10 hops over 2-4 days.  It was pretty amazing compared to the 6 weeks sending a letter could take.  Lots of email was exchanged by end-users on different systems and dog saw that it was good, but there was more and more spam being transmitted, crufting up the exchanges. This was bad.

A few people decided to bypass the ISP email servers and wrote spam mailers that could send spam email to every IP address and the most popular email usernames automatically. A spam thrower was invented and the "good people" were unhappy. They wanted to make it harder for "bad people" abusing internet connectivity from spamming the world.  Dog thought this was terrible. It was basically an automatic phone dialer for spam phone calls, just for email instead.

In general, people running servers, large and small, are trying to be good people.  The same for ISPs.  When full-time connections became possible at home, we could have relatively cheap "servers" running on the end point of almost every ISP, each in a different apartment/flat/home.  Because these IPs were DHCP - they changed every 4 hours or each week. This meant that blocking the spam servers would incorrectly penalize the wrong person, since the IP would change for the "bad person". Dog thought this was terrible. 

The server people got together and decided that they would block email from DHCP addresses. This would make it just a little harder for spammers to abuse their home connections.  When this happened, lots of "good" home server people were harmed, but for the greater good, it was left that way.  That was around 1998. I know, because that's when my home email server started having email blocked.  At work, I was running email servers that weren't blocked - they all had static IPs on the internet. Professional servers would work as they always had because they were connected to static IPs.  Home servers, connected to DHCP addresses, wouldn't work, but spam from these home IPs would be stopped. Dog thought this was a reasonable compromise. 

So, DHCP subnets are blocked on the recipient side, but the spam is still being sent and every MTA/SMTP server has to constantly keep up with every-changing DHCP subnets. What a pain.  "Good people" decided to ask ISPs if they would block all outbound SMTP from end-user DHCP addresses to drastically reduce the amount of spam being bounced around on the internet.  It took about a year, but eventually, the larger ISPs agreed and blocked all outbound SMTP, except to the ISP email relayhost.  When this happened, spam dropped about 90% on the internet. It was amazing.  For non-Unix people, that relayhost was also the normal email server almost always. mail.{name-of-isp}.com would be the relayhost AND the email server for all outbound email (SMTP) from end users.  Inbound email from ISPs was almost always POP3 or POP3S ... this protocol pulls messages from the ISP server down to the client machine, deleting them from the server.  A newer email protocol for clients, IMAP/IMAPS was created for places that wanted email to be left on the server, searchable on the server, but available from every client a user might have.  Blocking end-users from sending SMTP directly to other servers on the internet was a good compromise. They could still send email, provided it went through the ISP's relayhost first.  Dog thought this was a reasonable compromise. 

Now the ISP is blocking direct SMTP outbound and forcing email sent to any outside email addresses go through their SMTP relayhost.  Spam is drastically reduced, because the ISPs have clear views into which clients are sending thousands of emails an hour or daily.  Most clients send less than 50 emails a day.  Only people abusing email are a problem and ISPs can disable their service without too much effort while leaving 99% of the customers alone.

Life is good except .... a new industry starts offering cheap servers for $5/month that almost anyone with a little technical skill can get.  This is the VPS industry and spammers love this.  They can use a server for a week, then move to a different server in about 5 minutes and start over.  Basically, they spam and spam, until their server IP ends up on a "block list".  There is an industry that has been updating and maintaining IP SMTP block lists for 25 yrs.  Initially, spam block lists were forever. Get on the list and you were on it for 2+ yrs. Getting off is nearly impossible.  I know. My email server IP got put on a block list by a huge regional ISP nearby. Nothing I did would get it removed. About 50% of my clients used that ISP, so not being able to send them email was a huge problem for my business.  However, no other email servers in the world had that IP on their block lists and the IP was not in any of the email block list services.  Every 6 months, I'd attempt to have my IP removed from the regional ISP block list.  Around 4 yrs later, they finally had a self-service webapp setup which could get specific IPs removed AND it actually worked.  By that point, I'd already closed the business for other reasons, but I was holding onto the domainname. Dog didn't care about my issue.  Bob on the other had was speaking to me and I liked what he was saying. ;)

So, the "good people" meet again to figure out a way to block these fly-by-night "bad people", but not make it so difficult that "good people" can't setup whatever is needed.  The outcome of this is SPF and DKIM.  But those are stories for another time, young Padawan. There are wikipedia articles about both, if you'd like to read ahead.  Let's just say that Bob saw both SPF and DKIM and thought both were good.

Hope this is helpful.  I didn't re-read what was written. It probably jumps around and might not make sense. Sorry for any typos.

---

### Post by jcdenton1995 on 2021-05-05
> **TheFu said:**
> Hope this is helpful.  I didn't re-read what was written. It probably jumps around and might not make sense. Sorry for any typos.

aha! Thanks, that was very informative. You've given some context to information I've read scattered across the internet, but with more grammatical flair! What I still don't understand is this: if ISPs compel their customers to send all mail through a common SMTP server, surely when I attempt to have the postfix instance running on my local machine relay mail through my webmail providers SMTP server (I'm not actually using gmail, that is just the provider used in the guide) then my ISP is going to block that?

Is it the case that some email providers allow SMTP clients to connect on non standard ports in order to bypass the ISPs restrictions?

I'm working through the postfix documentation as we speak, I know I'll get the system working, I just don't know why the guide linked in the readme for inventory-hunter uses the methods that it does :roll: saying that, the author obviously knows more than I. I don't like to rely on how-to's anyway, I find comprehensive documentation is a god-send. Funny how my heart used to sink when I saw the doc's for a program were an absolute tome, now I breathe a sigh of relief :D

---

### Post by jcdenton1995 on 2021-05-05
(deleted, duplicated below with quote)

---

### Post by jcdenton1995 on 2021-05-05
> **rsteinmetz70112 said:**
> I don't know any reason postfix actually  requires a relay but the google mail servers are pretty picky about  what mail they will handle.

Thanks, I'm not actually using gmail, but rather that was the email provider used in the guide that the inventory-hunter documentation provides. I think that it *might *be to do with the fact that in said guide, the author is setting up a system which sends an email to his gmail account when some event occurs. Presumably the gmail smtp server would recognise the email as being addressed to a user within a domain it was responsible for and happily pass that down. As opposed to if someone was just freeloading off of googles servers and relaying mail through them. Also the guide explains how to set up SASL to authenticate with the google server using a password that can be generated from within ones gmail account, so I *believe *that the server may handle messages sent from authenticated remote clients similarly to if it came from a local client, as obviously being authenticated implies one has a gmail account?

---

### Post by TheFu on 2021-05-05
> **jcdenton1995 said:**
> aha! Thanks, that was very informative. You've given some context to information I've read scattered across the internet, but with more grammatical flair! What I still don't understand is this: if ISPs compel their customers to send all mail through a common SMTP server, surely when I attempt to have the postfix instance running on my local machine relay mail through my webmail providers SMTP server (I'm not actually using gmail, that is just the provider used in the guide) then my ISP is going to block that?
Perhaps.

> **jcdenton1995 said:**
> Is it the case that some email providers allow SMTP clients to connect on non standard ports in order to bypass the ISPs restrictions?
SMTP traffic server-to-server is on port 25/tcp.
SMTP traffic client-to-server is on ports 465/tcp or 587/tcp. This usually requires authenticated connections, i.e. a username/password.
POP3 and IMAP are on different ports.  /etc/services lists them.

> **jcdenton1995 said:**
> I'm working through the postfix documentation as we speak, I know I'll get the system working, I just don't know why the guide linked in the readme for inventory-hunter uses the methods that it does :roll: saying that, the author obviously knows more than I. I don't like to rely on how-to's anyway, I find comprehensive documentation is a god-send. Funny how my heart used to sink when I saw the doc's for a program were an absolute tome, now I breathe a sigh of relief :D

On Unix systems, the local MTA is the expected way for email to be sent by systems.  Windows decided that normal standard wouldn't work, so the authenticated SMTP ports 465 and 587 were created by service providers, as a way to have traceable email initiation by paying clients that don't have to pass SPF or DKIM validations.

server-to-server SMTP uses the source IP in making decisions about whether to accept or reject the email traffic. Even with 7K firewall subnet rules to block spammers, about 1000 emails were rejected to my tiny, personal, domain, yesterday for failing standards.  To block spammers, a common technique is to always refuse the first "send" attempt and to force using the secondary mail server from DNS.  Spammers don't have time for that and often give up if the first attempt fails.

And whatever you do, don't have your email server setup as an **open relay**. That will get it banned very, very, quickly.  There are webapps online which will test this for you. Google finds them easily.  There are thousands of incorrectly configured MTAs on the internet. I think about 80% of all spam goes through those.

---

### Post by SeijiSensei on 2021-05-06
Postfix doesn't *need* a mail relay, but if it doesn't send its mail through a well-regulated relay, the mail is likely to be refused.

To avoid using a relay you would need, at a minimum, both forward and reverse DNS resolution set up for the machine running Postfix. You will also need a domain name with an associated SPF record that indicates the machine running Postfix is a valid sending server for the domain you choose. These days using DKIM to sign your mail is becoming de riguer as well, especially if you have recipients in some of the big domains like verizon.net or yahoo.com.  Easier to send your mail through a valid relay server.

If you intend to send the mail directly from your machine, please visit mxtoolbox.com to run its variety of security tests.

---

### Post by TheFu on 2021-05-06
If your server is on a DHCP range of IPs, then it will be blocked by almost all reputable email servers. You'll need to use the ISP-provided relay. The ISP will likely block all outbound port 25/tcp attempts.  

**Some other options to consider:**
If you don't want to use the ISP relay, you can pay $25/yr for some other SMTP relay service. I've seen those listen on 2525/tcp and other ports. There are terms and conditions for use which don't allow spam in those services.  The inbound service is separate from the outbound service, so don't expect to get both for $25/yr. They are separate.  Many people can use the free-tier from Amazon EC2 as their email gateway server and certainly a $5/month VPS can easily be an email gateway, among other things.

If your server has a static IP, then you'll need to get forward and reverse DNS lookups and MX and TXT SPF records setup for most of the world to accept  emails from your server.  If the assigned IP is in a spam-blocklist, it will probably be rejected. The easiest answer is to get a new subnet/IP that isn't on any blocklist.

My email server blocks all DHCP subnet SMTP connections.

---

### Post by jcdenton1995 on 2021-05-06
> **TheFu said:**
> If your server is on a DHCP range of IPs, then it will be blocked by almost all reputable email servers. You'll need to use the ISP-provided relay. The ISP will likely block all outbound port 25/tcp attempts.

Thanks, to be clear the only people who will receive mail routed through my server are my brother and I, furthermore I don't have any need to be able to receive inbound mail through the server (I have no public domain name anyway). It's literally just so MUAs on my desktop can send mail out to my webmail providers servers and have them plonk it in my inbox.

I've tried it out today and it successfully delivers mail to my own email providers SMTP server (which my server authenticates with) and can also deliver mail to my dad's gmail account using the aforementioned webmail server as a relay (or I guess it would be considered a smart host in this scenario?).

I took your advice and configure my server to only permit MUA's on the local machine to relay through it, as well as disallowing anonymous authentication from clients on other networks, furthermore I haven't added any authentication credentials for any remote clients so I think I'm good there.

The big 'if' is that I have to tether my PC to my phone to get a decent internet connection, so I'm not sure if I'll get the same results working off of the terrible broadband, I assume our router is given a dynamic IP address so that may be a problem (I don't know if 'mobile' 4G also gets me a dynamic IP, I don't know anything about that yet) but time will tell.

I *think *I will be okay, as, like you mentioned, my webmail's SMTP server listens on port 587 and I *do *authenticate with it, so my ISP may just let that sail through!

---

### Post by jcdenton1995 on 2021-05-06
> **SeijiSensei said:**
> Postfix doesn't *need* a mail relay, but if it doesn't send its mail through a well-regulated relay, the mail is likely to be refused.

To avoid using a relay you would need, at a minimum, both forward and reverse DNS resolution set up for the machine running Postfix. You will also need a domain name with an associated SPF record that indicates the machine running Postfix is a valid sending server for the domain you choose. These days using DKIM to sign your mail is becoming de riguer as well, especially if you have recipients in some of the big domains like verizon.net or yahoo.com.  Easier to send your mail through a valid relay server.

If you intend to send the mail directly from your machine, please visit mxtoolbox.com to run its variety of security tests.

Thanks, I don't think I need all of the provisions you mention, just because I'm only using it to forward mail onto my webmail providers SMTP server, it will basically work in one direction and never actually receive any replies (I don't even have a domain name). As I said in my reply to @TheFu above, my initial tests have been a success!

I will visit mxtoolbox and see what tests they offer though, I did read the Postfix SASL documentation carefully and configure it to basically be a selfish server that only serves local email clients (as in very local, as in just my little desktop). My main concern was that I would get the home IP address on some sort of spam blocker list :shock: I think I've covered all of the important bases though.

---

### Post by TheFu on 2021-05-06
> **jcdenton1995 said:**
> I *think *I will be okay, as, like you mentioned, my webmail's SMTP server listens on port 587 and I *do *authenticate with it, so my ISP may just let that sail through!

587 is for client -to- server SMTP transmissions. No ISP should be blocking that.  Thunderbird and MS-Outlook and probably every other thick email client support that port for sending authenticated email.  DHCP doesn't matter.  It only matters when we are trying to send server-to-server emails without credentials.

---

