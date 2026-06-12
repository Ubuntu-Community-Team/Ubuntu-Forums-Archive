---
title: "apt-get can't access repositories"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by bwald on 2006-10-02
Hello, I'm having a very strange problem with my repositories.  When I try to do

```
apt-get
```

I get 

> Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

I don't think this is a problem with my sources.list as I'm pretty sure its completely correct.  My sources.list is as follows:

> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

So I think the problem is just that apt-get can't see the repositories.  I first thought it might be a DNS problem but when I try to visit the repositories in firefox, (i.e. go to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu))  I can see them fine.  But when I try to ping the repositories, I get an unknown host.

```
bwald@CIRCE:# ping http://archive.ubuntu.com/ubuntu
ping: unknown host http://archive.ubuntu.com/ubuntu
```

In fact, when I try to ping anything that begins with http:// I get an unknown host, but when I drop it and just do www. I can ping it fine.  For example:

```
bwald@CIRCE:# ping http://google.com
ping: unknown host [http://google.com](http://google.com)
```
```
bwald@CIRCE:# ping www.google.com
PING [www.l.google.com](www.l.google.com) (64.233.179.99) 56(84) bytes of data.
64 bytes from 64.233.179.99: icmp_seq=1 ttl=248 time=4.68 ms
```

I don't know what this means.  I'm going to post my /etc/hosts and /etc/resolv.conf because I suspect the problem lies in one of those files.

/etc/hosts
```
127.0.0.1       localhost
127.0.1.1       CIRCE

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/resolv.conf
```
search wireless.emory.edu
nameserver 170.140.1.1
nameserver 170.140.2.1
```

Any help you can give would be greatly appreciated.

---

### Post by handy on 2006-10-02
I have allways had this problem since I first started with Breezy.

Your symptoms are the same, I don't use wireless though.

After following **option 3** from[http://www.ubuntuforums.org/showthread.php?t=128254&page=2]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2")   **Post# 13**.

I cleared the **/etc/resolv.conf** & brought the interface down and up again:

[B]sudo ifdown eth0
sudo ifup eth0[/B]

I have at last got the desired result!:

The correct DNS addresses, in the correct order & with the router's IP address at the bottom!

I hope this works for you too...

---

### Post by bwald on 2006-10-02
Thanks for the help, but when I bring the interface down and back up my resolv.conf is the same.  I tried using the wired network instead of the wireless and the same situation is occuring.

---

### Post by handy on 2006-10-03
> **bwald said:**
> Thanks for the help, but when I bring the interface down and back up my resolv.conf is the same.  I tried using the wired network instead of the wireless and the same situation is occuring.

Sorry bad link in my post above.

Try **Option 3** of **Post# 13** in the following link: [http://www.ubuntuforums.org/showthread.php?t=128254&page=2](http://www.ubuntuforums.org/showthread.php?t=128254&page=2)

---

### Post by bwald on 2006-10-03
I'm still having a problem.  I tried option 3 of that thread you showed me, and the problem still exists.  I don't know if this helps, but when I try and launch elinks it says I have an incorrectly set proxy.  I'm not sure where this proxy would be set or how to fix it, but I think that might be a problem.

---

