---
title: "Intranet Problem"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by md5hash on 2007-05-04
i have a intranet site named 'http://intranet/portal' but when i try to browse the site from other pc its redirecting to [http://www.intranet.com/portal](http://www.intranet.com/portal).. 

i have my firefox configure no proxy for "localhost, 127.0.0.1, intranet"
and "intranet" is listed in my ignore host lit in network proxy

---

### Post by kidders on 2007-05-06
Hi there,

Looks like you're having DNS trouble. Could you describe your network?

---

### Post by md5hash on 2007-05-09
i dont know much about our network all i know is we are connect to the net using a proxy

---

### Post by kidders on 2007-05-09
Hmmm... without more information, I can't really do much more than describe your problem. :-( Essentially, what's probably happening is...
[LIST=1]
[*]Firefox looks up the hostname "intranet".
[*]Your DNS service denies any knowledge of its existence.
[*]Firefox starts guessing alternative hostnames.
[*]Your DNS service resolves one of them (www.intranet.com).
[*]Firefox assumes that's what you meant to type, and takes you there.
[/LIST]
Your proxy settings (ie what hosts browsers will use your proxy for) are irrelevant here, because Firefox is being told that there is no local machine called "intranet".

How to fix this depends on your DNS configuration, and where it comes from (eg DHCP). Some people like to tweak their /etc/hosts to fake DNS resolutions for non-existant hostnames, but you would have to do that on every machine in your entire network. The best thing to do might be to contact your network admin.

---

