---
title: "Bind - One Domain with multiple hostnames - Creating a dns server on the 2nd server?"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by rktmedia on 2014-03-21
Hi, my name is Damian, im new on the forums.
Im having some issues trying to setup my 2nd server. This is the story:

I have domain.com hosted in GoDaddy. I setup ns1 & ns2 pointing to the server-ip-1 and ns3 & ns4 pointing to server-ip-2 on the hostname manager of godaddy.

In [COLOR=#ff0000]server 1[/COLOR] I host "domain.com". It has bind9 working fine, with +60 domains on it without issue. I created the following zones:

**db.domain.com**

```
$ORIGIN domain.com.
$TTL 86400 ; 1 dia
@ IN SOA ns1.domain.com. eaf12.domain.com. (
   2007062001
   28800
   3600
   604800
   38400
);


@               IN      NS      ns1.domain.com.
@               IN      NS      ns2.domain.com.


domain.com. IN      NS      ns1.domain.com.
ns1             IN      A       <server-1-ip>
ns2             IN      A       <server-1-ip>
www             IN      A       <server-1-ip>
ftp             IN      A       <server-1-ip>
mail            IN      A       <server-1-ip>
sql             IN      A       <server-1-ip>
host01          IN      A       <server-1-ip>




```

**Reverse Zone:**

```
$ORIGIN 00.00.192.in-addr.arpa.
$TTL 86400     ; 1 dia
@       IN      SOA     host01        postmaster (
        1      ; serie
        6H     ; refresco (6 horas)
        1H     ; reintentos (1 hora)
        2W     ; expire (2 semanas)
        3H     ; mínimo (3 horas)
)
       NS      host01.domain.com.
       NS      ns1.domain.com.
       NS      ns2.domain.com.
00      PTR     host01.domain.com.

```

**named.conf.local:**

```
zone "domain.com" {
  type master;
  file "db.domains.com";
};


zone "00.00.192.in-addr.arpa" {
  type master;
  file "db.192.00.00";
};

```

OK, until here there is no problem with the server. It process all request and serve the sites without problem.

But, Im trying to setup a [COLOR=#ff0000]second dns server[/COLOR] on eaf12.domain.com in another server & ip, and these are the setup files:

**db.eaf12.domain.com**

```
$ORIGIN eaf12.domain.com.$TTL 86400 ; 1 dia
@ IN SOA ns3.domain.com. eaf12.domain.com. (
   2007062001
   28800
   3600
   604800
   38400
);


@               IN      NS      ns3.domain.com.
@               IN      NS      ns4.domain.com.


eaf12.domain.com. IN      NS      ns3.domain.com.
ns3             IN      A       <server-2-ip>
ns4             IN      A       <server-2-ip>
www             IN      A       <server-2-ip>
```

**Reverse zone:**

```
$ORIGIN 01.01.176.in-addr.arpa.$TTL 86400     ; 1 dia
@       IN      SOA     eaf12        postmaster (
        1      ; serie
        6H     ; refresco (6 horas)
        1H     ; reintentos (1 hora)
        2W     ; expire (2 semanas)
        3H     ; mínimo (3 horas)
)
       NS      eaf12.domain.com.
       NS      ns3.domain.com.
       NS      ns4.domain.com.
01      PTR     eaf12.domain.com.
```

**named.conf.local**

```
zone "eaf12.domains.com" {  type master;
  file "db.eaf12.domain.com";
};


zone "01.01.176.in-addr.arpa" {
  type master;
  file "db.176.01.01";
};
```

Of course the 2nd server is not working. I have 4 domains on them pointing to the ns3&ns4 nameservers created in Godaddy pointing to the 2nd server ip and they didnt resolve.

I know something is wrong on the 2nd setup of BIND. Im a total newbie with it, I faced to setup the 1st server with success but the 2nd since its using a subdomain as hostname I cant make it work.

Any help or comment will be really appreciated.

Thanks in advance.
Damian

---

### Post by rktmedia on 2014-03-21
_***UPDATE:***_

I disabled the "forwarders" in /etc/bind/named.conf.options and it works.
Both servers are resolving fine, serving the domains hosted on them.

---

