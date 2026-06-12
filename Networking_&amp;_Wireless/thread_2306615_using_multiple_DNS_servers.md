---
title: "using multiple DNS servers"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by mawxcarroll on 2015-12-17
I have an Ubuntu workstation in my office and I would like to use OpenDNS -- it's *significantly* faster than our campus dns servers. However, when I do so, I can no longer print to network printers. I thought that either using 

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

or

```
supersede domain-name-servers 208.67.222.222,208.67.220.220,198.17.40.11,198.17.40.113;
```

would work (where the 198. addresses are the local dns servers).

However, in either of those cases, Ubuntu seems to use the local dns servers exclusively. Is there a way to configure the dns servers so that OpenDNS is used by default and then, if something (like a network printer) isn't resolved, Ubuntu moves on to one of the local dns servers?

Or perhaps I'm just misunderstanding how all of this works!

Thanks for any help!

Cheers,
tom

---

### Post by SeijiSensei on 2015-12-17
Not really.  The only solution I can think of is to set up your own DNS server with BIND9.  You could point the school domain to the school's server and use a forwarders directive to send everything else off to OpenDNS.  

Now if you know exactly which hostnames are needed to access the printers, and their associated IP addresses, you can put this information into /etc/hosts.  The resolver will consult that before using DNS.  You could then use OpenDNS for everything else.
```

10.10.10.10     myprinter1.example.com
10.10.10.11     myprinter2.example.com

```

---

### Post by mawxcarroll on 2015-12-18
Thanks, SeijiSensei -- that put me on the right track. I just changed the printer configuration to refer directly to the printer's ip address and it's working fine.

Cheers,
tom

---

