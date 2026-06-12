---
title: "Problems with bind9"
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by zoey-cluff on 2015-03-02
I'm trying to install bind9 on a ubuntu server, and I'm getting the following problem.

zoey@ns1:~$ sudo apt-get install bind9
Reading package lists... Done
Building dependency tree
Reading state information... Done
bind9 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up bind9 (1:9.9.5.dfsg-3ubuntu0.2) ...
 * Stopping domain name service... bind9        
  rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                        usage: named [-4|-6] [-c conffile] [-d debuglevel] [-E engine] [-f|-g]
             [-n number_of_cpus] [-p port] [-s] [-t chrootdir] [-u username]
             [-m {usage|trace|record|size|mctx}]
named: extra command line arguments
                                                                         [fail]
invoke-rc.d: initscript bind9, action "restart" failed.
dpkg: error processing package bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
zoey@ns1:~$


I'm running the latest version of ubuntu.

Edit: It's happening on two different PC's.

---

### Post by Doug S on 2015-03-02
Hi and welcome to Ubuntu forums.

You might want to try uninstalling bind first, then install it again.

> **zoey-cluff said:**
> I'm trying to install bind9 on a ubuntu [COLOR=#ff0000]server[/COLOR]By server, you mean server right? No GUI stuff? If you installed any desktop stuff, or even if you installed virtualization during server install, then dnsmasq would have been installed, and might be competing for resources. Try getting rid of it also.

---

### Post by zoey-cluff on 2015-03-05
it's a base install except bind9. no gui or anything. dnsmasq is not installed. I tried reinstalling on both machines, still the same problem.

---

