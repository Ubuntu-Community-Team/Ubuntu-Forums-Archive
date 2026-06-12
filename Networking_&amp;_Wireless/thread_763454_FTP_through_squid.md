---
title: "FTP through squid"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by adityaj on 2008-04-23
Hi

I connect to the Internet via a squid proxy. Now i need to upload a file on a ftp server outside my network. Any ftp clients where i can specify using my proxy? i tried exporting the ftp_proxy variable but the commandline ftp doesnt seem to work.

Any suggestions. Its kinda urgent. 

Thanks

Aditya

---

### Post by mrsteveman1 on 2008-04-23
Since squid is an HTTP proxy i don't think any other protocols can go through it. The only way you can do that is with a socks proxy.

---

### Post by adityaj on 2008-04-23
> **mrsteveman1 said:**
> Since squid is an HTTP proxy i don't think any other protocols can go through it. The only way you can do that is with a socks proxy.

accomplished with cURL. Thanks anyways.

---

### Post by nikeshshk on 2009-06-15
> **mrsteveman1 said:**
> Since squid is an HTTP proxy i don't think any other protocols can go through it. The only way you can do that is with a socks proxy.

I am facing same problem too through squid. HTTP traffic pass through squid but FTP traffic cant pass through it.

And can you tell me what is socks proxy.

---

### Post by adityaj on 2009-06-15
> **nikeshshk said:**
> I am facing same problem too through squid. HTTP traffic pass through squid but FTP traffic cant pass through it.

And can you tell me what is socks proxy.

use the settings of filezilla to enter your proxy details or use cURL

---

### Post by nikeshshk on 2009-06-16
What i found on google was.
Squid is only http proxy but dont supports ftp or telnet.
So what should i do if I want to pass ftp through squid. or there is any other software like squid to pass ftp?

I am using fireftp and my internal network computer's ftp request cant pass through my proxy server.

---

