---
title: "Unable to send ICMP redirect"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Nathariel on 2008-04-11
Hi all, 

In order to test some tcp/ip stack and firewall security features on diff. linux boxes I need to craft a fake icmp redirect in my local network. And here come the troubles...The kernel keeps rejecting to send icmp redirect packets ( type 5 code 0-3)

The simplest example that should pass:

```

 hping2  -1 -I eth0 192.168.2.213 -a 192.168.2.1  -C 5 -K 1

HPING 192.168.2.213 (eth0 192.168.2.213): icmp mode set, 28 headers + 0 data bytes
[send_ip] sendto: Operation not permitted


```

Of course I have tried it under root , sudo-ing, etc and nothing...
Let me attach the current conf at the ubuntu box:

```

 sysctl -a | grep net.ipv4.conf.*redirect

net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.secure_redirects =0
net.ipv4.conf.all.send_redirects = 1
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.default.secure_redirects = 0
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.lo.accept_redirects = 0
net.ipv4.conf.lo.secure_redirects =0
net.ipv4.conf.lo.send_redirects = 1
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.eth0.secure_redirects = 0
net.ipv4.conf.eth0.send_redirects = 1
net.ipv4.conf.eth1.accept_redirects = 0
net.ipv4.conf.eth1.secure_redirects = 0
net.ipv4.conf.eth1.send_redirects = 1


```

The ip tables is also flushed...

```

sudo iptables -L 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


```

And this is the strace output:

```

 sudo strace  hping2  -1 -I eth0 192.168.2.213 -a 192.168.2.1  -C 5 -K 1

...
write(1, "HPING 192.168.2.213 (eth0 192.16"..., 83HPING 192.168.2.213 (eth0 192.168.2.213): icmp mode set, 28 headers + 0 data bytes
) = 83
getpid()                                = 21688
kill(21688, SIGALRM)                    = 0
--- SIGALRM (Alarm clock) @ 0 (0) ---
brk(0)                                  = 0x805e000
brk(0x807f000)                          = 0x807f000
sendto(3, "E\0\0008\364`\0\0@\1\0\0\300\250\2\1\300\250\2\325\5\1"..., 56, 0, {sa_family=AF_INET, sin_port=htons(0), sin_addr=inet_addr("192.168.2.213")}, 16) = -1 EPERM (Operation not permitted)
dup(2)                                  = 5
fcntl64(5, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(5, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f1a000
_llseek(5, 0, 0xbfce5dd8, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(5, "[send_ip] sendto: Operation not "..., 42[send_ip] sendto: Operation not permitted
) = 42
...


```

The same is happening on another pc running SUSE so I presume it is a kernel problem...
I have already spend 20 hours searching solution about this and nothing so far. That's why I have decided to contact the community if somebody have experience with stuff like that.

I would be gratefull if anyone could help.

---

### Post by The Cog on 2008-04-12
I haven't tried it, but packEth looks like it could do the trick for you:
[http://packeth.sourceforge.net/](http://packeth.sourceforge.net/)

---

