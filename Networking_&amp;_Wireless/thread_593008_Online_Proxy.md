---
title: "Online Proxy"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by uhlive on 2007-10-26
I would like to setup an online proxy sorta like the ones you see on websites like 

"proxify.com" for example

I am currently running the lasest version of apache.. and I'm just curious as how to create one.. Any ideas? help?

---

### Post by uhlive on 2007-10-28
Does no one have any information on this?

---

### Post by Gammell on 2007-10-30
Nothing specific, but maybe you can do something with the apache2 proxy modules?... There's some online [documentation](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html) available...

---

### Post by Gammell on 2007-10-30
...Though a quick google looks like they're probably using some version (possibly modified) of:
[list]CGIProxy,[/list]
[list]Glype Proxy,[/list]
[list]PHProxy, or[/list]
[list]Zelune.[/list]
There also appears to be a lot of sites dedicated to providing skins for the above scripts...

---

### Post by KCPokes on 2007-10-30
CGIProxy is pretty straightforward and easy to set up. There hasn't been any development on it in a while, but works for the most part.  The version I was running did not have any logging in it, which bothered me, so I wrote my own logging so I could capture who was using my proxy (I had it password protected as well) and where they were going.  I would recommend making the same modification (its just Perl code) unless you like flying blind as to where people are going.  I only had it in place to get around firewall restrictions at work to a few sites (like eBay).  

Just remember a proxy in the wrong hands can get you into trouble as all requests will be coming from your IP and you are liable for requests made on your connection.

---

