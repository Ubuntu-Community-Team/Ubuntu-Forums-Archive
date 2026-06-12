---
title: "mod_proxy URL rewriting"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2013-09-16
My folks use a webmail service that blocks non-Dutch IP adresses.

This is very unfortunate as they are travelling quite a bit and use their e-mail quite extensivly. Right now I've setup a VPN solution for them, but this has limits and, also, is 'complex' for them.

What I would like is to create a proxied URL they can use instead of their webmail. So, I want to give them 'mail.mydomain.com' on my server, that somehow proxies all requests to 'mail.provider.com' without them having to change anything.

I tried doing that useing mod_proxy, however, for some reason, my efforts have so far been in vain. This is my config;

```
<VirtualHost *:80>
</Directory>
ServerName mail.mydomain.com
ProxyPass / http://mail.provider.com
</VirtualHost>
```

That works just fine, except, it immediatly rewrites the URL to mail.provider.com, making the exercise pointless. My folks fill in mail.mydomain.com in the browser and then get redirected to mail.provider.com, not proxied. I am missing something fundamental here, but can't figure it out.

---

### Post by CrimsonRider on 2013-09-16
It seems to work a bit better now, I've changed nothing however.

But, now the pages seems to load okay'ish, but all things that are slightly more complex then text, images, javascript, do not get loaded.

It occurs to me that I could solve a bit of this using squid. But, is that possible to combine with the URL thing? So, make an URL that somehow gets translated to the mail.provider.com site via squid and apache?

---

