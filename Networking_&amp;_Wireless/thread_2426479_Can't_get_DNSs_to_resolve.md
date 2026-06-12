---
title: "Can't get DNSs to resolve"
date: 2019-09-09
forum: Networking &amp; Wireless
---

### Post by philiptmay on 2019-09-09
I'm running Ubuntu Server 18.04.3 LTS as a media server at my house, I'm also running pihole as my DNS from this machine. 

Today I had a power failure and found that my server wouldn't boot up so I ran Boot Repair through LiveCD. That got me back into the machine, but now I can't get any DNS requests to resolve. IP pings will go through, and all other devices on my network appear to have no issues, it's only this machine. I originally had the server DNS pointed to 127.0.0.1, and I believe that worked fine, but I also tried setting it to the router (which is set to point to the server, and which every other device is referencing) with no luck. 

I'm at the end of my Google-Fu on this.

Some possibly relevant info:
philip@server:~$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=16.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=16.0 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=56 time=19.9 ms


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 16.012/20.520/30.139/5.777 ms


philip@server:~$ ping -c 4 www.google.com
ping: www.google.com: Temporary failure in name resolution


philip@server:~$ systemd-resolve --status
Global[INDENT]DNSSEC NTA: 10.in-addr.arpa[/INDENT]
[INDENT=2]16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test[/INDENT]


Link 2 (enp0s25)[INDENT]Current Scopes: DNS
       LLMNR setting: yes[/INDENT]
MulticastDNS setting: no[INDENT]DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.0.1[/INDENT]


philip@server:~$ ifconfig
enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[INDENT]inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::7a2b:cbff:fe90:b628  prefixlen 64  scopeid 0x20<link>
        inet6 ::7a2b:cbff:fe90:b628  prefixlen 64  scopeid 0x0<global>
        inet6 ::2037:a654:e0fb:4073  prefixlen 64  scopeid 0x0<global>
        ether 78:2b:cb:90:b6:28  txqueuelen 1000  (Ethernet)
        RX packets 35194  bytes 6405331 (6.4 MB)
        RX errors 0  dropped 4189  overruns 0  frame 0
        TX packets 28363  bytes 13525336 (13.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xe1a00000-e1a20000[/INDENT]


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536[INDENT]inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 76993  bytes 6437152 (6.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 76993  bytes 6437152 (6.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/INDENT]

---

### Post by pcfan1234 on 2019-09-10
Show ```
nslookup google.de 9.9.9.9
nslookup google.de 127.0.0.53
nslookup google.de 192.168.0.1

```
Systemd-resolve runs under 127.0.0.53

---

### Post by philiptmay on 2019-09-10
> **pcfan1234 said:**
> Show ```
nslookup google.de 9.9.9.9
nslookup google.de 127.0.0.53
nslookup google.de 192.168.0.1

```
Systemd-resolve runs under 127.0.0.53


Here are those results:
philip@server:~$ nslookup google.de 9.9.9.9
Server:         9.9.9.9
Address:        9.9.9.9#53


Non-authoritative answer:
Name:   google.de
Address: 64.233.185.94
Name:   google.de
Address: 2607:f8b0:4002:c08::5e


philip@server:~$ nslookup google.de 127.0.0.53
;; connection timed out; no servers could be reached


philip@server:~$ nslookup google.de 192.168.0.1
Server:         192.168.0.1
Address:        192.168.0.1#53


Non-authoritative answer:
Name:   google.de
Address: 64.233.185.94
Name:   google.de
Address: 2607:f8b0:4002:c08::5e

---

### Post by SeijiSensei on 2019-09-10
You can specify the servers you want to use in [/etc/systemd/resolved.conf]("https://manpages.debian.org/testing/systemd/resolved.conf.5.en.html").  

```
DNS = 8.8.8.8 8.8.4.4
```

---

### Post by pcfan1234 on 2019-09-10
Do you use the NetworkManager to configure you network?
Then check if there is a DNS specified.

---

### Post by philiptmay on 2019-09-10
> **pcfan1234 said:**
> Do you use the NetworkManager to configure you network?
Then check if there is a DNS specified.

I'm pretty certain I've done everything through netplan. I do not have network manager installed (unless that's the same thing? it prompted me to install network-manager though netplan also references NetworkManager).
Also, to clarify, I'm running a private DNS from this machine that every other machine on my network is able to access, this is the only one not able to, and it had previously been working.

philip@server:/etc/netplan$ sudo netplan --debug generate
DEBUG:command generate: running ['/lib/netplan/generate']
** (generate:16536): DEBUG: 18:41:12.003: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:16536): DEBUG: 18:41:12.003: starting new processing pass
** (generate:16536): DEBUG: 18:41:12.003: Processing input file /etc/netplan/50-cloud-init.yaml..
** (generate:16536): DEBUG: 18:41:12.003: starting new processing pass
** (generate:16536): DEBUG: 18:41:12.003: enp0s25: setting default backend to 1
** (generate:16536): DEBUG: 18:41:12.003: Configuration is valid
** (generate:16536): DEBUG: 18:41:12.003: Generating output files..
** (generate:16536): DEBUG: 18:41:12.003: NetworkManager: definition enp0s25 is not for us (backend 1)

---

### Post by pcfan1234 on 2019-09-10
Show the content of the files located at /etc/netplan

---

### Post by philiptmay on 2019-09-10
> **pcfan1234 said:**
> Show the content of the files located at /etc/netplan

01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      dhcp4: no
      addresses: [192.168.0.10/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [127.0.0.1]     

50-cloud-init.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      dhcp4: no
      addresses: [192.168.0.10/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [127.0.0.1]     

I've tried swapping out other DNS addresses, pointing to the router, 127.0.0.53

---

### Post by TheFu on 2019-09-10
Last week I did a fresh install of 18.04.3 server and DNS didn't work.  I had to manually modify the netplan config files to get it working.  Sad when a fresh install doesn't work.   BTW, "server" distros don't use network-manager.  THANK GOD!

```
network:
    version: 2
    renderer: networkd
    ethernets:
        ens3:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```
Is what got it working, though the nameservers are being ignored as far as I can tell from the /etc/resolv.conf file.  If I cared more, I'd install dnscrypt-proxy and flush all the other solutions.

---

