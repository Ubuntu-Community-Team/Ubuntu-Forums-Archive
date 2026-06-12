---
title: "What is the lowdown with hostname.local and hostname"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-11-12
I find samba only works when I specify hostname.local.

I can also ping my machine at hostname.local but not at hostname.

Is this a new convention in ubuntu?

Thanks.

---

### Post by jonobr on 2008-11-12
Hello

When you open your terminal and enter hostname
what dose it give you? Did you remove lines from your /etc/hosts
If it doesnt give away anything critical , could you post the contents here?

---

### Post by sefs on 2008-11-12
the command hostname gives toto

/etc/hosts
```

127.0.0.1	localhost
127.0.1.1	toto

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/hostname
```

toto

```

What is the current convention that works....
should it be toto or toto.local

The aviah thing seems responsible for appending the .local part.

---

### Post by Iowan on 2008-11-12
Just for grins, try editing /etc/hosts: ```

127.0.0.1	localhost
127.0.1.1	toto [COLOR="Red"]toto.local[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
``` See if it has any effect on pings - probably not, but worth a try!

---

### Post by jonobr on 2008-11-12
Hi

It looks as if there is no space between between your 127 entries and the name, I also think (could be wrong here) toto should be after 127.0.0.1

---

### Post by sefs on 2008-11-13
> **jonobr said:**
> Hi

It looks as if there is no space between between your 127 entries and the name, I also think (could be wrong here) toto should be after 127.0.0.1

I think around dapper it was that the fresh installs removed the hostname from the 127.0.0.1 line and placed it next to that 127 line.  At that time it had caused a bit of a problem.

---

### Post by sefs on 2008-11-13
Iowan ... are you saying that I can put more than one name on those lines?  That would be great.  What about the /etc/hostname  can I put two names in there as well or does that only take one name.

thanks.

---

### Post by sefs on 2008-11-13
ok here is what I was able to garner...

short names go into /etc/hostname

FQDN's go into /etc/host


So in /etc/hostname I should have toto

in /etc/host on the 1.27.0.1.1 line I should have both toto.local and toto

now I can ping everything.

Although samba seems to only work properly when i use the FQDN name and not the shortname.

---

### Post by Iowan on 2008-11-13
Yes, there should be a space or tab between address and hostname(s). [This]("http://linux.die.net/man/5/hosts") manpage link has information and examples.  You can put multiple names on the line, but (contrary to my example) the FQDN name should come first - nicknames follow.  There is (reportedly) a separate hosts file kept by avahi(/etc/avahi/hosts) but I'm not near my machine to check.  The man page for that one suggested only FQDN.

---

### Post by jonobr on 2008-11-13
Just as a follow up comment, you can have toto totoanddorothy you could even have ( i dont think this is right) [email]toto@mydomain.com[/email].
They just resolve off that name before they go to DNS.

They can all be on the one line.

IN fact, some cheap protection programs that block you getting to "dubious" sites simply put entries in your hosts file which can map to the loopback address or another address which is not the site,
So when someone goes to eg [www.xxx_action.com](www.xxx_action.com) there is an entry in your hosts file which will resolve to your local address and give you a page not found,
You could off course make it go to an internal website which has a page says "naughty naughty, HR will be down to see you in a few minutes....." :)

---

