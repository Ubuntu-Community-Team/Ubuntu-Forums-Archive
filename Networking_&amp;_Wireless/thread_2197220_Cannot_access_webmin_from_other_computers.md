---
title: "Cannot access webmin from other computers"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by itpro007ca on 2014-01-02
I apologize if this is not the right category -but,then,it still may be networking related,anyway.

Here's the situation:

Last night I installed Webmin,and,then eventually the Apache and MySQL modules,after which I installed phpmyadmin separately.

In any event,all work fine,from this PC,but,I could not access any of those pages,meaning: blackbox,blackbox/testphp.php,blackbox/phpmyadmin,blackbox:10000 from my laptop downstairs.

After adding a port 80 rule to GUFW,I could access all except: blackbox:10000 and blackbeard:20000.

I tried taking down the a/v firewall on the laptop,but,that wasn't it.I tried adding a GUFW rule for 192.168.2.12 ==> 192.168.2.10 port 80.No go.

Webmin is configured to start at boot time.

What have I missed?

---

### Post by lisati on 2014-01-02
Are you trying to access a webpage or webmin? Opening up port 80 should be fine for accessing normal webpages, but for webmin, you might need to look at port 10000 instead.

---

### Post by itpro007ca on 2014-01-02
Hi Lisati:

Yes,I am aware that it's port 10000.

Anyway,checking a resource I use,I realized my mistake.

I needed to add a rule in ufw to open port 10000 and 20000 for usermin.

Meaning:

  ```
sudo ufw allow 10000/tcp # webmin
``` and the same,but 20000 for Usermin.

After doing that,both worked fine.

Thanks.

---

