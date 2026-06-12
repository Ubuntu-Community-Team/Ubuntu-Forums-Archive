---
title: "DnsCrypt on mobile broadband connection"
date: 2017-06-05
forum: Networking &amp; Wireless
---

### Post by Dedalus1983 on 2017-06-05
I followed the instruction here:
[http://www.linuxandubuntu.com/home/how-to-encrypt-dns-traffic-in-linux-using-dnscrypt](http://www.linuxandubuntu.com/home/how-to-encrypt-dns-traffic-in-linux-using-dnscrypt)

to install and configure dnscrypt on Ubuntu-gnome 17.04. When using a wireless/ethernet connection, everything's all right.

Since I mostly use mobile broadband connections (i.e. hardware huawei usb modem), I can't manage to make it work.
I changed the connection I'm using in /etc/NetworkManager/system-connections/...
Relevant part:

```
[ipv4]
dns=127.0.0.2;
dns-search=
method=auto
ignore-auto-dns=true
```

After doing this, I can see a change, doing
```
nmcli dev show | grep DNS
```

output:
```
IP4.DNS[1]:                             127.0.0.2
```

(while before I saw other 2 DNS ips I didn't set).
Anyway, seems that somehow is not working, because if I take the online test here: [http://opendns.org/welcome](http://opendns.org/welcome) 
The test fails...
What's going on? Maybe the ISP provider forcing some redirect?

Thanks.

---

### Post by Dedalus1983 on 2017-06-08
For people with the same problem..

I found the best thing to read the implementation specific manual, that is, not just DNScrypt protocol but the very dnscrypt-proxy here:
[https://github.com/jedisct1/dnscrypt-proxy/wiki](https://github.com/jedisct1/dnscrypt-proxy/wiki)

So, looking at config file in
/etc/dnscrypt-proxy/dnscrypt-proxy.conf

Relevant section to modify:

```
ResolverName cisco
LocalAddress 127.0.2.1:53
```

Then back to system connections, put 127.0.2.1 as dns and ignore isp dns.
It works!! :p:guitar::p

---

