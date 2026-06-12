---
title: "*Domain name* alias? (not ip)"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by olejorgen on 2007-09-10
How do I make a *domain name* alias in the same sense as the ip-aliases in /etc/hosts?

ie. I want to write scp <file> <domain name alias> instead of scp <file> <full domain name>

I don't want to use the ip directly, because it might change.

---

### Post by andreid on 2007-09-10
A quick hack will be to add to your ~/.bashrc file 
export alias="host.domain.com"
and then use scp $alias
I know it's not exactly what you asked, but it works. I have looked in the manual page of resolv.conf and I don't see any option regarding what you asked. Hope that someone else has the answer.
Cheers

---

### Post by olejorgen on 2007-09-10
Yeah, I know, but $ is so annoying to type, and i really thought this would be easy to accomplish.

---

### Post by bwhitaker on 2007-09-10
Do you mean you'd rather use:
scp file user@blah:
instead of:
scp file [email]user@blah.blahdomain.com[/email]:

If you have access to the /etc/hosts file you could add it as a host record, assuming the ip is static.

just edit the file and add a line like this:
(of course change 127.0.0.1 to the ip and blah to the hostname you want to use
```

127.0.0.1 blah

```

then you should be able to use blah to reach whatever resource you want.

If it isn't static you could add the parent domain "blahdomain.com" for example to your search domains.

Still assuming the FQDN is blah.blahdomain.com, and that you're not using dhcp:

Add blahdomain.com to the search line of resolve.conf

Edit /etc/resolv.conf
```

search blahdomain.com otherdomain.com

```

if you are using dhcp it gets a little tricky, as the dhcp client changes this file with it's own entries that it recieved from the dhcp server.

---

### Post by olejorgen on 2007-09-10
> I don't want to use the ip directly, because it might change.

The search trick will work in some cases, but is no good when the domain is not splitted in subdomains.

The hostfile is a decent solution since the ip does not change often, but still.. my original goal should be possible (?)

---

### Post by olejorgen on 2007-09-16
Hm.. apparently this is not trivial. I've asked around on various irc channels too, but got no real answer.  Guess I'll have to go with the hosts file, and maybe make a cron script to update the ip.

---

