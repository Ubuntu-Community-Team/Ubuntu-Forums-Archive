---
title: "So you want to run your own nameserver. . ."
date: 2009-12-06
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-12-06
Hi!  Please excuse my utter lack of knowledge in this area. . . 

OK, at present, I pay for DynDNS' Custom DNS service.  From what I understand, their nameservers are authoritative for my zone/domain.  Would it be possible to setup my own nameserver as a primary master, and then pay only for redundancy?

DynDNS registered my domain when I bought it.  Does that make them my registrar?  Would setting up my own nameserver save me from this cost as well?

It's not so much that I mind paying for these services, it's more of a "let's see if we can" sort of thing.  But I can get it working, that's one less bill to pay!

Any information/advice whatsoever would be appreciated.
Thanks in advance!

---

### Post by btmiller on 2009-12-06
If you have a static IP address (i.e. not a residential cable/DSL connection that gets its IP via DHCP) then it should be possible to set up your own authoratative name server. However, each domain requires both a primary and back-up nameserver, and I'm not sure if DynDNS will let you only have a backup one. In theory, if you have two public IPs you can run both the primary and secondary name servers. Or you could buy a cheap VPS hosting package, but this will probably be more expensive than just paying DynDNS to worry about it.

You need some sort of registrar for your domain name, You can figure out your current registrat via the "whois" command (it may be DynDNS or they might be doing registrations via a 4rd party -- I've never used them so I don't know).

---

### Post by pi.boy.travis on 2009-12-06
> **btmiller said:**
> If you have a static IP address (i.e. not a residential cable/DSL connection that gets its IP via DHCP) then it should be possible to set up your own authoratative name server. However, each domain requires both a primary and back-up nameserver, and I'm not sure if DynDNS will let you only have a backup one. In theory, if you have two public IPs you can run both the primary and secondary name servers. Or you could buy a cheap VPS hosting package, but this will probably be more expensive than just paying DynDNS to worry about it.

You need some sort of registrar for your domain name, You can figure out your current registrat via the "whois" command (it may be DynDNS or they might be doing registrations via a 4rd party -- I've never used them so I don't know).

If I setup a primary master, DynDNS will provide the backup redundant server.  whois reports that DynDNS is their own registrar.  I'm not exactly clear on what the difference is between a nameserver and a registrar.  Could I manage my domain name on my own without a registrar?

Thanks for the help!

---

### Post by btmiller on 2009-12-08
I don't think it's possible to have a domain name without some sort of registrar. The registrat is authorized by ICANN to register domain names; not just anyone can do that. You might want to check [the wikipedia page](http://en.wikipedia.org/wiki/Domain_name_registrar) for details.

---

### Post by cariboo on 2009-12-09
I don't see why you'd bother, if everything works the way it should, the price won't be any less, and you have guaranteed redundancy.

DynDNS has their own nameservers, they don't contract it out to anyone else. They are also a Domain Name registrar, so they are a one-stop shop.

---

### Post by pi.boy.travis on 2009-12-10
Thanks for all the info!

---

### Post by ythe1300 on 2009-12-18
Sorry for hijacking this thread but it applies. I would really like to set up my own nameserver. As I own a domain name however the group that I registered with says they will not release the domain name to me with out me having a nameserver. If there is any information on how i wold go about this I would greatly appreciate it.

---

### Post by slakkie on 2009-12-18
If you want to host your own nameservers you need to setup your nameservers before you can tell the registar that it needs to update the whois info.

I just migrated four of my domains to my own nameservers.
My plan of attack was:

1) Setup a master/slave DNS server on your box/boxes.
2) Test it locally and remote:
```

dig a yourdomain.tld @localhost

# remote
dig a yourdomain.tld @ip.add.re.ss

# Or if you already have entries for your nameserver 
dig a yourdomain @ns1.yourdomain.tld

```


3) Make sure your current zonefile has nameserver entries (hosted at your current ISP/DNS provider. 

```

ns1     IN    A ip.add.re.ss
; different IP address for your secundairy NS
ns2     IN    A ip.add.re.ss 

```

4) Specify a higher serial then in the zonefile you're using now

5) Make sure the NS entries in your zonefile (on your own DNS server) are setup correctly for your domain. I did this on my own server and at my previous provider. I've also added my secondary nameservers from xname (ns[0-2].xname.org)

```

    IN      NS      ns1.yourdomain.tld.
    IN      NS      ns2.yourdomain.tld.
    IN      NS      ns0.xname.org. 
    IN      NS      yourold.nameservers.com.
    IN      NS      yourold2.nameservers.com.

```

6) Get a provider which wants to be your secondary/tertiary nameserver, eg xname.org (registration and service are free).

7) Make sure your DNS server allowes transfer of the zonefile from allows clients:

```

dig axfr yourdomain.tld @ns1.yourdomain.tld

```

8 ) Make sure your secundairy DNS has your zonefile (xname will send an e-mail and has an interface which shows the zonefile information). And/or test it manually:

```

dig soa yourdomain.tld @nameserver.provider.tld # eg ns0.xname.org in my case

```

If this all works, then contact your registar to change the nameservers for your domain. Namecheap.com has an excelent GUI to do that, and Nordnet doesn't :(

---

