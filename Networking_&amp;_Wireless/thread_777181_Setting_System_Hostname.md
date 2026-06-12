---
title: "Setting System Hostname"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Ignite_nz on 2008-05-01
I'm trying to set the system hostname right now, and I'm getting all kinds of problems. Basicly this is the desired output I want:

hostname = server
hostname -f = server.theginger.info.

But this is what I'm getting:

```
server server:~# hostname
server server.theginger.info
server server:~# hostname -f
hostname: Unknown host
server server:~# cat /etc/hosts
127.0.0.1       server localhost
192.168.1.3     server.theginger.info

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

server server:~# cat /etc/hostname
server server.theginger.info

```

I thought I'd paste all that to give as much info as possible. I've definatly boked it nicely, and since i've never had problems with hostnames likes this before it'd be great if someone could give me a pointer on what to do here.

Cheers.

---

### Post by Oldsoldier2003 on 2008-05-02
> **Ignite_nz said:**
> I'm trying to set the system hostname right now, and I'm getting all kinds of problems. Basicly this is the desired output I want:

hostname = server
hostname -f = server.theginger.info.

But this is what I'm getting:

```
server server:~# hostname
server server.theginger.info
server server:~# hostname -f
hostname: Unknown host
server server:~# cat /etc/hosts
127.0.0.1       server localhost
192.168.1.3     server.theginger.info

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

server server:~# cat /etc/hostname
server server.theginger.info

```

I thought I'd paste all that to give as much info as possible. I've definatly boked it nicely, and since i've never had problems with hostnames likes this before it'd be great if someone could give me a pointer on what to do here.

Cheers.

here is a default /etc/hosts:
```
127.0.0.1	localhost
127.0.1.1	theginger

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
here is a default /etc/hostname
```
theginger
```
 Hardy doesn't like dotted host names, it can cause problems, like breaking sudo. The server name with fqdn is set in apache so patch up your hosts and hostname to look like a default and everything should be fine.

---

