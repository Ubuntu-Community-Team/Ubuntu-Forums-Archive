---
title: "ping to localhost failed"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by kagarcia on 2017-07-19
Can someone help me with this issue?
[INDENT]root@racken-ubuntu-server:~# ping localhost[/INDENT]
[INDENT]ping: unknown host localhost[/INDENT]

Already did the following checking:
[INDENT]**hosts file check**
root@racken-ubuntu-server:~# more /etc/hosts[/INDENT]
[INDENT]127.0.0.1       localhost[/INDENT]
[INDENT]192.168.133.22  racken-ubuntu-server

**nsswitch.conf file check**
root@racken-ubuntu-server:~# more /etc/nsswitch.conf | grep hosts
hosts:          files dns mdns4

root@racken-ubuntu-server:~# stat -c "%a %n" /etc/nsswitch.conf
644 /etc/nsswitch.conf

**ping check**
root@racken-ubuntu-server:~# ping 127.0.0.1 -c 1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.015 ms


--- 127.0.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.015/0.015/0.015/0.000 ms
root@racken-ubuntu-server:~# 

**nslookup check**
root@racken-ubuntu-server:~# nslookup localhost
Server:         192.168.1.254
Address:        192.168.1.254#53


Name:   localhost
Address: 127.0.0.1


root@racken-ubuntu-server:~# 


My root issue is that I can't ping any URL but can resolve their IP thru dig or nslookup then I found out that ping to localhost isn't even working. Thanks everyone in advance! 



[/INDENT]

---

### Post by chili555 on 2017-07-19
My /etc/hosts looks like this:```
127.0.0.1       localhost
[COLOR="#FF0000"]127.0.1.1       T440p[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```I have highlighted the part that seems to be misconfigured that may play a part here. If that is how you are trying to set a static IP, it is wrong.

I'd also look at:```
cat /etc/hostname
```Mine says:```
T440p
```

For comparison:```
chili@T440p:~$ ping -c3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.021 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.043 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.043 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2033ms
rtt min/avg/max/mdev = 0.021/0.035/0.043/0.012 ms
chili@T440p:~$ ping -c3 www.ubuntu.com
PING www.ubuntu.com (91.189.89.118) 56(84) bytes of data.
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.118): icmp_seq=1 ttl=44 time=97.0 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.118): icmp_seq=2 ttl=44 time=96.5 ms
64 bytes from www-ubuntu-com.nuno.canonical.com (91.189.89.118): icmp_seq=3 ttl=44 time=98.4 ms

--- www.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 96.549/97.350/98.481/0.860 ms

```

---

### Post by kagarcia on 2017-07-19
It's the same as checked. Any other areas that might have been misconfigured?

---

### Post by chili555 on 2017-07-19
> It's the same as checked.Meaning what, exactly? That your hosts file still reads:```
127.0.0.1 localhost
192.168.133.22 racken-ubuntu-server

```Then it's wrong.

---

### Post by kagarcia on 2017-07-19
I mean tried it already but still not working.

```
root@racken-ubuntu-server:~# 
root@racken-ubuntu-server:~# ping localhost
ping: unknown host localhost
root@racken-ubuntu-server:~# more /etc/hosts
127.0.0.1       localhost
127.1.0.1       racken-ubuntu-server
#192.168.133.22 racken-ubuntu-server
#8.8.8.8                www.google.com


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@racken-ubuntu-server:~# more /etc/hostname
racken-ubuntu-server





```

---

### Post by chili555 on 2017-07-19
```
127.0.0.1       localhost
[COLOR="#FF0000"]127.1.0.1     [/COLOR]  racken-ubuntu-server
#192.168.133.22 racken-ubuntu-server
#8.8.8.8                www.google.com


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```It should be 127.0.1.1. Next, I suggest a reboot.

---

### Post by kagarcia on 2017-07-19
Still not working.

```
root@racken-ubuntu-server:~# uptime 06:55:18 up 1 min,  1 user,  load average: 0.16, 0.07, 0.02
root@racken-ubuntu-server:~# ping localhost
ping: unknown host localhost
root@racken-ubuntu-server:~# more /etc/hosts
127.0.0.1       localhost
127.0.1.1       racken-ubuntu-server
#192.168.133.22 racken-ubuntu-server
#8.8.8.8                www.google.com


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@racken-ubuntu-server:~# 
```

---

### Post by chili555 on 2017-07-19
Let's see:```
cat /etc/hostname
cat /etc/network/interfaces

```

---

### Post by kagarcia on 2017-07-19
Here you go:

```

root@racken-ubuntu-server:~# cat /etc/hostname
racken-ubuntu-server
root@racken-ubuntu-server:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto ens160
iface ens160 inet static
        address 192.168.133.22
        netmask 255.255.255.0
        network 192.168.133.0
        broadcast 192.168.133.255
        gateway 192.168.133.250
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.254


auto tap_vpn_lan
iface tap_vpn_lan inet static
        address 192.168.30.2
        netmask 255.255.255.0
        network 192.168.30.0
        broadcast 192.168.30.255
```

---

### Post by chili555 on 2017-07-19
I was concerned about the loopback stanzas. That looks default and perfect.

You won't need these entries, although it probably has nothing to do with the current problem.:```
source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto ens160
iface ens160 inet static
        address 192.168.133.22
        netmask 255.255.255.0
        [COLOR="#FF0000"]network 192.168.133.0
        broadcast 192.168.133.255[/COLOR]
        gateway 192.168.133.250
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.254


auto tap_vpn_lan
iface tap_vpn_lan inet static
        address 192.168.30.2
        netmask 255.255.255.0
        network 192.168.30.0
        broadcast 192.168.30.255
```The gateway looks a bit suspicious and I wonder if the DNS nameserver is pingable from 192.168.133.xx. It's hard to test, of course, when *nothing* is pingable!!

Aside from that, I regret I know nothing whatever about VPN.

---

### Post by kagarcia on 2017-07-19
Gateway & DNS doesn't have any problem. I'm on a virtual environment that's why it's like that.

```
root@racken-ubuntu-server:~# arp -a
? (192.168.133.136) at 00:50:56:c0:00:08 [ether] on ens160
? (192.168.133.250) at 00:50:56:ad:36:17 [ether] on ens160

root@racken-ubuntu-server:~# dig @192.168.1.254 www.google.com


; <<>> DiG 9.10.3-P4-Ubuntu <<>> @192.168.1.254 www.google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42448
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;www.google.com.                        IN      A


;; ANSWER SECTION:
www.google.com.         55      IN      A       74.125.24.106
www.google.com.         55      IN      A       74.125.24.104
www.google.com.         55      IN      A       74.125.24.105
www.google.com.         55      IN      A       74.125.24.147
www.google.com.         55      IN      A       74.125.24.99
www.google.com.         55      IN      A       74.125.24.103


;; Query time: 1 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Thu Jul 20 08:15:39 SGT 2017
;; MSG SIZE  rcvd: 128

root@racken-ubuntu-server:~# ping www.google.com
ping: unknown host www.google.com
root@racken-ubuntu-server:~# ping 74.125.24.106
PING 74.125.24.106 (74.125.24.106) 56(84) bytes of data.
64 bytes from 74.125.24.106: icmp_seq=1 ttl=42 time=4.66 ms
64 bytes from 74.125.24.106: icmp_seq=2 ttl=42 time=6.60 ms
^C
--- 74.125.24.106 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.667/5.634/6.601/0.967 ms
root@racken-ubuntu-server:~# 





```

---

### Post by chili555 on 2017-07-19
> root@racken-ubuntu-server:~# ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
root@racken-ubuntu-server:~# ping 74.125.24.106
PING 74.125.24.106 (74.125.24.106) 56(84) bytes of data.
64 bytes from 74.125.24.106: icmp_seq=1 ttl=42 time=4.66 ms
64 bytes from 74.125.24.106: icmp_seq=2 ttl=42 time=6.60 ms
^C
--- 74.125.24.106 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.667/5.634/6.601/0.967 msBetter?> I'm on a virtual environment Another subject I know nothing about. Sorry.

---

### Post by kagarcia on 2017-07-19
This is my first issue and still is my issue:

```
[COLOR=#000000]*root@racken-ubuntu-server:~# ping *[/COLOR][www.google.com]("http://www.google.com/")
[COLOR=#000000]*ping: unknown host *[/COLOR][www.google.com]("http://www.google.com/")
```

Thank you very for your help **@chili555**. I hope other folks here have somehow encountered this issue like mine. I can easily revert back to any my VM snapshots to resolve this issue but I wanna know first what caused this problem.

---

### Post by chili555 on 2017-07-19
Can you:```
ping -c3 8.8.8.8
```If so, I'd try that instead for DNS:```
dns-nameservers 8.8.8.8 8.8.4.4
```

---

### Post by kagarcia on 2017-07-21
This is not the issue because I can definitely ping any public IP address. My issue is that when I ping any public or private domain name, the system doesn't resolve it to its equivalent IP address.

```

root@racken-ubuntu-server:~# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=4.22 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=4.11 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=5.57 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 4.116/4.637/5.572/0.666 ms

```

```

root@racken-ubuntu-server:~# ping google.com
ping: unknown host google.com
root@racken-ubuntu-server:~# ping yahoo.com
ping: unknown host yahoo.com
root@racken-ubuntu-server:~# nslookup google.com
Server:         192.168.1.254
Address:        192.168.1.254#53


Non-authoritative answer:
Name:   google.com
Address: 74.125.200.138
Name:   google.com
Address: 74.125.200.102
Name:   google.com
Address: 74.125.200.139
Name:   google.com
Address: 74.125.200.101
Name:   google.com
Address: 74.125.200.113
Name:   google.com
Address: 74.125.200.100


root@racken-ubuntu-server:~# dig yahoo.com


; <<>> DiG 9.10.3-P4-Ubuntu <<>> yahoo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38272
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;yahoo.com.                     IN      A


;; ANSWER SECTION:
yahoo.com.              203     IN      A       98.138.253.109
yahoo.com.              203     IN      A       98.139.180.149
yahoo.com.              203     IN      A       206.190.36.45


;; Query time: 20 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Fri Jul 21 20:57:07 SGT 2017
;; MSG SIZE  rcvd: 86


root@racken-ubuntu-server:~# 

```

---

