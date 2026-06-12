---
title: "won't let me change the dns server (-&gt; internet painfully slow)"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by bloah on 2006-08-26
hi,

my internet is painfully slow on ubuntu (not on windows though), so i did some research.
after finding the solution (changing the dns server to my isp's) i have some problems to apply it.

if i go to system -> administration -> networking | -> DNS | delete the given dns server (192.168.254) and replace it with my isp's (DNS 1: 195.20.224.234
DNS 2: 194.25.2.129) it somehow switches back after a while...

internet works fine for a moment and then stops.
if i go to the dns tab now, i can see that the dns servers haven't changed at all. :confused: 

thanks in advance...

---

### Post by Woei on 2006-08-26
> **bloah said:**
> hi,

my internet is painfully slow on ubuntu (not on windows though), so i did some research.
after finding the solution (changing the dns server to my isp's) i have some problems to apply it.

if i go to system -> administration -> networking | -> DNS | delete the given dns server (192.168.254) and replace it with my isp's (DNS 1: 195.20.224.234
DNS 2: 194.25.2.129) it somehow switches back after a while...

internet works fine for a moment and then stops.
if i go to the dns tab now, i can see that the dns servers haven't changed at all. :confused: 


192.168.254 isn't a valid IP address, but we'll make the assumption you simply forgot a .1 or .0 in between. If that's the case, then that means your router/NAT also has a built-in DNS server that should normally forward DNS requests it doesn't have in its cache to your ISP's DNS servers. This is generally a *good thing*. Could you please append the contents of /etc/resolv.conf here ?

Also, are you 100% sure it's DNS related ? Your problem sounds like a case of a broken IPv6 setup at your ISP. Dapper comes with IPv6 enabled by default, and, if your ISP configured things correctly, it shouldn't give you that much of a headache. However, if they didn't, every DNS request will have to timeout first on an AAAA record (ipv6), before it'll drop back to a straight A record (ipv4). Follow the guide [here](http://www.ossgeeks.co.uk/?p=20) or [here](http://blogs.sun.com/sharps/entry/faster_surfing_with_the_dapper) to disable ipv6 and try again.

If all else fails: sudo /etc/init.d/networking restart.

---

### Post by bloah on 2006-08-26
> **Woei said:**
> 192.168.254 isn't a valid IP address, but we'll make the assumption you simply forgot a .1 or .0 in between. If that's the case, then that means your router/NAT also has a built-in DNS server that should normally forward DNS requests it doesn't have in its cache to your ISP's DNS servers. This is generally a *good thing*. Could you please append the contents of /etc/resolv.conf here ?

Also, are you 100% sure it's DNS related ? Your problem sounds like a case of a broken IPv6 setup at your ISP. Dapper comes with IPv6 enabled by default, and, if your ISP configured things correctly, it shouldn't give you that much of a headache. However, if they didn't, every DNS request will have to timeout first on an AAAA record (ipv6), before it'll drop back to a straight A record (ipv4). Follow the guide [here](http://www.ossgeeks.co.uk/?p=20) or [here](http://blogs.sun.com/sharps/entry/faster_surfing_with_the_dapper) to disable ipv6 and try again.

If all else fails: sudo /etc/init.d/networking restart.


thank you very much...

i changed the dns after reading a post in some topic (i think it's even been this forum) according to my isp's site [http://faq.1und1.de/access/11_internet/zugang_einwahl_passwort/8.html](http://faq.1und1.de/access/11_internet/zugang_einwahl_passwort/8.html) (it's german but you should be able to read the digits ;) ). and it worked, just for some moments, though.

anyway, after deactivating ipv6 in firefox it flies :mrgreen: 
i think i am going to do it system wide (thanks to your given link).

many thanks again ...

---

