---
title: "persist option timeout in resolv.conf"
date: 2022-12-18
forum: Networking &amp; Wireless
---

### Post by ralph.eichelberger on 2022-12-18
I just want to add the option timeout:1 to reduce the time that dns lookup is blocking. 
It seems that is not so easy doable. Even if I add the options to 
/etc/resolvconf/resolv.conf.d/base
like this: 
rotate timeout:1 attempts:1
like it is suggested here [https://manpages.debian.org/testing/resolvconf/resolvconf.8.en.html](https://manpages.debian.org/testing/resolvconf/resolvconf.8.en.html)
under ifup:[INDENT]N.B.: On a machine where resolvconf has just been or is about to be installed and which previously relied on a static /etc/resolv.conf file,[/INDENT]
[INDENT]
[/INDENT]
[INDENT]•[/INDENT]
[INDENT]the nameserver information in that static file, (which is to say the information on nameserver, domain, search and sortlist lines) should be migrated to the appropriate iface stanza(s) in /etc/network/interfaces(5) as just described;[/INDENT]
[INDENT]•[/INDENT]
[INDENT]options (which is to say, any options lines) should be migrated to /etc/resolvconf/resolv.conf.d/base.[/INDENT]
It will not work.  
Network-Manger is still overwriting any attempt to change /etc/resolv.conf and doesn't add the options from  /etc/resolvconf/resolv.conf.d/base.

Where to go from there?

Any help appreciated!

---

