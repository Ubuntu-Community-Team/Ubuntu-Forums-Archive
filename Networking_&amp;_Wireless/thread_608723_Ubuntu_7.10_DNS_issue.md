---
title: "Ubuntu 7.10 DNS issue"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by dirtblade on 2007-11-10
I've been searching thru the same type of topics in this forum but couldn't find any clear answer regarding Ubuntu 7.10 DNS issue. Well, perhaps I've missed it some how. If someone knows anything, please point me there.

Basically, lots of people have reported a problem with DNS in Ubuntu 7.10 but no one mentioned my type of situation. I use my Ubuntu 7.10 in several places. I usually use DHCP to get local network IP address and this is where I start having issues.

If, lets say, I work behind NAT and DHCP server released 10.1.1.x IP address to my box it also gives me set of local DNS servers, usually the same subnet of 10.1.1.x, at that point all local network resources works just great but as soon as I try to use Firefox for external internet browsing DNS name resolution becomes extremely slow ~10-15 seconds for each site. If that site I'm trying to visit has banners pointing to other site then it takes 1-2 min to open that page. Again, there is no such problem if I browse local network resources it only applies to external links.
I've tried disabling IP v.6 but it doesn't help. Here goes funny part, if I'm still behind NAT but instead of using local DNS server as my primary I manually change to to some external (OpenDNS, WCom, etc.) everything externally starts working perfectly - fast and reliable but... the internal sources are inaccessible even if I keep internal DNS settings within my configurations as a secondary DNS.

Any thoughts?

Thank you all in advance.

---

### Post by gexcko on 2007-11-10
What DNS server are you running locally?
Does this delay happen only the first time to request a hostname, or every time?

Sounds like there could be an issue in the setup (forwarding to servers vs. running a local cache and doing lookups directly)

---

### Post by dirtblade on 2007-11-10
I'm trying to be 'original', so I use my box on MS Active directory-based corporate network ;) meaning that local DNS servers are MIcrosoft DNS and 'yes' it happens on every request not only first time. We have couple of other users who runs MacOSX Leopard on their laptops within the same environment and apparently they are not experiencing the same issue.

---

### Post by gexcko on 2007-11-10
hmm I was thinking you were running the ubuntu server with bind9 - i had a similar issue with my setup but it affected all clients ... sorry I can't be of help to ya.

---

### Post by dirtblade on 2007-11-10
Thanks anyway! By the way, as something interesting, I also have VMWare workstation running on my box with virtual Win2003 server. My virtual OS has no issues as well... Weird!

---

### Post by HermanAB on 2007-11-10
ADS, ughhh - I can feel your pain... 

When you use ADS, you have to point your desktop to the corporate DNS as the *only* DNS server(s).  The corp DNS should forward to an upstream DNS to resolve queries.  If you try to bypass the corp DNS  then the LAN servers will not resolve.

BTW, you can test the speed of the corporate DNS servers using 'dig', then put the fastest one at the top of /etc/resolv.conf.  Otherwise, look at a fast XP desktop and see which one is listed first.

Cheers,

Herman

---

### Post by dirtblade on 2007-11-10
Hmmm...
Well, I've used 6.10, 7.04 before and did not have this problem. Besides, I'm not sure why even if I use static IP confs like this, for instance:

IP: 10.1.1.x
M: 255.255.255.0
GW: 10.1.1.x

NS1: 199.6.100.25
NS2: 10.1.1.x

Ubuntu would not use secondary DNS to resolve internal resources. Why? It used to work in all previous versions...

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

