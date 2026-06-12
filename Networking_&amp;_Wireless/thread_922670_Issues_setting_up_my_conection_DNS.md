---
title: "Issues setting up my conection DNS"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by fencer on 2008-09-17
I was having troubles with my conection so I called to the phone company and they told me to use new DNS: 

so I went to network properties and tried to change them from there so it was like this: 

[IMG]http://files.tulinux.es/Pantallazo.png[/IMG]

and I changed it to this:

[IMG]http://files.tulinux.es/Pantallazo-1.png[/IMG]

but after a while it always turn back into the older DNS, I tried editing resolv.conf but I get the same result, all I want is to set those new DNSby default
If this helps a lil, Im using local cache

---

### Post by Iowan on 2008-09-17
I presume you use DHCP to get IP Address from your ISP.  Edit **/etc/dhcp3/dhclient.conf** (I like **sudo nano /etc/dhcp3/dhclient.conf**) Find the line:```
#prepend domain-name-servers 127.0.0.1;
``` Uncomment it (remove the #) and include your new DNS servers. You could also remove the "domain-name-servers," from the "request" line.

---

### Post by fencer on 2008-09-17
ok now my file looks something like this

```
#supersede domain-name “fugue.com home.vix.com”;
prepend domain-name-servers 127.0.0.1, 200.35.65.3, 200.35.65.4;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope;
```

is that ok???
because I havent seen any changes so far, (let me restart to see the results)

Edit: It worked like a charm, thx a lot for the help :-)

---

