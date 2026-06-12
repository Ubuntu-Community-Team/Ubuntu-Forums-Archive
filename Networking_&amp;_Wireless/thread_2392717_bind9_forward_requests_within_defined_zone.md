---
title: "bind9 forward requests within defined zone"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by ralen1225 on 2018-05-24
I am happily using bind9 on my ubuntu setup but I would like to be able to refer unknown subdomain requests to an outside server.
For example, if my domain is home.com (it's not) and I have entries in my local zone file to cover my local machines and services and I also have other outside services which are covered by another domain server, I would like my local name server to request the info from the outside server for anything it does not have entries for.

---

### Post by Doug S on 2018-05-24
Did you try setting forwarders in your etc/bind/named.conf.options file? See also the [Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/dns-configuration.html").

---

### Post by ralen1225 on 2018-05-24
Yes. That only forwards for domains that are not included in the bind zones.

---

### Post by SeijiSensei on 2018-05-24
Duplicate the external records in the local zone file. It's not possible to do what you want without using subdomains. You could put your local machines in a local.example.com subdomain and place an NS record for that subdomain that points to your local server. I just have copies of remote records, e.g. the A record for "www.example.com" returns its public address.

---

### Post by ralen1225 on 2018-05-25
I was beginning to suspect that. I was hoping for a more elegant solution. I read through all of the man pages and references I could find.
Thanks

---

