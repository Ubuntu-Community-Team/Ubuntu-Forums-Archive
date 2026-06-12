---
title: "How to block https sites..?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-22
I am using squid proxy,using squid proxy i am to block all [COLOR=DarkSlateGray]http[/COLOR] sites but how can i block [COLOR=DarkSlateBlue][COLOR=DarkSlateGray]https[/COLOR] [/COLOR]sites..?

---

### Post by nhasian on 2010-06-22
https uses port 443.  you can block https by blocking all port 443 traffic.

---

### Post by karthick87 on 2010-06-22
> **nhasian said:**
> https uses port 443.  you can block https by blocking all port 443 traffic.


I dont want to block all https sites,i wanted to block some particular sites..

---

### Post by 11hjpphty76lkjj on 2010-06-22
I can't recall the name of the addon, but Firefox has an addon that you can block specific sites. and it does wildcards, etc.

Also depending on what router/AP you have, some have a site blocking function in the admin/setup dialogs.

The firefox addon you should be able to find on the addon site.

To check if your router will block you can look up the specs or go to 192.168.1.1 (unless you configured your network differently) and see if that option is available.

Hope this helps.

A

---

