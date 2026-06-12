---
title: "How do I make DNS server settings persistent?"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Giardap on 2006-11-01
Hi,

I'm running Firefox in Ubuntu 6.06. Browsing was painfully slow. A friend pointed me to the networking section and the DNS server tab. He said that the machine was set up to refer to the modem to resolve addresses, and that if I deleted this reference and inserted the DNS server IP address of my ISP that would resolve things. It did and browsing was lightning fast.

However when I re-boot the machine everything reverts to where it was and I have to edit the DNS tab again to achieve fast browsing.

Anybody know how to make the changes persist? Thanks.

---

### Post by Swab on 2006-11-01
> **Giardap said:**
> Hi,

I'm running Firefox in Ubuntu 6.06. Browsing was painfully slow. A friend pointed me to the networking section and the DNS server tab. He said that the machine was set up to refer to the modem to resolve addresses, and that if I deleted this reference and inserted the DNS server IP address of my ISP that would resolve things. It did and browsing was lightning fast.

However when I re-boot the machine everything reverts to where it was and I have to edit the DNS tab again to achieve fast browsing.

Anybody know how to make the changes persist? Thanks.

There may well be a better way, but you can give yourself a static IP address and that should fix it.  The reason you are losing the settings is probably because you are getting the DNS settings via DHCP.

---

### Post by Joe_CoT on 2006-11-01
There might be an easier way to do this, but I'm going to refer you to the resolv.conf file. From a terminal:

```

sudo gedit /etc/resolv.conf

```

You can instead use kate if in kde, or nano/vi if you're familiar with the console.

in there, add this line, and remove any other name servers
```

nameserver x.x.x.x
```
where x.x.x.x is the ip address of the dns server. you can add multiple nameserver lines like this if there's multiple dns servers.

Assuming you're using dhcp, do this as well:

```
 sudo gedit /etc/dhcp3/dhclient.conf
```

Change the prepend line to read
```

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

```

With your own nameservers. Now, even though dhcp will override your resolv.conf, it'll at least override with the right ones. :-D

---

### Post by Giardap on 2006-11-01
Thanks Joe_CoT - that worked for me.

---

