---
title: "BIND9 with nsupdate results in error: update failed: NOTIMP"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by nuesel2 on 2015-10-07
Hello!
I would like to update my BIND configuration from the command line, but I just get the error:

/usr/bin/nsupdate -k /etc/bind/Kupdate_key.+157+10019.private
> update add new.domain 300 A 1.2.3.4
> send
; TSIG error with server: expected a TSIG or SIG(0)
update failed: NOTIMP

The BIND log keeps empty upon this command.
Does NOTIMP mean **NOT** **IMP**LEMENTED?

I created a TSIG key with:
dnssec-keygen -a HMAC-MD5 -b 512 -n HOST update_key
I added these lines to named.conf.local:

key dyndns {
  algorithm HMAC-MD5;
  secret "mysecret";
};

zone "dyndns.gruenbaer.net" IN {
  type master;
  file "/etc/bind/subdomain.domain.com.zone";
  allow-update { key dyndns; };
};

I extracted the string for mysecret from Kupdate_key.+157+10019.private.

I'm using Ubuntu 14.04 (kernel 3.19.0-30-generic) and bind 9.9.5 (version 1:9.9.5.dfsg-3ubuntu0.5).
Does anbody know, why this does not work?

Regards
Nuesel

---

### Post by nuesel2 on 2015-10-25
I needed to specify which BIND server to contact with nsupdate. In my case a remote server was contacted which obviously indeed didn't support the update feature.
```
/usr/bin/nsupdate -k /etc/bind/Kupdate_key.+157+10019.private
> server localhost
> zone domain
> update add new.domain 300 A 1.2.3.4
> send
```

Moveover the private and the public key needed to readable by nsupdate.
Now it works.

Thanks.

---

