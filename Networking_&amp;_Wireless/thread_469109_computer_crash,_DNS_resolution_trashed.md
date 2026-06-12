---
title: "computer crash, DNS resolution trashed"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by zaroff on 2007-06-09
Last night, I had a problem with a chipset cooler that led to some overheating and caused my desktop system crashing hard several times during boot up. I've fixed that problem and all the hardware is running fine now.  However, during the course of recovery with fsck, some files on my root partition got trashed. The result is that now I can't resolve DNS names with most programs. For example, apt-get and wget always say "Could not resolve" but the host command works fine:

```
zaroff@tardis:~$ host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 209.85.165.103
www.l.google.com has address 209.85.165.104
www.l.google.com has address 209.85.165.147
www.l.google.com has address 209.85.165.99
```

Trying to ssh into my mythtv box by name doesn't work:

```
zaroff@tardis:~$ ssh mythtv
ssh: mythtv: Name or service not known
```

but by IP address does:

```
zaroff@tardis:~$ ssh 192.168.1.5
zaroff@192.168.1.5's password: 
Welcome to KnoppMyth (Kernel 2.6.18-chw-13)
```

Thunderbird, Gaim, and Azureus can't resolve any server names but Firefox works fine (posting from it now). I can also access the internet fine from my Windows XP virtual machine in Vmware Server.

resolv.conf is there and is correct (same as on all my other machines at home):

```
search gallifrey
nameserver 192.168.1.1
```

as is nsswitch.conf

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

So what's wrong? I'm thinking it's probably just one or two files missing or corrupted but I have no idea what they might be. I'd like to try and avoid a complete reinstall if possible. Does anyone have any ideas?

---

