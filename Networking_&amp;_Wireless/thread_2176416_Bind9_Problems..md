---
title: "Bind9 Problems."
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by djnightchild2 on 2013-09-24
Bind9 is unable to resolve hostnames in my domain [ns.ehb.local]  (Host is unreachable).
Forwarding to other DNS Servers however works fine.

[http://pastebin.com/yGPwDiBi#](http://pastebin.com/yGPwDiBi#)

Can you guys please help me?


Thanks in Advance

---

### Post by SeijiSensei on 2013-09-24
You have a typo in your zone files.  You have typed "SAO" rather than "SOA" for the "Statement of Authority" record.

Been watching *Sword Art Online* perhaps?

You can test your nameserver quickly from the command prompt.  After you have restarted BIND, enter some queries using the "host" command like this:

```

host -t soa example.com
host -t ns example.com
host -t mx example.com
host -t a www.example.com

```

replacing "example.com" with the name of your domain.  A well-configured nameserver should reply to each of the top three requests; whether you have an A record for [www.example.com](www.example.com) is, of course, optional.

If for some reason your server is not its own resolver, append "localhost" to each query to force it to use the local nameserver.

---

### Post by djnightchild2 on 2013-09-25
Okay thanks for your help. Ill try it out.

---

### Post by djnightchild2 on 2013-09-27
I corrected that part, but still didn't work. Tried MYSQL backend powerdns, and gave the same problems. 
Right now imh checking if the problems are connected to the .local domains, since PowerDNS gave error messages when creating an .local domain.

---

### Post by Doug S on 2013-09-27
There is also a typo in the TTL lines. This (two spots):```
$TLL    604800
```Should be this:```
$TTL    604800
```After I fixed that, and also the typo Seiji mentioned, named-checkzone passes:```
doug@doug-64:~/config/bind/tempe$ named-checkzone enb.local db.enb.local
zone enb.local/IN: loaded serial 2
OK
doug@doug-64:~/config/bind/tempe$ named-checkzone 234.168.192.in-addr.arpa db.192
zone 234.168.192.in-addr.arpa/IN: loaded serial 2
OK
```

---

### Post by djnightchild2 on 2013-09-28
well the named-checkzone turned out to be ok
and the host -t did its work as well (typo's fixed btw).
However, when pinging the server ns.ehb.local it still says it's an unknown host.

---

### Post by djnightchild2 on 2013-10-02
*bump*

---

### Post by Doug S on 2013-10-02
> **djnightchild2 said:**
> However, when pinging the server ns.ehb.local it still says it's an unknown host.Pinging the server from where? Some other computer on your LAN? Is that computer using your server for its DNS? Can the same computer ping the server by IP address?

---

