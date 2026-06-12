---
title: "I can only access Internal server but cant access from Outside"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by kustomjs on 2007-11-15
Hi Guys
can anybody tell me the reason why I only can access my server from inside meaning (internal) but cant access it from outside source?

---

### Post by stevux on 2007-11-15
wow. now i know what 'the default techsupport guy' gets to digest.. :)

let's start at the start;
[INDENT]  what is your network topology? (internal IPs, router, external IPs, NAT, DHCP, etc etc)
  what is 'access'? (http/ssh/telnet/mail/ping/...)
  what have you tried to get access?
  what were your own conclusions?[/INDENT]

i'm sorry to be asking all these questions (specially since you should have provided this info in the start of the thread) but this is needed for; a) anyone to reply to the thread, besides fools like me, b) get a slight notion of the problem and c) learn you you should provide ample info when asking a question.

don't worry! we'll get there!

thx,

---

### Post by kustomjs on 2007-11-15
I have a static IP address from ISP and I am behind a router and each computer have a static ip address and I can ping both computers and i can also ping the router.

---

### Post by kustomjs on 2007-11-15
~bump~

---

### Post by jetsam on 2007-11-15
If you're behind a router, you generally need to set up [port forwarding]("http://en.wikipedia.org/wiki/Port_forwarding") on the router to have it direct traffic from the net to one of your internal machines.  Most routers come set by default to drop all inbound traffic.  This is good for security, but it means you need to configure the router if you want to publish a service and make it available on the net.  

Your router documentation should have instructions on how to configure it.  On mine, there's a browser based administration utility that I connect to internally and then configure Security-->Rules.  The interface will be different for different brands of router, though,

---

### Post by kustomjs on 2007-11-15
I am behind linksys router WRT54-G V5

---

### Post by jetsam on 2007-11-15
The documentation is available from Linksys [[COLOR="Blue"]_here_[/COLOR].]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859837401&packedargs=sku%3DWRT54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3740137401B01&displaypage=download#versiondetail")

Select version five in the menu on that page and then download the .pdf user's manual.  

I just scanned it briefly, and the router is firewalled by default.  Look at page 15 under 'Applications and Gaming>Port Range Forward.'  That should get you going.

Do be aware of security, though.  Publishing stuff on the net opens your computer to security vulnerabilities.  In general, only open ports that you really need to be available, use strong passwords, and be sure that the services you're running are adequately secured.

---

### Post by kustomjs on 2007-11-15
would it be also when i installed webmin that default firewall is rejecting any outside internet connection?

---

### Post by kustomjs on 2007-11-15
well I finally got to access to my server to my xp machine but now i only i can get 192.168.1.3 to work not my real ip address to work at all because at one time i had 206.51.165.1x to work but now it doenst.

---

### Post by jetsam on 2007-11-15
I'm not sure about that.  I don't know much about webmin, sorry.  

One possible source of trouble here is that your public router ip address will be different than your internal network ip address.  The simplest way to check your public address is probably a website like [http://whatismyipaddress.com/]("http://whatismyipaddress.com/").  It will show your public address at the top of the page.  

Firewalls and host rules on the server can also block traffic...  it all gets complicated.  You may need to find someone on the forum who's better at diagnostics.  :confused:

---

### Post by theDaveTheRave on 2007-11-25
Hi.

I'm setting up a similar facility at the moment, mainly for access to public files (eg host my own web pages).

But to do this I obviously needed to set up a server etc.

Security is a big thing, I set up an OpenSSH system between the server and my laptop, for access to root on the server.

Currently I haven't completed the procedure but a quick overview of what I believe is possible is:

You only really want to access root serverices on a terminal when you are "sat in front of it" to this end I have been able to confirm that if I want to play as root I can only gain access via the main network port - allways connecting via a short bit of network cable. Otherwise the remaining access is done via the wirless access port - still using SSH to my "personal" user area - whcih comes up on my machines as either ath0 or wlan0 (this depends on the machine acting as server / host.

I obviously also want access from any terminal on the interet - so I have simply given myself a "chocked" down minimal permisions area that I will log into from the net. I haven't decided on the best way to get this to work yet, maybe by by having a USB key with a pasword generator applet on it that will generate new password for when I want to log in?? or maybe by a "swipe" card type access??

My concern now is to be able to proove in my mind that my personal area access is secure etc, but I haven't as yet found out how to... which is actually why I am here today!

Oh well back off on my search

Dave

---

### Post by kustomjs on 2007-12-19
I thought I had it fixed but I dont I reinstalled everything and now I am behind linux router (smoothwall) I can access the webmin internal but I cant get it on my xp machine at all.

---

