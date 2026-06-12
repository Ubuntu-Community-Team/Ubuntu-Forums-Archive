---
title: "DHCP settings with DHCP client ???"
date: 2017-04-30
forum: Networking &amp; Wireless
---

### Post by Vincen_PUJOL on 2017-04-30
Hi

I' killing my head with that weird issue :( My Ubuntu server 16.04.2 is in DHCP (don't ask me why, it's due to network it's plugged to !). When it gets IP from DHCP server it also retrieves a search domain and DHCP servers.
I don't want the ones given by DHCP server so I added in /etc/dhcp/dhclient.conf these two directives:

```
supersede domain-name "myowndomainhere.com";
supersede domain-name-servers 127.0.0.1, 62.210.16.6, 62.210.16.7;
```

But once reloaded the network interface or restarted the system, it keeps only the first DNS listed (127.0.0.1) and not the other ones ! I have double checked syntax and still not understanding the problem :( any ideas ?

Thanks

Vincèn

---

### Post by Doug S on 2017-05-02
My notes on this are a little old, but...

You could try using "prepend" instead of "supersede", and in your license request do not ask for "domain-name-servers". For example, here is a segment of my "/etc/dhcp/dhclient.conf" file (my "prepend"s are commented out now, because I do it a different way):
```
#send host-name "mail";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 192.168.111.1;
# No, use /etc/default/bind9 to set the DNS
#prepend domain-name-servers 127.0.0.1;

supersede host-name "mail";
supersede domain-name "mydomain.com";
supersede domain-search "mydomain.com";

#request subnet-mask, broadcast-address, time-offset, routers,
#       domain-name, domain-name-servers, domain-search, host-name,
#       netbios-name-servers, netbios-scope, interface-mtu,
#       rfc3442-classless-static-routes, ntp-servers;

request subnet-mask, broadcast-address, time-offset, routers;

```

---

### Post by Vincen_PUJOL on 2017-05-03
> **Doug S said:**
> My notes on this are a little old, but...
You could try using "prepend" instead of "supersede", and in your license request do not ask for "domain-name-servers". For example, here is a segment of my "/etc/dhcp/dhclient.conf" file (my "prepend"s are commented out now, because I do it a different way):
Thanks for your suggestions and it looks to be what I tried already in the past !! here is what I have now with your modifications:
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
	interface-mtu,rfc3442-classless-static-routes, ntp-servers;
supersede host-name "pro-2.mydomain.com";
supersede domain-name "mydomain.com";
supersede domain-search "mydomain.com";
supersede domain-name-servers 127.0.0.1, 62.210.16.6, 62.210.16.7;
```
After reboot I have well the mydomain.com in resolv.conf and only the first DNS listed (127..) but not other ones :( Killing my head on that problem....

---

