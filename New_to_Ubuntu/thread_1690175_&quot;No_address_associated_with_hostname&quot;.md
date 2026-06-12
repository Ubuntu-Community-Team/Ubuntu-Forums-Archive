---
title: "&quot;No address associated with hostname&quot;"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Gooseheaded on 2011-02-17
Hello, everyone.

Recently I installed Xubuntu on a desktop, and installed LAMP on it. I forwarded my ports, assigned a static IP, and all that good stuff. A few days ago, however, I had to reboot my router, and everything got quite messy,

The server responds to ping, and the website works fine;
but when I try to install any programs (say, mumble through *apt-get mumble-server*), I get several error messagees saying, 

W: Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Something wicked happened resolving 'mx.archive.ubuntu.com:http' (-5 - No address associated with hostname)

Google says it's something about my /etc/hosts file.
What should it look like? my hostname is gooseheaded-desktop, and here is my /etc/hosts file at the moment:

```
127.0.0.1       gooseheaded-desktop     localhost.localdomain   localhost
::1     gooseheaded-desktop     localhost6.localdomain6 localhost6
::1     gooseheaded-desktop     localhost6.localdomain6 localhost6
127.0.1.1       gooseheaded-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Thanks, again.

---

### Post by Keiran230 on 2011-02-18
That sounds like a "name resolution" issue, which means you're missing DNS information. To set this through the command-line, edit **/etc/resolv.conf**. If you don't know what DNS server to use, you can use Google's free DNS server located at the IP of 8.8.8.8 (primary) or 8.8.4.4 (secondary).

When trying to find out where a server is, your computer looks in three places. First, it looks in cache, then /etc/hosts, then to whatever nameserver (DNS server) is listed in /etc/resolv.conf. After it has tried these three places, it gives up and says it can't find the server.

---

