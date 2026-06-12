---
title: "BIND9 errors"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by dom_madrid on 2010-11-11
Hi,

Just installed BIND9 to resolve my new domain. Followed the manual, but I can't get BIND 9 to load properly.

In the log it shows:

zone solipym.es/IN: loading from master file /etc/bind/db.solipym.es failed: CNAME and other data
zone solipym.es/IN: not loaded due to errors.

Kind of unhelpfull.

Here is my db.solipym.es if someone can help me out.

```
;
; BIND data file for local loopback interface
;
$TTL    604800
@                IN    SOA    ns.solipym.es.     root.solipym.es. (
                        2010111104        ; Serial
                            604800        ; Refresh
                             86400        ; Retry
                              2419200        ; Expire
                                604800 )        ; Negative Cache TTL
;
@                IN    NS        ns.solipym.es.
@                IN    A        127.0.0.1
@                IN    AAAA        ::1
ns                IN    A        192.168.1.50
solipym.es            IN    A          192.168.1.50
www.solipym.es        IN    CNAME        solipym.es.
mail.solipym.es        IN    A        192.168.1.50
mailserver.solipym.es    IN    CNAME        mail.solipym.es.
                IN    MX    10    solipym.es.
                IN    MX    20    mail.solipym.es.
```

Thanks for the help,

Dom

---

### Post by gordintoronto on 2010-11-11
> **dom_madrid said:**
> Hi,

Just installed BIND9 to resolve my new domain...


I'm sorry, I have no idea how to solve your problem. You posted it in "absolute beginner talk," and it's an "advanced" question.

Did you install bind9 using Synaptic or Software Center?

---

### Post by dom_madrid on 2010-11-11
Thanks for the response,

I use the synaptic package.

I'll repost later in the 'advanced' section.

Dom

---

### Post by toekneewood on 2010-11-11
What happens if you tail the messages
```

tail -f /var/log/messages

```
then reload bind.  Do you then get any log output?

---

### Post by dom_madrid on 2010-11-11
> **toekneewood said:**
> What happens if you tail the messages
```

tail -f /var/log/messages

```then reload bind.  Do you then get any log output?

Same as before reloading. No change in messages.

---

