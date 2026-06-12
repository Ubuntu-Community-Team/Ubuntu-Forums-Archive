---
title: "http_proxy doesn't work"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by cloudcatcher on 2011-08-07
Hello,

I want to set a http_proxy by command line!
I can set a proxy with the tool that comes with ubuntu (network proxy) 

I'd like to achieve the same with the command line, I searched how to do this, but nothing worked for me.

I tried to set export http_proxy=http://proxy:port
but that didnt worked i also edited ~/.bashrc and added the same line, didnt worked also..

What am i doing wrong?

---

### Post by hailtothethief on 2011-08-07
It depends on the software which you want to use the proxy. The Network Proxy tool only works if the application is specifically made to use the Gnome system-wide proxy.

http_proxy is an environment variable specifically for urllib as far as I know. But if you're sure this is the variable you need, make sure you use export and try using quotes (I think bash could be trying to expand the colon which is a builtin)

```
export http_proxy='http://proxy:port'
```

---

