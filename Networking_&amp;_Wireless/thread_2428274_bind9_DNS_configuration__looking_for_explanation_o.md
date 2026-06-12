---
title: "bind9 DNS configuration : looking for explanation of advice."
date: 2019-10-02
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-10-02
In this article about DNS caching. the author gives advice on how to avoid frequent cache queries.

[https://kb.isc.org/docs/aa-01537](https://kb.isc.org/docs/aa-01537)

> 
If you are using a manually-configured root hints file, then update it with the current root NS/A/AAAA RRsets for the root nameservers.

If you are using the built-in root hints, then (temporarily) configure it to use a manual root hints file which contacts the current root NS/A/AAAA RRsets.

Temporarily eliminate the root re-priming by populating cache manually with the root nameserver A and AAAA RRsets. 

To do this, you will need to send queries to your resolver for each root nameserver's A and AAAA RRset.

The query responses will be added to cache and will persist per their TTL (although they may be discarded sooner than this if max-cache-size is reached or if max-cache-ttl in named.conf is lower than the TTL on the received RRset).

How do I configure this? How does this  advice translate into changes to  make to which configruation files in the bind9 system?

---

### Post by SeijiSensei on 2019-10-02
Is this server supporting a large network of clients? If not, I don't think there is much to be gained here.

---

