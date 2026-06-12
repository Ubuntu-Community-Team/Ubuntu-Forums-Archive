---
title: "Permanent redirect for subdomain"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by blasto333 on 2011-02-09
If I have mail.poweranew.com and want to forward to -->[https://poweranew.com:4343](https://poweranew.com:4343), is this the best way to do it?

<VirtualHost *:80>
    ServerAdmin [email]admin@poweranew.com[/email]
    ServerName mail.poweranew.com
    redirect permanent / [https://www.poweranew.com:4343](https://www.poweranew.com:4343)
</VirtualHost>

---

### Post by robsoles on 2011-02-12
By memory it looks like one way to do it.

Might I suggest though that this has nothing to do with Ubuntu (beyond that apache runs in Ubuntu like it does in lots of distros) and you would get much more (possibly even better) response(s) if you asked on [www.webmasterworld.com](www.webmasterworld.com) ?

---

