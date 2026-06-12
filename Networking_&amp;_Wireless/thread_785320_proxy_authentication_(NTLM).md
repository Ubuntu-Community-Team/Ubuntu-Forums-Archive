---
title: "proxy authentication (NTLM)"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by sleeper.design on 2008-05-07
i have a problem connecting through a corporate proxy (squid) that is configured to use NTLM authentication.

i tried:
```
export http_proxy = [http://local.proxy.address:8080](http://local.proxy.address:8080)
export http_proxy_username = domain\username
export http_proxy_password = password
```

and also

```
export http_proxy = [http://domain\username:password@local.proxy.address:8080](http://domain\username:password@local.proxy.address:8080)
```
but it doesn't work.

any ideas?

---

### Post by Cameri on 2008-12-23
more like:

```
export http_proxy="http://username:password@proxy_host:port"
```

Also, you may want to add to your ~./bashrc file this:
```
http_proxy="http://username:password@proxy_host:port"
```

Note: Don't use export there.

---

