---
title: "Could someone please reccommend a good SSl certificate issuer that is not expensive."
date: 2015-10-21
forum: Networking &amp; Wireless
---

### Post by rscarlett on 2015-10-21
I need to purchase a wild card SSL certificate. Any suggestions of where I should purchase it?

---

### Post by TheFu on 2015-10-22
You've asked this question before?

Probably no answers because the providers are all pretty much the same for cheap certs.  They all suck equally.
Plus, you didn't say what the purpose of the cert is.  There are thousands of different TLS uses. Technically, nobody should be using SSL anymore.  All versions of the SSL protocol have been cracked for over 2 years. TLSv1.2+ are the current versions to be used. [https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet#Rule_-_Only_Support_Strong_Protocols](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet#Rule_-_Only_Support_Strong_Protocols)

Last month the free provider "Lets Encrypt" [https://letsencrypt.org/](https://letsencrypt.org/) came online. Perhaps that would work for you? 
I've used startSSL before. Not completely happy with them mainly because I was still learning and teaching isn't in their business model. BTW,  please regenerate the "DH" files periodically. Do not use the pre-installed files.

---

