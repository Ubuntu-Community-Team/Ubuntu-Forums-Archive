---
title: "apache 2 pointing to standard page when it isn't set to"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by AuroraDizon on 2014-10-29
So if I go to the private ip 192.168.***** it will show what its suppose to show from /var/www/ but if I go to a website pointing at it or even localhost different things happen.  If I type in localhost it will not take me to the index I set up, but the standard one.  If I redirect from another website it seems not to work.

I have been working on trying to get my server running with more programs on it and had a virtual host for a minuet but I think I removed it.  May have something to do with why I can't get to it from a no-ip dynamic dns (shows a blank page). But I believe I can get to it directly from my ip address.

Any idea on what file I must edit?

---

### Post by JazzPotato on 2014-10-29
I'm not sure I am understanding your question properly, however, do you mean that when you visit the page from an external ip address you are served the "Site not found" page? Are you sure you have port forwarded correctly?

---

### Post by SeijiSensei on 2014-10-29
Read this: [http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)

The page you see depends on the hostname in the URL.  [http://localhost/](http://localhost/) may deliver a different page from [http://myhostname/](http://myhostname/).

---

