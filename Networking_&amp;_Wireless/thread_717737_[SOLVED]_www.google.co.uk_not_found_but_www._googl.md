---
title: "[SOLVED] www.google.co.uk not found but www. google.co.uk OK"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by JonAxtell on 2008-03-07
I've just installed Ubuntu 7.10 and I'm having problems accessing [www.google.co.uk](www.google.co.uk). When I enter the URL Firefox times out. Trying to ping it also times out. However I can access [http://www.google.com/webhp?hl=en](http://www.google.com/webhp?hl=en) and can ping [www.google.com](www.google.com). I can't access [www.google.com](www.google.com) because it redirects to [www.google.co.uk](www.google.co.uk). I know it's not my router because if I reboot and switch to Windows I can access  it with no problem. It's not just [www.google.co.uk](www.google.co.uk), some sites take ages to load because of embedded images from affected domains.

I've disabled AdBlocker, cleared cache and cookies, still no joy. My ISP is Tiscali.

Any clues where I need to look to resolve this?

---

### Post by {BzF}~JOKesTER on 2008-03-07
I Don't Know About The [www.google.co.uk](www.google.co.uk) Thing As I Don't Live In The UK...

I Do Know That This Fix Speeds Up Firefox Tremendously!!!!!!


[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)


Hope This Helps!!!:)

---

### Post by JonAxtell on 2008-03-08
Nope, not related to IPV6/V4. Disabled IPV6 via the System->Adminstration->Network method and also in Firefox via about:config. Couldn't use the other methods (aliases or blacklist) because I couldn't save the file as it was in use. Still no joy.

Confusing thing is seems to be random which websites aren't accessible, but no matter how many re-boots it's always the same websites, eg.. [www.google.co.uk](www.google.co.uk), earth.google.com.

---

### Post by {BzF}~JOKesTER on 2008-03-08
In Order To Use The Aliases Or Blacklists You Learned About You Must Use:

sudo gedit /folder/textdocument

{Obviously Replace The "Folder" And "Text Document" With There Real Names

Hope This Helps!!!

---

### Post by JonAxtell on 2008-03-09
Changed the alias and added a blacklist for IPv6. As I said, I don't think it's IPV6 related as I can access some sites, but not others. I haven't gone through an exhaustive list but it seems to be related more to Google than any other organisation.

Jon

Added: Tried some other things to get some clues. Using the Network Tools - Lookup facility I did a lookup on default information on [www.google.com](www.google.com) and that worked. Tried the same with [www.google.co.uk](www.google.co.uk) and the tool did nothing. It's like there is some internal filter on the URL [www.google.co.uk](www.google.co.uk) which is stopping my any network activity from seeing [www.google.co.uk](www.google.co.uk). What have I done (by accident obviously!)? I might just re-install Ubuntu.

---

### Post by wormser on 2008-03-09
Maybe it is a DNS issue.  It probably is not since other sites are working but it is always a good trouble shooting step.  Try pinging google.co.uk by their ip address of 72.14.221.104.  Here are some DNS servers you can use: 4.2.2.2 and 4.2.2.1.

---

### Post by JonAxtell on 2008-03-09
Thanks for the DNS IPs. It does seem to be a DNS issue. My DNS is my router (Vigor 2600We) but even power-cycling it doesn't solve the problem. Adding the two DNS servers to the list in the DNS tab of the Network tool seems to have solved the problem. I can also ping it now as well. The weird thing is that when I boot into XP which uses the same router for DNS services, it can access google.co.uk. Maybe XP has the IP cached and so I haven't noticed the problem in XP. Oh well, at least I don't have to re-install Ubuntu.

---

### Post by stream303 on 2008-03-10
Question is, exactly who operates those dns servers?  If this message is read and cached elsewhere a few months from now, what is to prevent it from being subverted to some unsecure bogus dns server?  In other words, it is a big security risk just using addresses mentioned in thread posts, unless you know for sure, and can verify that they haven't been tampered with.

If you know your isp's primary and backup dns server(s), great, but if you don't, why not use an alternate that welcomes outside usage.  I'm not sure those folks at the addresses you listed would like them to become universal dns servers.

I prefer using OpenDNS servers, and you can find their server addresses shown on the bottom right of this page:

[http://www.opendns.com/](http://www.opendns.com/)

I could just print them here, but I think from a security standpoint, it is better to look at them yourself.

I tend to place the addresses* inside my router's setup page*, which saves me a lot of pain in the long run, especially with multi-architecture environments.

Just some thoughts...

---

### Post by wormser on 2008-03-10
> **stream303 said:**
> Question is, exactly who operates those dns servers?  If this message is read and cached elsewhere a few months from now, what is to prevent it from being subverted to some unsecure bogus dns server?  In other words, it is a big security risk just using addresses mentioned in thread posts, unless you know for sure, and can verify that they haven't been tampered with.

That is a good point.  It definitely can be a security risk.  Those DNS servers I posted are Verizon (Level3) and are not restricted to Verizon customers.  

Details here:
[http://www.dnsserverlist.org/](http://www.dnsserverlist.org/)
[http://portforward.com/networking/dns.htm](http://portforward.com/networking/dns.htm)

---

