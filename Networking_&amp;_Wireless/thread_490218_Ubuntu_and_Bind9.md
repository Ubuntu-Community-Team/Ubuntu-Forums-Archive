---
title: "Ubuntu and Bind9"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by terrrorr on 2007-07-02
Hello!

at the begining... i'm very sory for my bad english...

I got a major problem which i cannot resolve. I have a DNS server (ubuntu 6.06 LTS Server) which uses Bind9. All worked fine after i made some modifications. I got an error about rndc key (rndc: connect failed: connection refused). I did not have much time to resolve this problem , so i made a desission to restore all data from my backup files.... No changes. I even installed my server again, but i stil got this same message.

Now i'm very confused...

I did all of the configuration and installation by several instructions from [www..](www..). but stil no go

Is there something i have missed.

What i have done

[LIST]
[*]Restore all data from backup file
[*]Made full server installation
[*]write all configuration by hand
[*]tried with another domain name
[/LIST]

Please.... help me before i loose my hair

---

### Post by darkog on 2007-07-02
first make sure that it's running. 

```
ps aux | grep named
```

you should see "named -u bind" listed.

then check your logs?

```
cat /var/log/syslog | grep named | more
```

and post here if you see anything that stands out.

---

### Post by terrrorr on 2007-07-03
Thank you very many :p

This hint gave me everything I needed. The problem was much simpler than I thought.

Solution:

Use proper ssh client with right configurations before you try to fix some problems. Somehow there was some cyrilic letters inside the configuration file even i'm using finnish keyboard :confused:

Phew... this was a good reminder. Allways use -- tail -f <log_file> | grep <what_you_want_to_know> --- when you are making changes in your configuration ;-)

thank you darkog

---

### Post by darkog on 2007-07-03
no problem. you welcome.

---

