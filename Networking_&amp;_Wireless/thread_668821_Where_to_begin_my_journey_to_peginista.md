---
title: "Where to begin my journey to peginista?"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by bacoxswain on 2008-01-15
Alright ... after considering the only viable and known option of port fowarding to get access to my internal network I have decided to switch from a consumer set-up to a pro-sumer set-up.  In that, I mean I want my Ubuntu 7.10 box to be my router, my DNS, my DHCP server, my mail server, my gateway; in short, I want it to do everything and be the only box between my switch and the internet.  The only problem is, I have absolutly no idea how to do  what I want to do.  Here is what I want.

1) to be able to reach my webpage using the address [www.mydomain.com](www.mydomain.com)

2) be able to reach all servers on my home network via a fully qualified address such as server.mydomain.com from the internet (ie not on my local network)

3) be able to reach my a particular range of ports a particular server via a fully qualified address such as voip.mydomain.com from anywhere with an internet connection (ie not on my local network)

4) serve my own email using POP3 and IMAP from a mail server located on my network

5) access my email on my email server from anywhere using either a web interface or other POP3 Client from anywhere with an internet connection (ie not on my local network)

I'm looking for how toos for the ultra newbie here.  My significant other has stated his desire for this and plus, I think it's just kinda cool.

Thanks in advance for the help.
-Chris

---

### Post by sqrt2 on 2008-01-15
It is very unwise in terms of security to have everything running on one machine, especially because you don't seem to have deep insight into how the Internet works and how the protocols you want to service work, i.e. how attacks on them would look like. (I'm deriving that from you describing yourself to be a newbie.)

With you providing services to the public and also having a private network that you most likely want to protect from the outside, you will need a firewall (i.e. the corresponding *security concept*; a piece of software or hardware won't do it, regardless of what marketing divisions of "firewall" vendors may tell you). It would be a reasonable approach to separate your network into two parts, a so-called Demilitarized Zone (DMZ) and a protected, internal network.

In short, simple recipes on how to set up each of the services won't do it. You really have to get to the bottom of things to prevent having your mail server to be turned into a spam relay (I've seen that happen in no time), your network having to suffer from Denial of Service attacks etc. pp.

---

