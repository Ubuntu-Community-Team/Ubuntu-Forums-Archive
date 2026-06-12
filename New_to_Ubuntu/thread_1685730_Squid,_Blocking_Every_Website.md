---
title: "Squid, Blocking Every Website"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Hovercat on 2011-02-11
I'm trying to block a few websites from my network, but when I have Squid used as my proxy, every website is blocked.  I get this error for every website:  ```
ERROR The requested URL could not be retrieved  The following error was encountered while trying to retrieve the URL: http://www.google.com/      Access Denied.  Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.  Your cache administrator is webmaster.  Generated Fri, 11 Feb 2011 11:11:17 GMT by NETWORK-SERVER (squid/2.7.STABLE9)
```  The only changes I've made to my squid.conf is:  ```
acl bad url_regex &quot;/etc/squid/squid-block.acl&quot; http_access deny bad
```  and /etc/squid/squid-block.acl contains:  ```
.4chan.org .redtube.com .brazzers.com .brazzersmobile.com 
```  EDIT: I don't have it the way the forum parsed the text, it's all on it's own line.

---

### Post by Blutkoete on 2011-02-11
I think the default setting for Squid is to block all traffic. You must allow the other computers to access the internet.

Example (for all computers within 192.168.1.x):


```
acl allcomputers src 192.168.1.0/255.255.255.0
http_access allow allcomputers
```

EDIT: WARNING: I'm no expert on the subject and this might cause security problems.

---

### Post by Hovercat on 2011-02-11
Thanks, I'll try it when I get home.

---

### Post by Hovercat on 2011-02-11
Oh my god! It works! Thank you soooooo much!

---

