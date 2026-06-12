---
title: "Tracing an IP"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by pkj on 2010-08-24
Hi,

Which tool can trace the origin of an IP....

i.e., i have an IP and i want to know its physical location


Any suggestions

pkj

---

### Post by linux-hack on 2010-08-24
Well don't want to bee meen but google is your friend !! [http://www.ip-adress.com](http://www.ip-adress.com)

[http://www.cyberciti.biz/faq/what-is-iptrace-command-in-bash/](http://www.cyberciti.biz/faq/what-is-iptrace-command-in-bash/)

and there is a command on linux for domain infos :

```
whois [option] query
```

---

### Post by MrWES on 2010-08-24
> **pkj said:**
> Hi,

Which tool can trace the origin of an IP....

i.e., i have an IP and i want to know its physical location


Any suggestions

pkj

```
sudo apt-get install traceroute 
```
```
traceroute domain or IP
```

---

### Post by Rumpletumbler on 2010-08-24
[http://www.ip-adress.com/ip_tracer/](http://www.ip-adress.com/ip_tracer/)

---

