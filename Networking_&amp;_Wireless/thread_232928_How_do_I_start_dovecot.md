---
title: "How do I start dovecot?"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by sugarat on 2006-08-09
Having just installed Ubuntu 6.06 onto my server, I have done
```

sudo apt-get install dovecot-common

```

and then tried to start dovecot, with
```

sudo /etc/init.d/dovecot start

```

It doesnt look like it has started though, as if I telnet into port 143 there is no response at all. 

Any ideas?

---

### Post by sugarat on 2006-08-09
Problem solved. 

I also needed to install dovecot-imapd  and now it works.

---

