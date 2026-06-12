---
title: "DHCP Prepending Name Servers"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by SAH62 on 2015-01-21
[FONT=courier new][SIZE=3][COLOR=#000000]I'[SIZE=2]m running Ubuntu 14.04 on a Dell 2950. I have theselines in my dhclient.conf file (the second IP address is just an example):[/SIZE][/COLOR][/SIZE]

```
[SIZE=2][COLOR=#000000]prepend domain-name-servers 127.0.0.1, 1.2.3.4;[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]request subnet-mask, broadcast-address, time-offset,routers,[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]domain-name, domain-name-servers, domain-search, host-name,[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]dhcp6.name-servers, dhcp6.domain-search,[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]netbios-name-servers, netbios-scope, interface-mtu,[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]rfc3442-classless-static-routes,ntp-servers,[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]dhcp6.fqdn,dhcp6.sntp-servers;[/COLOR][/SIZE]
```

[SIZE=2][COLOR=#000000]I would expect this to prepend name server entries for 127.0.0.1 and 1.2.3.4 to the list of server(s) specified by my DHCP server inmy resolv.conf file. That's not what happens, though - I get only this in resolv.conf:[/COLOR][/SIZE]
 
```
[COLOR=#000000]nameserver 127.0.0.1[/COLOR]
```
[SIZE=2]
Am I missing something? What should I be doing to get both name server addresses added to resolv.conf?

I've also tried listing them /etc/network/interfaces. Same result.[/SIZE][/FONT]

---

### Post by Doug S on 2015-01-21
I can not help much, as I do not recall the specific details. All I can say is that I did try prepend once, but then commented it out with a note:```
#prepend domain-name-servers 192.168.111.1;
# No, use /etc/default/bind9 to set the DNS
#prepend domain-name-servers 127.0.0.1;
```However, I do use supersede with good results

---

### Post by SAH62 on 2015-01-22
> **Doug S said:**
> I can not help much, as I do not recall the specific details. All I can say is that I did try prepend once, but then commented it out with a note:```
#prepend domain-name-servers 192.168.111.1;
# No, use /etc/default/bind9 to set the DNS
#prepend domain-name-servers 127.0.0.1;
```However, I do use supersede with good results

I've done some other reading that suggests that prepend doesn't work the way it would appear, and yes, one option is to get your DNS server to register itself. BIND can do that, but I'm using PowerDNS. I haven't been able to find a way to get PowerDNS to do that. There's good info here:

[http://askubuntu.com/questions/239169/how-to-edit-etc-resolv-conf-on-ubuntu-12-04](http://askubuntu.com/questions/239169/how-to-edit-etc-resolv-conf-on-ubuntu-12-04)

---

