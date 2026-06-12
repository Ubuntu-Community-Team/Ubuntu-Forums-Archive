---
title: "My ISP's DNS redirects me to SPAM"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by Elijah on 2008-08-09
Hi, 

Everytime I get a browser error like a 404 I get redirected to this page: 
[http://i259.photobucket.com/albums/hh286/pinoguin/speedtestnet_1218336452354.png]("http://i259.photobucket.com/albums/hh286/pinoguin/speedtestnet_1218336452354.png")

I tried deleting the dns entries but somehow it comes back each time... I think opendns can cure this as someone here in the forums already suggested to me but is this something that I should be concerned about for my internet connection? Is this ISP forcing spam to me by inserting bogus dns entries? What do you call this practice of disrupting dns? 

I'm asking what it was because I'm thinking of switching ISP's, if this ISP is guilty of forcing me those dns then I'll tell them that so they can terminate my account easily.

---

### Post by SMGauna on 2008-08-09
I use dnsmasq on my router, it has an option called "bogus-nxdomain".  Basically, you do a dig +short to some address that you know to be re-directed, then assign the returned IP as a bogus-nxdomain.

A nx domain is a "Non Existant" domain.

Check out : [http://en.wikipedia.org/wiki/DNS_hijacking](http://en.wikipedia.org/wiki/DNS_hijacking)

---

### Post by PmDematagoda on 2008-08-09
> **Elijah said:**
> Hi, 

Everytime I get a browser error like a 404 I get redirected to this page: 
[http://i259.photobucket.com/albums/hh286/pinoguin/speedtestnet_1218336452354.png]("http://i259.photobucket.com/albums/hh286/pinoguin/speedtestnet_1218336452354.png")

I tried deleting the dns entries but somehow it comes back each time... I think opendns can cure this as someone here in the forums already suggested to me but is this something that I should be concerned about for my internet connection? Is this ISP forcing spam to me by inserting bogus dns entries? What do you call this practice of disrupting dns? 

I'm asking what it was because I'm thinking of switching ISP's, if this ISP is guilty of forcing me those dns then I'll tell them that so they can terminate my account easily.

Perhaps your ISP may be a victim of the DNS cache poisoning vulnerability that was there recently, in this case OpenDNS should fix it for you.

---

### Post by Elijah on 2008-08-09
ahhh 'dns cache poisoning', that seems to be a good term for it. Can this be prevented by my ISP?

---

### Post by jimv on 2008-08-10
> Is this ISP forcing spam to me by inserting bogus dns entries?

It may be more productive to contact the support line for your ISP and send them this screenshot to see if it's something they're doing or not.

---

### Post by wdaniels on 2008-08-10
I don't think the ISP would be doing this intentionally. What would be the benefit to them from sending people to this page? It does raise some questions about their competence though if they haven't identified and fixed this issue already.

---

### Post by jimv on 2008-08-10
Either way he's going to find out some good info.  If it's something they're doing, he should dump them.  If their DNS servers are poisoned, he should dump them.  If they can't recreate the problem, there's something funky on his machine.

---

### Post by silkstone on 2008-08-10
You could use the OpenDNS nameservers instead, as suggested by PmDematogoda

[http://www.opendns.com/](http://www.opendns.com/)

They are...

208.67.222.222
208.67.220.220

---

