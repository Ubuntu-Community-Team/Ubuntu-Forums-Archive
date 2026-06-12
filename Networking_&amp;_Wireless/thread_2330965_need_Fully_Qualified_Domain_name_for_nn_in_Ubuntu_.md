---
title: "need Fully Qualified Domain name for nn in Ubuntu 16.04 LTS"
date: 2016-07-16
forum: Networking &amp; Wireless
---

### Post by dalekellytoo on 2016-07-16
Ubuntu 16.04 LTS

installed the nn newsgroup reader from Ubuntu software-center

when I run nn I get
hostname=my_hostname, You need a fully qualified domain name

does any have a URL about setting up a fqdn? or know how?

if I run
hostname --fqdn
I get
my_hostname

---

### Post by dalekellytoo on 2016-07-16
this works for slrn

[http://slrn.sourceforge.net/docs/slrn-FAQ-2.html#ss2.2](http://slrn.sourceforge.net/docs/slrn-FAQ-2.html#ss2.2)

Some Linux distributions (e.g. Ubuntu) do not provide the option of giving the system a fully qualified domain name during installation. This can be fixed by editing the /etc/hosts file. E.g., Before:
  
        127.0.0.1       localhost
        127.0.1.1       desktop
 After:
  
        127.0.0.1       localhost
        127.0.1.1       desktop.your.domain     desktop

same error message for nn

---

