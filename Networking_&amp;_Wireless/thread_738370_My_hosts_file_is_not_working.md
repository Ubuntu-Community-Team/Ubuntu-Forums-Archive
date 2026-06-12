---
title: "My hosts file is not working"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by alexisbellido on 2008-03-28
I have tried to add a host in my /etc/hosts file in one of my boxes but it's not working, as root I edited /etc/hosts and added something like this:

1.2.3.4 dev example.com

But when I ping to example.com I get the original IP of that hosts, not the one I'm using.

I was running BIND9 and I stopped it, even if I know /etc/hosts has the priority, no luck either.

My /etc/nsswitch.conf is like this:

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns
networks:       files

```

I've done /etc/hosts changes in many of my other boxes and works ok, any idea why is not working here?

Thanks!

---

### Post by seeker1458 on 2008-03-28
What are you trying to accomplish? are you logging things from these addresses? The reason I ask is when setting up a syslog-ng server I had all my devices defined, and realized they were being logged by ip address referencing their FQDN.  Even though I had the address defined in the hosts file.  I had to enable DNS just to use the hosts file host names.

:edit: Let me clarify that.  I had to enable DNS in my syslog-ng.conf to relove the defined host names.

---

### Post by Eiríkr on 2008-03-28
Here's a couple sample lines from a Win XP hosts file, since I'm not at home right now:
```
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host
```

The hosts file format is identical, since Microsoft just used BSD's TCP stack years ago and hasn't ever futzed  with it too badly.  

@alexisbellido --

You have a space between your hostname "dev" and your domain name "example.com".  There should be no spaces, only dots, separating parts of any host name.  

@seeker1458 --

Did you have the FQDNs in your hosts file, or only the hostnames (the part before the first period)?

Cheers,

Eiríkr

---

### Post by alexisbellido on 2008-03-28
No, I'm not logging anything, it's just that I've moved a server but still haven't updated name servers for its domain so I need a way to tell my laptop how to resolve the host name.

---

### Post by alexisbellido on 2008-03-28
Eiríkr, dev and example.com are two host names I want to associate to IP 1.2.3.4, I didn't try to say 'dev.example.com'

---

### Post by Eiríkr on 2008-03-28
Thanks for the clarification.  Does "ping dev" work then, by any chance?

---

### Post by alexisbellido on 2008-03-31
No, neither host name us working. I have used hosts files for years and know my way around DNS stuff on Linux, that's why I find so weird that Ubuntu is not following /etc/hosts settings.

Any suggestions?

---

### Post by yota on 2008-03-31
Hi what's in your /etc/host.conf file?

should be something like this in order to make /etc/hosts have precedence over resolv.conf:
> 
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on


hope this helps!

p.s. here works as expected:
> 
$ ping [www.ubuntu.com](www.ubuntu.com)
PING [www.ubuntu.com](www.ubuntu.com) (91.189.94.158) 56(84) bytes of data.
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=1 ttl=44 time=42.0 ms
64 bytes from arctowski.canonical.com (91.189.94.158): icmp_seq=2 ttl=44 time=41.9 ms

--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 41.930/41.975/42.021/0.209 ms
$ sudo vi /etc/hosts
$ ping [www.ubuntu.com](www.ubuntu.com)
PING [www.ubuntu.com](www.ubuntu.com) (1.2.3.4) 56(84) bytes of data.
--- [www.ubuntu.com](www.ubuntu.com) ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9033ms


---

### Post by alexisbellido on 2008-03-31
Hi, I reviewed my /etc/hosts/conf file, I have exactly the same thing you posted:

```

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

```

Still no luck :(

---

### Post by yota on 2008-03-31
And what about /etc/nsswitch.conf?
mine is as follows:
> 
$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

**hosts:         _ files_ mdns4_minimal [NOTFOUND=return] dns mdns4**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

pay attention expecially to the bolded line: files should be the first entry.

---

### Post by alexisbellido on 2008-03-31
Hey Yota, thanks for the suggestion. I posted my nsswitch.conf file above and yes, I already have 'files' as first in the hosts line.

---

### Post by yota on 2008-04-01
Whoops sorry... I thought I fixed the "remember to read the whole post" bug long time ago, but apparently it come back!

I'm out of ideas here... maybe you can launch "strace pring" or "strace <some other command that requires name resolution>" trying to spot if something is going badly wrong about /etc/hosts.

---

