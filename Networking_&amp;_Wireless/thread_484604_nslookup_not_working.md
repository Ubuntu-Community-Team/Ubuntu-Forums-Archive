---
title: "nslookup not working"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by s_raghu20 on 2007-06-26
Hi Folks, 

Have got this strange issue. Not really blocking.. but annoying nonetheless.

I have this laptop... A Dell.. running ubuntu feisty on a disk partition..the other partition (boot point) runs win xp.
I have this Dlink Ethernet router (no wireless), which works as my dhcp server as well. 

My ubuntu is configured to work through dhcp, and works fine for internet usage etc.

However, an nslookup to self (nslookup `hostname`) comes back with this

```

raghav@raghav-ubuntu:~$ nslookup `hostname`
Server:         62.2.24.162
Address:        62.2.24.162#53

** server can't find raghav-ubuntu: NXDOMAIN

raghav@raghav-ubuntu:~$ nslookup google.com
Server:         62.2.24.162
Address:        62.2.24.162#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.187.99

raghav@raghav-ubuntu:~$ 


```

I tried tinkering resolv.conf and restarted network and added a line with my server name there, no good.

when I do a ifconfig -a, I read the following for my adapter
```
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:96:E7:6F  
          inet addr:192.168.0.143  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe96:e76f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7402833 (7.0 MiB)  TX bytes:2191802 (2.0 MiB)
          Interrupt:10 

```
which looks good to me...

then, how come my nslookup doesnot come back good... any body.. please

regards
raghav..

---

### Post by PaulFr on 2007-06-26
nslookup looks for DNS entries in a DNS server (recursively) that translate a domain or a machine inside a domain to an IP address (among other things) - if your hostname has been entered in a DNS server's 'database' somewhere, nslookup or dig will be able to translate your hostname to an IP address successfully. The other part is that the name in that 'database' needs to resolve to an IP address (usually a static IP address).

Usually residential users do not have their own domain or static IP addresses (though there are exceptions :-), so having DNS entries for our machines is not typical. But if you do want a DNS entry for your machine, there are services like DynDNS (see [http://en.wikipedia.org/wiki/Dynamic_DNS](http://en.wikipedia.org/wiki/Dynamic_DNS) for more details) where you can create a domain that resolves to your dynamic IP address. This will mean you need to periodically update that service with your dynamic IP address if it has changed.

---

### Post by s_raghu20 on 2007-06-29
> **PaulFr said:**
> nslookup looks for DNS entries in a DNS server (recursively) that translate a domain or a machine inside a domain to an IP address (among other things) - if your hostname has been entered in a DNS server's 'database' somewhere, nslookup or dig will be able to translate your hostname to an IP address successfully. The other part is that the name in that 'database' needs to resolve to an IP address (usually a static IP address).

Usually residential users do not have their own domain or static IP addresses (though there are exceptions :-), so having DNS entries for our machines is not typical. But if you do want a DNS entry for your machine, there are services like DynDNS (see [http://en.wikipedia.org/wiki/Dynamic_DNS](http://en.wikipedia.org/wiki/Dynamic_DNS) for more details) where you can create a domain that resolves to your dynamic IP address. This will mean you need to periodically update that service with your dynamic IP address if it has changed.

Dear Paul (I guess thats what ur name is),

thanks a lot for your knowledge piece. In fact you are right, I myself had forgotten that i am running on a dhcp thing. However, shouldnt this box (ubuntu 7.04) be running a small little dns server of its own ? I thought that should resolve the name i am looking for. Even if its the same name i am launching the request from.

But, thats not to contest your points. you really have sent me an eye opener. thanks again. :)

regards
raghav..

---

