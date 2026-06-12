---
title: "Cannot resolve hostnames"
date: 2017-10-13
forum: Networking &amp; Wireless
---

### Post by shniperson on 2017-10-13
I have strange problem with resolving hostnames on Ubuntu 16.04.2.
It's a server in local network with two interfaces: external (to the internet) and internal (to local network). Both are static configured. I'll show config below.
It was working perfectly since installed in march. Several times I've successfully made 'apt update' with no problem. Today i tried to update it again, and here the main story begins...

```

Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-93-generic x86_64)

~$ sudo apt update
Err:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree
Reading state information... Done
195 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

```

~$ ping google.com
ping: unknown host google.com

~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=3.87 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=3.93 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=3.88 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.870/3.898/3.939/0.077 ms

~$ telnet 8.8.8.8 53
Trying 8.8.8.8...
Connected to 8.8.8.8.
Escape character is '^]'.
Connection closed by foreign host.

```

On previous updates there was no such problems with resolving hostnames. Server is primarily used in local network by ip address, so i don't know when this problem arise.
So here are some commands, that i executed (sorry, external ip address i replaced with #):

```

~$ ifconfig
enp29s0   Link encap:Ethernet  HWaddr 00:10:18:25:cd:40
          inet addr:#.#.#.#  Bcast:#.#.#.#  Mask:255.255.255.248
          inet6 addr: fe80::210:18ff:fe25:cd40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14777641 (14.7 MB)  TX bytes:22823397 (22.8 MB)


enp3s0    Link encap:Ethernet  HWaddr 00:1a:64:c9:93:f8
          inet addr:10.0.35.115  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:64ff:fec9:93f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:779951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:608340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:514425482 (514.4 MB)  TX bytes:189891768 (189.8 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2145438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2145438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:1185976997 (1.1 GB)  TX bytes:1185976997 (1.1 GB)

```

```

~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface - Internal
auto enp3s0
iface enp3s0 inet static
        address 10.0.35.115
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255
#       gateway 10.1.10.102
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 10.1.10.102
        metric 20


# The secondary network interface - External
auto enp29s0
iface enp29s0 inet static
        address #.#.#.#
        netmask 255.255.255.248
#       network #.#.#.#
#       broadcast #.#.#.#
        gateway #.#.#.#
        dns-nameservers 8.8.8.8 8.8.4.4
        metric 10


#auto enp6s0
iface enp6s0 inet manual

```

```

~$ ls -la /etc/resolv.conf
lrwxrwxrwx 1 root root 27 Oct 14 01:46 /etc/resolv.conf -> /run/resolvconf/resolv.conf


~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4

```

But nmcli didn't show any DNS configured:
```

~$ nmcli dev show | grep 'DNS'

~$ nmcli dev show | grep 'IP4'
IP4.ADDRESS[1]:                         #.#.#.#/29
IP4.GATEWAY:                            #.#.#.#

```

What i did:
- several times restarted server.
- several times restarted systemd-resolved, NetworkManager.
- comment and uncomment "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf (with restart service and server).
- found advice about switch off DNSSEC, but as i found it's already switched off.
- made /etc/resolv.conf static file (not symbolic link), get back to symbolic link - all with restarts.

Nothing of this helps...

So i have no any more ideas how to get DNS resolving back to work.
All advices appreciates :)

---

### Post by mcparty2 on 2017-10-17
Something must have changed... Has there been any firewall changes?
Failing that, if you temporarily shut down enp3s0 - does the problem disappear? 

Can you run:

```
dig @8.8.8.8 www.google.com
```

You should get an answer like this:

```


dig @8.8.8.8 www.google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @8.8.8.8 www.google.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24747
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;www.google.com.            IN    A

;; ANSWER SECTION:
www.google.com.        262    IN    A    216.58.206.100

;; Query time: 33 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Oct 17 14:15:57 BST 2017
;; MSG SIZE  rcvd: 59


```


If you don't there is something very screwy going on.

I hope this helps

---

### Post by shniperson on 2017-10-18
Finally, I got it: it was iptables issue. I didn't remember that I was blocking this rule, but all UDP incoming packets were marked to DROP. So DNS server cannot send answer to Ubuntu.
Setting to ACCEPT resolve problem.

---

