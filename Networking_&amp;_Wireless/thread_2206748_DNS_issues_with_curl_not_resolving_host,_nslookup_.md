---
title: "DNS issues with curl not resolving host, nslookup and dig work fine"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by rwarasaurus on 2014-02-20
I dont know why curl is failing:

nslookup works fine


```

[user@box ~] nslookup project.staging.local
Server:        192.168.30.201
Address:    192.168.30.201#53


Name:    project.staging.local
Address: 192.168.30.8

```


dig works fine


```

[user@box ~] dig A project.staging.local


; <<>> DiG 9.8.1-P1 <<>> A project.staging.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42724
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;project.staging.local.    IN    A


;; ANSWER SECTION:
project.staging.local. 3600    IN    A    192.168.30.8


;; Query time: 0 msec
;; SERVER: 192.168.30.201#53(192.168.30.201)
;; WHEN: Thu Feb 20 17:17:54 2014
;; MSG SIZE  rcvd: 58

```


curl fails


```

[user@box ~] curl -v http://project.staging.local/
* getaddrinfo(3) failed for project.staging.local:80
* Couldn't resolve host 'project.staging.local'
* Closing connection #0
curl: (6) Couldn't resolve host 'project.staging.local'

```


sysctl settings


```

[user@box ~] sudo sysctl -p
net.ipv4.ip_forward = 1

```


```

[user@box ~] cat /etc/resolv.conf 
nameserver 192.168.30.201
nameserver 192.168.30.203

```


```

[user@box ~] cat /etc/network/interfaces 
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.31.52
    netmask 255.255.255.0
    network 192.168.31.0
    broadcast 192.168.31.255
    gateway 192.168.31.254
    dns-nameservers 192.168.30.201 192.168.30.203

```


What am I missing?

---

### Post by rwarasaurus on 2014-02-21
Resolved!

Changed /etc/host.conf like so

```

#order hosts,bind
order bind,hosts

```

And /etc/nsswitch.conf

```

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:		dns files

```

---

### Post by rwarasaurus on 2014-02-21
Something still wasn't right, looking at the /var/log/daemon.log was showing "error (no valid RRSIG) resolving"

Adding this in /etc/bind/named.conf.options fixed the lookup issues.

```

        dnssec-enable no;
        dnssec-validation no;

```

---

