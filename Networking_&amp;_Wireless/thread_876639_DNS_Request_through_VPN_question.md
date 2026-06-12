---
title: "DNS Request through VPN question"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by c1rcu17 on 2008-07-31
I have 2 vpn's set up at home that I use for work from home. One is the cisco vpn, and the other is the AT&T vpn client. Both vpn's use one of the companies several vpn servers. The clients set dns servers for me

My router is set to push out opendns addresses as the primary and secondary dns resolvers. My browsers do not tunnel anywhere and use my ISP provided IP address. If I right-click on my network status icon, and check 'Connection Information', I am told that the primary and secondary dns servers are the open dns ones.

My question is, what can I do to check that my browser is sending dns requests through my opendns before it checks my companies dns servers?

I don't want to be browsing a bunch of nonsense websites, then get a call from IT telling me I lost my job because of some the crazy dns requests.

Thanks all!

Browsers - Latest versions of firefox, opera, and ie4linux
VPN clients - Cisco, AT&T VPN Client

---

### Post by Njem on 2008-08-01
So what happens when you're not connected by VPN. Then your system only has your local dns to use. I suppose that works? Depending on your router you might also be able to block packets to/from the company dns addresses, so you know it can only use the local.

---

### Post by c1rcu17 on 2008-08-01
When I disconnect from the vpn it uses the opendns dns servers, but only after I flush the dns cache. When the vpn is on, I need to use their dns servers to access the intranet, what I want is for my dns requests to go to the opendns servers before the vpn ones.

---

### Post by Njem on 2008-08-01
Forgive the Win reference, but in Win VPN connections there is a setting for "Use default gateway on remote connection" which controls just such priority, so your general web browsing uses your own connection and dns, and only things that can only be found through the vpn are routed there. Prevents the office from being burdened with feeding you your general web traffic. Unfortunately I don't know the equivalent in Linux but maybe if you search for that phrase you'll find one.

---

### Post by c1rcu17 on 2008-08-01
ok, does anyone know if there is a online tool that can show you what dns servers your computer is using? I would prefer not to trust what ubuntu is saying, because the vpn's seem to convolute my settings (although it works).

---

### Post by whosmatt on 2008-08-01
> **c1rcu17 said:**
> ok, does anyone know if there is a online tool that can show you what dns servers your computer is using? I would prefer not to trust what ubuntu is saying, because the vpn's seem to convolute my settings (although it works).

You could try the testing tool at [http://www.doxpara.com](http://www.doxpara.com)

It's for the recently patched DNS vulnerability but it will also tell you which dns server  you're using.

---

### Post by kaffe_02 on 2008-08-01
> **c1rcu17 said:**
> ok, does anyone know if there is a online tool that can show you what dns servers your computer is using? I would prefer not to trust what ubuntu is saying, because the vpn's seem to convolute my settings (although it works).

form the command line "nslookup server" will show you what servers your dns is trying to resolve with.

---

