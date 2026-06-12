---
title: "Unable to resolve non-qualified LAN hostnames registered in our DNS"
date: 2021-07-13
forum: Networking &amp; Wireless
---

### Post by manjushri108 on 2021-07-13
Hello,

We would like to give simple names (non-qualified hostnames without a dot) to our main servers on our LAN, let's say for example fooserver, but we have problems to resolve these names with Ubuntu.

We have registered fooserver (the name we want) and fooserver.com (a name we don't want but that will be helpful to describe our issue) in our DNS (which is a service running on our main router).

My client is a laptop on Ubuntu 21.04. This laptop can resolve fooserver.com but not fooserver (and this is the problem). So it looks like the name resolution works only with qualified hostnames.

Here are a few commands I ran that should help to better identify the issue.

Regarding the IP addresses, 10.101.0.1 is our main router (and DNS) and 10.101.0.5 is the expected IP address for fooserver registered in the DNS.

1) nslookup fooserver.com works

```
$ nslookup fooserver.com
Server:        127.0.0.53
Address:    127.0.0.53#53


Non-authoritative answer:
Name:    fooserver.com
Address: 10.101.0.5

```

2) nslookup fooserver doesn't work

```
$ nslookup fooserver   
Server:        127.0.0.53
Address:    127.0.0.53#53


** server can't find fooserver: SERVFAIL

```

3) But nslookup fooserver works when I specify the IP address of the router (which is also our DNS)


```
$ nslookup fooserver 10.101.0.1
Server:        10.101.0.1
Address:    10.101.0.1#53


Name:    fooserver
Address: 10.101.0.5

```

4) The DNS server received from DHCP is however correctly set to 10.101.0.1 as you can see below (I'm connected through WiFi which is Link3):

```
$ systemd-resolve --status
Global
    Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub


Link 2 (enp8s0)
Current Scopes: none
   Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported


Link 3 (wlp7s0)
  Current Scopes: DNS
     Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 10.101.0.1
    DNS Servers: 10.101.0.1

```

So everything looks configured properly and I wonder why it doesn't work.
In particular why 2) doesn't behave like 3) knowing that the DNS server for my WiFi connection is the same as the one explicitly given in 3)?

Thanks.

---

### Post by TheFu on 2021-07-13
a) fooserver.com is a terrible, terrible, name.  LAN FQDN should be fooserver.lan or fooserver.local.  Don't use any TLD unless it is actually a TLD that you own and setup public DNS to access.

b) In the resolv.conf file, a "search" like this is needed:
```
search jdpfu.lan jdpfu.com
```
The setup you choose to manage the resolv.conf should be modified to do that for you.  I use "vim" as my resolv.conf management tool.

If you use something like 
```
search com
```
bad things are likely with resolving internet servers, as you can see.  Review "a" above.

---

### Post by manjushri108 on 2021-07-14
[COLOR=#000000]Thanks for your reply.

Regarding a) fooserver.com was just a temporary and arbitrary example to illustrate the different behaviour of the name resolution in Ubuntu between qualified and non-qualified names. Most importantly this is not the final name we want (we want the non-qualified fooserver name). But ok if you prefer I replaced the example fooserver.com with fooserver.lan in our DNS but the result is the same: I can resolve fooserver.lan but not fooserver (which is what we try to achieve) - see below:[/COLOR]

```
[COLOR=#000000]$ nslookup fooserver.lan[/COLOR]
[COLOR=#000000]Server: 127.0.0.53[/COLOR]
[COLOR=#000000]Address: 127.0.0.53#53[/COLOR]


[COLOR=#000000]Non-authoritative answer:[/COLOR]
[COLOR=#000000]Name: fooserver.lan[/COLOR]
[COLOR=#000000]Address: 10.101.0.5

[/COLOR][COLOR=#000000]$ nslookup fooserver[/COLOR]
[COLOR=#000000]Server: 127.0.0.53[/COLOR]
[COLOR=#000000]Address: 127.0.0.53#53[/COLOR]


[COLOR=#000000]** server can't find fooserver: SERVFAIL[/COLOR]
```


[COLOR=#000000]I also registered fooserver.local in the DNS and surprisingly it doesn't work:[/COLOR]

```
[COLOR=#000000]$ nslookup fooserver.local[/COLOR]
[COLOR=#000000]Server: 127.0.0.53[/COLOR]
[COLOR=#000000]Address: 127.0.0.53#53[/COLOR]


[COLOR=#000000]** server can't find fooserver.local: SERVFAIL[/COLOR]
```

[COLOR=#000000]So is the problem related to this?
[/COLOR]
[COLOR=#000000]My /etc/resolv.conf has only 3 lines (ignoring the header comments):
[/COLOR]
```
[COLOR=#000000]nameserver 127.0.0.53[/COLOR]
[COLOR=#000000]options edns0 trust-ad[/COLOR]
[COLOR=#000000]search .[/COLOR]
```

If I add .local in the search line, it doesn't fix the problem.
But if I replace the name server from 127.0.0.53 to 10.101.0.1, it works (with both fooserver and fooserver.local):

```
$ nslookup fooserver
Server:        10.101.0.1
Address:    10.101.0.1#53


Name:    fooserver
Address: 10.101.0.5

$ nslookup fooserver.local
Server:        10.101.0.1
Address:    10.101.0.1#53


Name:    fooserver.local
Address: 10.101.0.5

```

However this is not an ideal solution as we have several WiFi connections (public, staff department 1, 2, etc...) with different DHCP settings (and different DNS IPs).

Do you see an alternative solution to successfully resolve fooserver without changing the name server in resolv.conf?

---

### Post by TheFu on 2021-07-14
In a LAN environment, it is best to use DNS and there is little reason to run a local caching DNS.  
I don't think this is valid inside resolv.conf:
```
search .
```

Did you change the settings in the resolvconf or systemd-resolved config files?

BTW, nslookup has been deprecated over 5 yrs, perhaps 10 yrs.  dig is the ugly replacement.

.local is what mdns uses. That's controlled by avahi on Ubuntu systems, if it is running. Generally, Ubuntu Server doesn't install avahi, but I think all desktop versions do.

```
$ nslookup [COLOR="#008000"]hadar[/COLOR]
Server:         172.22.22.80
Address:        172.22.22.80#53

Name:   **hadar.jdp.foo**
Address: 172.22.22.6

$ more /etc/resolv.conf 
nameserver 172.22.22.80
nameserver 172.22.22.81
search jdp.foo jdpfu.com
```

I don't use resolvconf nor systemd-resolved. Both are disabled, masked. What would be the point when there are DNS servers on the LAN caching requests for all clients?

My DNS servers are DNS filters too. They run the pi-hole software. I used to run BIND and when my network was smaller, I used ansible to maintain the /etc/hosts files across the systems.  Centralized management makes life great or terrible. Just depends on how good the person doing the setup is with details.

---

### Post by manjushri108 on 2021-07-14
I don't want a local DNS cache neither on my machine as my LAN DNS server already has a cache.
Not sure if I have one and how to disable it.

But I guess problems like mine where a name can't be resolved are not caused by a cache anyway (if a name is not present in the cache, the system should finally request the LAN DNS).

I confirm avahi is listed in my running processes.

My laptop has no default domain name.
Would that explain the "search ." in my resolv.conf?

Does your machine has jdp.foo as default domain name?
And is it why when you try to resolve a non-qualified name such as hadar it actually resolves hadar.jpd.foo?
But I would like a solution that doesn't require a default domain name.

I disabled mDNS (and also LLMNR) as you can see below:

```
$ systemd-resolve --status
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub


Link 2 (enp8s0)
Current Scopes: none
     Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported


Link 3 (wlp7s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 10.101.0.1
       DNS Servers: 10.101.0.1

```

but this doesn't solve the problem.

I'm happy to use dig instead of nslookup, but this leads to the same results (resolution works with fooserver.lan but not fooserver):

```
$ dig fooserver.lan


; <<>> DiG 9.16.8-Ubuntu <<>> fooserver.lan
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61711
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;fooserver.lan.            IN    A


;; ANSWER SECTION:
fooserver.lan.        0    IN    A    10.101.0.5


;; Query time: 8 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Jul 14 15:34:39 BST 2021
;; MSG SIZE  rcvd: 58


$ dig fooserver


; <<>> DiG 9.16.8-Ubuntu <<>> fooserver
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 65422
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;fooserver.            IN    A


;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Jul 14 15:34:43 BST 2021
;; MSG SIZE  rcvd: 38
```

Why do I have a status: NOERROR with fooserver.lan and status: SERVFAIL with fooserver?

---

### Post by TheFu on 2021-07-14
That's a question for the DNS server admin. Besides the search, there isn't much a client can control.

Disable systemd-resolve.  I would "mask" it too.  Then you can manually modify the non-symlinked /etc/resolv.conf as you like.  I find that is easier than dealing with terrible "automatic" tools that don't work well (systemd-resolved or resolvconf).  The problem they are trying it correct isn't a problem I've ever had.  I have no idea why systemd-resolved would put **search .** into the config.  Just another example of "fixing" things that weren't broke, IMHO.

Be 100% certain that you replace any symbol link for /etc/resolv.conf with a real file with these permissions, owner, group.
-rw-r--r-- 1 root root 70 Jul  3 04:31 /etc/resolv.conf


BTW, 
```
$ systemd-resolve --status
Failed to get global data: Unit dbus-org.freedesktop.resolve1.service is masked.
```
That's how systemd-resolved should should appear if it is disabled and won't be restarted at reboot.  

AND
```
$ resolvectl query hadar
hadar: resolve call failed: Unit dbus-org.freedesktop.resolve1.service is masked.

```
is how resolvconf should appear when disabled and won't be restarted a reboot too.

---

### Post by manjushri108 on 2021-07-16
Thanks but I don't want to go to the direction you are suggesting, sorry.

I want to comply to the default Ubuntu system as much as possible for long term administration reason.
So I prefer to understand the default behaviour and see what is wrong with my settings (or eventually report a bug in Ubuntu if the problem is on Ubuntu).

I think "search ." is correct for clients that have no default local domain like in my case.
The dot alone refers to the DNS root domain and also can be used to indicate a full stop [as explained here]("https://unix.stackexchange.com/questions/412881/what-is-root-domain").

So in your case, because your client machine seems to have jdp.foo as default domain name, it should be listed in your "search jdp.foo" of etc/resolv.conf and automatically append to resolve any non qualified name.
That's why when you typed nslookup hadar it was automatically translated to nslookup hadar.jdp.foo

In a client machine like mine with no default domain name, because of the "search ." nslookup fooserver will automatically be translated to nslookup fooserver. (with a stop) which is actually correct according to the previous link.

And I continue to think that it is a Ubuntu problem and not a DNS problem because as I said it works when I explicitly force the resolution directly to my local DNS by giving its IP, and the result is the same with the dot stop as you can see below:

```
$ nslookup fooserver.
Server:        127.0.0.53
Address:    127.0.0.53#53


** server can't find fooserver: SERVFAIL


$ nslookup fooserver. 10.101.0.1
Server:        10.101.0.1
Address:    10.101.0.1#53


Name:    fooserver
Address: 10.101.0.5

```

The stop can also be explicitly used on client machine like yours with a default domain name to prevent the default behaviour and ask the resolution of the non qualified name alone (without appending the default domain name).
So you may be able to reproduce my issue on your machine by running:

```
$ nslookup hadar.
```

Can you please report the result of this command?

---

