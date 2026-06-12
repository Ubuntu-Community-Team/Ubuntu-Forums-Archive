---
title: "Can I use VPN for ssh, but not for browsing?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by KIAaze on 2010-11-19
Hi,

Can I use VPN for ssh, but not for browsing?
i.e. when connected to a VPN, can I make Firefox not use it, but still use it for ssh for example?

---

### Post by SlugSlug on 2010-11-19
> **KIAaze said:**
> Hi,

Can I use VPN for ssh, but not for browsing?
i.e. when connected to a VPN, can I make Firefox not use it, but still use it for ssh for example?


set firefox to direct connect in it's network settings / proxy page

---

### Post by dozycat on 2010-11-19
I forgot where I found this, but it works:

ssh -p xxx -X -C -c blowfish user@ipserver "firefox"

where:

xxx port  of ssh in the server
user user with account in the server
ipserver the ip of the server
blowfish is the protocol of compression
firefox is the navigator.

You are using the navegator in the server I know is not exactly the same you asked but it works great.

---

### Post by bodhi.zazen on 2010-11-19
> **KIAaze said:**
> Hi,

Can I use VPN for ssh, but not for browsing?
i.e. when connected to a VPN, can I make Firefox not use it, but still use it for ssh for example?

What are you wanting to do exactly? By definition, ssh is a VPN of sorts. By that I mean if all you need is shell access (ssh) or forwarding X applications, (ssh -X) or prot forwarding, you do not need VPN.

Or if you are using VPN to access a private network, and do not want to tunnel traffic on port 80, you may need to write a few rules for your route (default gw, host, etc) and or a few custom rules for iptables.

I can not tell from your post which method would be best.

---

### Post by KIAaze on 2010-11-19
> **bodhi.zazen said:**
> 
Or if you are using VPN to access a private network, and do not want to tunnel traffic on port 80, you may need to write a few rules for your route (default gw, host, etc) and or a few custom rules for iptables.


This sounds like what I want to do.
Basically, I don't want my http traffic to go through the VPN, but need the VPN to access servers on the private network.

I tried setting firefox to direct connect, but it didn't work.
At the moment I test where it goes through by either using the fact that some pages (sourceforge.net notably) strangely don't load on my network, but load through the remote network or the fact that the remote network blocks malware sites (got one from google safebrowsing for testing).

---

### Post by bodhi.zazen on 2010-11-19
> **KIAaze said:**
> This sounds like what I want to do.
Basically, I don't want my http traffic to go through the VPN, but need the VPN to access servers on the private network.

I tried setting firefox to direct connect, but it didn't work.
At the moment I test where it goes through by either using the fact that some pages (sourceforge.net notably) strangely don't load on my network, but load through the remote network or the fact that the remote network blocks malware sites (got one from google safebrowsing for testing).

I can not give you specific instructions off the top of my head, but you need to set a route, and add a gate way.

define the default GW to no go through the VPN
and a gateway for the VPN traffic

see man route and you should be able to sort it out

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

Just specify the gateway for the VPN =)

---

