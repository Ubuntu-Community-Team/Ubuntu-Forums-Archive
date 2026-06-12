---
title: "Slow DNS lookups, I've tried everything"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by FuturePilot on 2008-03-05
The last few days I've been getting really long DNS lookups. About 80% of the time I click on a link it stalls at "Looking up..." for 3-10 seconds. At first I thought it might be IPv6, so I disabled it in Firefox and even blacklisted it but it didn't help any. So I thought it might be my ISPs DNS servers, so I used the OpenDNS DNS servers. Problem still exists. I thought it might be my router so I removed that and hooked up directly to my cable modem. Still have the problem. Tried OpenDNS without the router. The problem is *still* there. Grrrrr:mad:
What else can I try? 
Is it possible it still could be an issue with my ISP? This just started happening, I've never had this problem before.](*,)

---

### Post by FuturePilot on 2008-03-06
Ok, I think it really is my ISP's DNS servers. I put the OpenDNS servers back into my router earlier this evening and the problem seemed to disappear. So out of curiosity I switched back to my ISP's DNS servers and immediately I ran into the problem. Looks like I need to make a call :mad:

---

### Post by stream303 on 2008-03-07
> **FuturePilot said:**
> I put the OpenDNS servers back into my router earlier this evening and the problem seemed to disappear.

This has been the source of my happiness for the last few years.  OpenDNS primary and backup servers configured in my router and just let the system run dhcp.  Works every time, whether it is *nix, Mac, or Windows boxes.  The trick is to put the dns servers into the router's config page.  DNS issues now are so, yawn. :)

[http://www.opendns.com/](http://www.opendns.com/)
(see bottom right of page)

It works great too if you need to use your ISP's dns servers, but as you've seen they can get bogged down.

I also do away with other windows-centric features like Upnp, disable remote access, and make sure that I've changed the default username and password in the router.

When I'm feeling paranoid, I'll do a

```
cat /etc/resolv.conf
```

just to make sure that I'm not being redirected to some bogus / unsecure dns server somehow.

---

### Post by FuturePilot on 2008-03-08
> **stream303 said:**
> This has been the source of my happiness for the last few years.  OpenDNS primary and backup servers configured in my router and just let the system run dhcp.  Works every time, whether it is *nix, Mac, or Windows boxes.  The trick is to put the dns servers into the router's config page.  DNS issues now are so, yawn. :)

[http://www.opendns.com/](http://www.opendns.com/)
(see bottom right of page)

It works great too if you need to use your ISP's dns servers, but as you've seen they can get bogged down.

I also do away with other windows-centric features like Upnp, disable remote access, and make sure that I've changed the default username and password in the router.

When I'm feeling paranoid, I'll do a

```
cat /etc/resolv.conf
```

just to make sure that I'm not being redirected to some bogus / unsecure dns server somehow.
Thank you for the info. Kind of off topic but I guess I really don't need Upnp?

I tried calling my ISP today but they were really backed up. So I'll try again tomorrow.

---

### Post by stream303 on 2008-03-08
> **FuturePilot said:**
> Thank you for the info. Kind of off topic but I guess I really don't need Upnp?

Well, I know nothing that I use with Linux needs Universal Plug n Play.  Even when I was running windows, I didn't need it, so I just disable the stuff I don't need to keep it out of the way.

> I tried calling my ISP today but they were really backed up. So I'll try again tomorrow.

Unless there is something in the ISP agreement about being forced to use their dns servers, why not just stick with OpenDNS servers?

---

