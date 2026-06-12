---
title: "[SOLVED] Lag while looking up site address"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Theo148 on 2008-04-10
Despite the extremely slow service provided by my ISP, usually resolving a site's address takes less than a second (in Windows). However, when I'm browsing the web in Ubuntu sometimes my browser ends up taking 5-10 seconds looking up a site's address. While this isn't a major problem, it does get annoying at times.

Is this a DNS problem and how can I solve it if it is?

---

### Post by stream303 on 2008-04-12
If you are behind a router, you can put your isp's primary and backup dns server addresses inside the router setup page.  If you don't know your isp's addresses, the ones I prefer to use are listed on the bottom-right hand of the page:

[http://www.opendns.com](http://www.opendns.com)

You could also place these addresses directly into your DNS tab, making sure that they are listed first in your networking prefs and see if that helps if you don't want to go into the router.

---

### Post by superprash2003 on 2008-04-12
incase you are using DHCP in ubuntu.THen editing the DNS in the DNS tab may not stick, as it maybe refreshed by the router again.You would need to edit the dhclient.conf file .Hope this tutorial will help [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Theo148 on 2008-04-13
Thankyou for the replies. :) I successfully switched to the opendns servers and the URLs are being resolved much faster.

---

