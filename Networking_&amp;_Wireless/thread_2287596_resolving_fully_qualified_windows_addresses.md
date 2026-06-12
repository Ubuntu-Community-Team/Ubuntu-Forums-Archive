---
title: "resolving fully qualified windows addresses?"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by ncage on 2015-07-20
I just installed 14.04 LTS tonight. Ubuntu is have issues resolving fully qualified windows machines on my internal network. First of all i'm running an active directory domain. The 1st nameserver in the list is my internal dns server (windows).  For example:

Domain Name: mydomain.com
MachineName: win1

Fully qualified name: win1.mydomain.com

output of 'dig +short win1.mydomain.com'
192.168.0.1

output of 'ping win1.mydomain.com'
ping: unknown host win1.mydomain.com

pinging 192.168.0.1 directly works fine

I've did some searching around and most people that are on workgroups hence they don't have an internal dns server that can resolve (so they need WINS support). I don't of course. Sure if i wanted to be able to reference machines by their shorted name 'win1' then i would. What gives?

---

### Post by papibe on 2015-07-20
Hi ncage.

'dig' goes directly to the DNS server, and ask the records.

'ping' uses the rules on /etc/nsswitch.conf to resolve an address. They usually include DNS, but they may be set incorrectly, or with a different priority.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
cat /etc/resolv.conf 

nm-tool 

cat /etc/nsswitch.conf
```
Regards.

---

### Post by ncage on 2015-07-20
> **papibe said:**
> Hi ncage.

'dig' goes directly to the DNS server, and ask the records.

'ping' uses the rules on /etc/nsswitch.conf to resolve an address. They usually include DNS, but they may be set incorrectly, or with a different priority.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
cat /etc/resolv.conf 

nm-tool 

cat /etc/nsswitch.conf
```
Regards.

Hi and thanks for the reply. Sure  here goes:
**cat /etc/resolve.conf**
nameserver 127.0.1.1

**nm-tool**
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:1B:21:52:56:D8


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.146
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.40
    DNS:             208.67.222.222
    DNS:             208.67.220.220



[B]cat /etc/nsswitch.conf
[/B]passwd:         compat
group:          compat
shadow:         compat


hosts:          files mdns4_minimal [NOTFOUND=return] dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

---

### Post by papibe on 2015-07-20
Thanks.

A couple of observations:

Your DHCP server is giving the clients 3 DNS addresses:
```
DNS: 192.168.0.40
DNS: 208.67.222.222
DNS: 208.67.220.220
```
When a client have a list like that, it would try to balance its requests to all servers. This would result in attempting 2 out of 3 times to use OpenDNS servers. These servers do not know your domain, nor your internal machines. They would reply 'unknown host' to requests to resolve local names.

If your DNS server (192.168.0.40), is a forwarding server (not relaying), it would be better to use is as the only local DNS.

Also, your DHCP server is not giving the psudo local domain 'mydomain.com' to its clients. This would not allow them to resolve short names like just win1, or any other simple hostnames. This assuming the DHCP service it's updating the leases to the DNS server.

Does that help? Let us know if you have more questions, or need more help setting up your network.
Regards.

---

### Post by ncage on 2015-07-20
> **papibe said:**
> Thanks.

A couple of observations:

Your DHCP server is giving the clients 3 DNS addresses:
```
DNS: 192.168.0.40
DNS: 208.67.222.222
DNS: 208.67.220.220
```
When a client have a list like that, it would try to balance its requests to all servers. This would result in attempting 2 out of 3 times to use OpenDNS servers. These servers do not know your domain, nor your internal machines. They would reply 'unknown host' to requests to resolve local names.

If your DNS server (192.168.0.40), is a forwarding server (not relaying), it would be better to use is as the only local DNS.

Also, your DHCP server is not giving the psudo local domain 'mydomain.com' to its clients. This would not allow them to resolve short names like just win1, or any other simple hostnames. This assuming the DHCP service it's updating the leases to the DNS server.

Does that help? Let us know if you have more questions, or need more help setting up your network.
Regards.

Thanks for the help. The first thing i tried was to get rid of the 2 & 3 dns server (opendns). That didnt' work though. Still can't ping win1.mydomain.com. I did find in my dhcp server where i can set the domain. That did allow me to ping the short name "win1".

The reason i had 2 & 3 dns server was in case my local dns server went down (which has happened before). At least the other PCs on my network could get internet connectivity. I never realized they would ever hit 2 & 3 dns servers. I thought that would only happened if the primary dns server went down

---

### Post by ncage on 2015-07-21
Bump....
anyone else have any ideas on how t get full name resolution to work 'win1.mydomain.com'?

---

### Post by papibe on 2015-07-21
Let's test your DNS server configuration.

Could you run these commands on a client machine, and post back the output?
```
nslookup win1

nslookup win1.mydomain.com

nslookup 192.168.0.1

dig win1

dig win1.mydomain.com

dig -x 192.168.0.1

dig +nssearch mydomain.com

dig +nssearch ubuntuforums.org
```
I can't help you with the details on how to set up your DNS server in Windows (I'm only familiar with bind in Linux). However, may be we can discover where the configuration errors are. Also, another people may pitch in after seeing these tests.

Regards.

---

### Post by ncage on 2015-07-22
> **papibe said:**
> Let's test your DNS server configuration.


Could you run these commands on a client machine, and post back the output?
```
nslookup win1


nslookup win1.mydomain.com


nslookup 192.168.0.1


dig win1


dig win1.mydomain.com


dig -x 192.168.0.1


dig +nssearch mydomain.com


dig +nssearch ubuntuforums.org
```
I can't help you with the details on how to set up your DNS server in Windows (I'm only familiar with bind in Linux). However, may be we can discover where the configuration errors are. Also, another people may pitch in after seeing these tests.


Regards.


**nslookup win1**


Server: 192.168.0.39
Address: 192.168.0.39


name: win1.mydomain.com
Address 192.168.0.1


**nslookup 192.168.0.1:**
Server:        192.168.0.39
Address:    192.168.0.39#53


Non-authoritative answer:
*** Can't find 1.0.168.192.in-addr.arpa.: No answer


Authoritative answers can be found from:
1.0.168.192.in-addr.arpa
    origin = localhost
    mail addr = nobody.invalid
    serial = 1
    refresh = 600
    retry = 1200
    expire = 604800
    minimum = 1080


**dig win1:**
; <<>> DiG 9.9.5-3ubuntu0.3-Ubuntu <<>> win1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 52914
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;win1.                IN    A


;; Query time: 0 msec
;; SERVER: 192.168.0.39#53(192.168.0.39)
;; WHEN: Wed Jul 22 19:14:41 CDT 2015
;; MSG SIZE  rcvd: 33




**dig win1.mydomain.com:**
; <<>> DiG 9.9.5-3ubuntu0.3-Ubuntu <<>> win1.mydomain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29425
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;win1.mydomain.com.            IN    A


;; ANSWER SECTION:
win1.mydomain.com.        1200    IN    A    192.168.0.1


;; Query time: 0 msec
;; SERVER: 192.168.0.39#53(192.168.0.39)
;; WHEN: Wed Jul 22 19:16:21 CDT 2015
;; MSG SIZE  rcvd: 59




**dig -x 192.168.0.1:**
; <<>> DiG 9.9.5-3ubuntu0.3-Ubuntu <<>> -x 192.168.0.1
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56609
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;1.0.168.192.in-addr.arpa.    IN    PTR


;; AUTHORITY SECTION:
1.0.168.192.in-addr.arpa. 377    IN    SOA    localhost. nobody.invalid. 1 600 1200 604800 10800


;; Query time: 0 msec
;; SERVER: 192.168.0.39#53(192.168.0.39)
;; WHEN: Wed Jul 22 19:19:07 CDT 2015
;; MSG SIZE  rcvd: 112


**dig +nssearch mydomain.com**:
dig: couldn't get address for 'adserver.mydomain.com': no more


**dig +nssearch ubuntuforums.org**
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.91.139 in 41 ms.
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.94.173 in 107 ms.
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.95.3 in 114 ms.




as an aside the fully qualified domain name works on my Mac


Hopefully this helps?
Regards.

---

### Post by papibe on 2015-07-23
Thanks.

Your DNS is not properly setup.

For starters, it doesn't do reverse looking:
```
Non-authoritative answer:
*** Can't find 1.0.168.192.in-addr.arpa.: No answer

1.0.168.192.in-addr.arpa. 377    IN    SOA    localhost. nobody.invalid. 1 600 1200 604800 10800
```
But most importanly, it doesn't recognize itself as the domain master of 'mydomain.com':
```
dig: couldn't get address for 'adserver.mydomain.com': no more
```
This is an example of a proper answer (from my LAN domain 'localnet'):
```
dig +nssearch localnet
SOA ns.localnet. admin.reinhardt.localnet. 1503262353 10800 3600 604800 38400 from server 192.168.1.1 in 0 ms.
```
or as this example from the ubuntuforums.org domain:
```
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.91.139 in 41 ms.
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.94.173 in 107 ms.
SOA ns1.canonical.com. hostmaster.canonical.com. 2015070901 10800 3600 604800 3600 from server 91.189.95.3 in 114 ms.
```
To help with setting up a Windows DNS server you can try creating a thread in this subforum:
```
The Ubuntu Forum Community -> Other Discussion and Support -> Other OS Support and Projects -> Other Operating Systems -> Windows
```
Alternatively, you can request to move this thread to that forum, by pressing the 'report post' button and making the request there.
Regards.

---

### Post by ncage on 2015-07-25
Thanks i guess i have to dig more into dns :(. I'm not not a network admin by trade (as you can tell :) ). More of a programmer. I guess i'll be reading up more about dns.

---

