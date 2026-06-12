---
title: "How to find the FQDN of a local IP ?"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2014-08-26
Hi,

My ISP provides a web interface to login to my broadband account. There are 2 addresses which opens the same page.

[http://10.10.201.1/24online/servlet/E24onlineHTTPClient](http://10.10.201.1/24online/servlet/E24onlineHTTPClient)

[http://172.16.0.1/24online/webpages/client.jsp?fromlogout=true](http://172.16.0.1/24online/webpages/client.jsp?fromlogout=true)

These two pages loads fine from my PC but I cant open them on my phone no matter which browser I choose.

I made a horrible mistake of buying a Java phone, Nokia Asha 501. The only browser that doesn't use a proxy is

QQ Browser but even that is failing to open the page no matter which ip I use.

After some searching I found [this page]("http://stackoverflow.com/questions/8651043/android-browser-hostnames-does-not-get-resolved-if-domain-name-is-not-appended") which says most mobile browsers can only open FQDNs.

I tried the following to find out the FQDN but nothing worked :

```
$ host 172.16.0.1
Host 1.0.16.172.in-addr.arpa. not found: 3(NXDOMAIN)
[happy@one ~]$ nslookup 172.16.0.1
Server:        192.168.0.1
Address:    192.168.0.1#53

** server can't find 1.0.16.172.in-addr.arpa.: NXDOMAIN


```


```
$ host 10.10.201.1
Host 1.201.10.10.in-addr.arpa. not found: 3(NXDOMAIN)
[happy@one ~]$ nslookup 172.16.0.1
Server:        192.168.0.1
Address:    192.168.0.1#53

** server can't find 1.0.16.172.in-addr.arpa.: NXDOMAIN 
```

```
 [happy@one ~]$ nslookup 10.10.201.1
Server:        192.168.0.1
Address:    192.168.0.1#53

** server can't find 1.201.10.10.in-addr.arpa.: NXDOMAIN


```

```
$ nslookup 172.16.0.1
Server:        192.168.0.1
Address:    192.168.0.1#53

** server can't find 1.0.16.172.in-addr.arpa.: NXDOMAIN

```

```
$ nmblookup -A 10.10.201.1
Can't load /etc/samba/smb.conf - run testparm to debug it
Looking up status of 10.10.201.1
No reply from 10.10.201.1
```

```
$ nmblookup -A 172.16.0.1
Can't load /etc/samba/smb.conf - run testparm to debug it
Looking up status of 172.16.0.1
No reply from 172.16.0.1
```

```
$ ping 172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
64 bytes from 172.16.0.1: icmp_seq=1 ttl=63 time=1.30 ms
64 bytes from 172.16.0.1: icmp_seq=2 ttl=63 time=1.07 ms
64 bytes from 172.16.0.1: icmp_seq=3 ttl=63 time=2.65 ms
64 bytes from 172.16.0.1: icmp_seq=4 ttl=63 time=3.09 ms
^C
--- 172.16.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.073/2.032/3.096/0.861 ms
```

```
$ ping  10.10.201.1
PING 10.10.201.1 (10.10.201.1) 56(84) bytes of data.
64 bytes from 10.10.201.1: icmp_seq=1 ttl=63 time=1.42 ms
64 bytes from 10.10.201.1: icmp_seq=2 ttl=63 time=1.23 ms
64 bytes from 10.10.201.1: icmp_seq=3 ttl=63 time=1.05 ms
64 bytes from 10.10.201.1: icmp_seq=4 ttl=63 time=1.70 ms
^C
--- 10.10.201.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 1.053/1.351/1.703/0.244 ms

```

What else can I try ?

---

### Post by steeldriver on 2014-08-26
Both 10.x.x.x and 172.16.x.x are [private network ranges]("http://en.wikipedia.org/wiki/Private_network") - afaik addresses in them only have significance inside your LAN/WAN i.e. no public DNS record is going to resolve to such an address. Basically they belong to your modem rather than to the ISP's public address range.

You could possibly try adding an entry to the phone's hosts file if you know how to access it?

---

### Post by linuxyogi on 2014-08-26
> **steeldriver said:**
> Both 10.x.x.x and 172.16.x.x are [private network ranges]("http://en.wikipedia.org/wiki/Private_network") - afaik addresses in them only have significance inside your LAN/WAN i.e. no public DNS record is going to resolve to such an address. Basically they belong to your modem rather than to the ISP's public address range.

You could possibly try adding an entry to the phone's hosts file if you know how to access it?

If no command can tell FQDN of a private IP address then I guess I will have to cope with this.

In case of Android, Google helps to some extent but hardly any info is available about Java phones.

I logged into my router's web interface and searched if there is any place for adding DNS records but there is 

none.  I have no idea where my phone's host file is.

---

### Post by SeijiSensei on 2014-08-27
If your router acts as your DNS server, you might be able to create hostnames for those machines and add them to the router's DNS table.  You still won't be able to connect to them from outside the local network, of course.

---

### Post by linuxyogi on 2014-08-27
> **SeijiSensei said:**
> If your router acts as your DNS server, you might be able to create hostnames for those machines and add them to the router's DNS table.  You still won't be able to connect to them from outside the local network, of course.

The reason I was searching for the FQDN of my ISP's login server doesn't exist anymore. I called their customer care and explained my situation and they have enabled Auto Login for my account.
Its means there is no idle timeout for this account and it becomes an always on connection unless I visit that login page and logout.

I tried your suggestion but my router's firmware has no place for adding DNS entries.

---

### Post by SeijiSensei on 2014-08-27
Have any Linux machines on this network that can run BIND?  You could set up an internal DNS server that way.

---

### Post by linuxyogi on 2014-08-27
> **SeijiSensei said:**
> Have any Linux machines on this network that can run BIND?  You could set up an internal DNS server that way.

No, I got only one desktop and a phone connected via Wi-Fi. I don't need that page anymore. I switch on the router and I am connected.

---

