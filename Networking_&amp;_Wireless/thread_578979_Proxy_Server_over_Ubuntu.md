---
title: "Proxy Server over Ubuntu"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by ma2d_te on 2007-10-17
Hello everybody,
Hai I'm newbie here. somebody can help me how to release/build proxy server using Ubuntu??

please help, ASAP. this's some urgently case.

thanks.

regard,
ma2d_te

---

### Post by Loey on 2007-10-18
Hi,

You need to install Squid in your Ubuntu. It takes time to configure specially to newbie like us. But it works and more stable and you don't need to purchase antivirus software. 

Visit this site [www.squid-cache.org](www.squid-cache.org)

:guitar:
Loey

---

### Post by Loey on 2007-10-18
This link might help after you install squid to your ubuntu [www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)


:)
Loey

---

### Post by SonicSteve on 2007-10-19
If you don't mind me jumping in I have a question.

At my school our proxy server is also running A/V software. I know that AVG has made a package for Linux are their any others that are reliable that anyone would recommend for this kind of setup?

---

### Post by ma2d_te on 2007-11-23
> **Loey said:**
> Hi,

You need to install Squid in your Ubuntu. It takes time to configure specially to newbie like us. But it works and more stable and you don't need to purchase antivirus software. 

Visit this site [www.squid-cache.org](www.squid-cache.org)

:guitar:
Loey

yes I'v been installed Squid at my ubuntu. Just type:
```
sudo apt-get install squid
```

to setup squid:
```
sudo nano /etc/squid/squid.conf
```

---

