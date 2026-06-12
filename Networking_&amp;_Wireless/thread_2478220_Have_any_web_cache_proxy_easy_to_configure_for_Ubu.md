---
title: "Have any web cache proxy easy to configure for Ubuntu ?"
date: 2022-08-19
forum: Networking &amp; Wireless
---

### Post by aug7744 on 2022-08-19
Hello.
I want use an proxy only for web cache accelerating internet access avoiding repeated traffic.
In other OS had the Wingate. Simple and easy to configure.

Have any web cache proxy secure, not spying user access and easy to configure for Ubuntu ?

---

### Post by TheFu on 2022-08-21
"easy to configure" is extremely subjective.  Squid is the normal proxy server for Unix systems.  Whether it is easy or not is determined by your skill, but it does require manual configuration on the squid proxy server for your network AND on each client that will use it, unless you setup a transparent proxy, which is a little harder and requires a deeper level of network understanding than average users have.

[https://www.cyberciti.biz/faq/ubuntu-squid-proxy-server-installation-configuration/](https://www.cyberciti.biz/faq/ubuntu-squid-proxy-server-installation-configuration/) is a reputable how-to website, but I didn't follow those instructions.
Squid is what a business would use or a home user with multiple devices or multiple users.

---

### Post by SeijiSensei on 2022-08-21
I suppose it would be possible to run Squid in a virtual machine and force all traffic through localhost:3128. But that would still mean everything is cached on your machine. You'd need a separate server to accomplish much. And unless you have multiple users, I don't see it would provide any advantage over the caching that your browser does automatically. I've run Squid in an office setting with 250 workstations all sending their requests through a server. I wouldn't recommend it for the average desktop user.

---

### Post by ActionParsnip on 2022-08-21
Squid all the way. Can even run it on the same system

---

