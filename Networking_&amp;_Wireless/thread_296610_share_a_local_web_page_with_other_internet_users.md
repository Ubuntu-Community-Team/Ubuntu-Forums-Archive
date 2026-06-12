---
title: "share a local web page with other internet users"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by yellowband on 2006-11-09
Hi
probably a common question, can't think of any useful search terms to find what i'm looking for.

anyways, i have a webpage on an apache/edgy server that i can view on my home network by typing the internal network address and path to the html file:

         [http://192.168.xxx.xxx/var/www/xxxx/index.html](http://192.168.xxx.xxx/var/www/xxxx/index.html)

I can see the page just fine from within my home network, but how do i send the address to somebody who is not in my homenetwork so they can view the page as well?  

thanks.

---

### Post by ner0tic on 2006-11-09
first off make sure your router doens't block incoming requests on port 80.

and depending on the router you ahve to have it direct port requests to your machine's local ip, some will jsut scan teh network for a reply from that port and redirect.

---

