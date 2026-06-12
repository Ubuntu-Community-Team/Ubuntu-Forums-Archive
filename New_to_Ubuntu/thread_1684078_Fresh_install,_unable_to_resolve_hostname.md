---
title: "Fresh install, unable to resolve hostname"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by newn on 2011-02-08
Hi everybody. What this error is about:
Resolving long.and.pointless.address... failed: Temporarily failure in name resolution.
Unable to resolve host address 'http://address.something.google.blablabla'

I just installed the server edition of Ubuntu 10.10 x64 and I want to try to compile the kernel, which means I need to wget at least 2 files.

I can't connect trough SSH, because it's not working either...

---

### Post by Tyggna on 2011-02-08
Well, it's a network problem.

If it can't resolve a hostname--that means it can't contact a DNS server to associate the server's name with its appropriate ip address.

This can mean one of two things:  you have no DNS server to connect to (unlikely), or you have no connection.

Given that you can't get in via ssh, you probably don't have proper internet access on this server.

Try running dhclient as root, see if you can get a lease.

---

### Post by newn on 2011-02-08
I've got KVM access to the server. Running dhclient prints permission denied on all of these...

[http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.37.tar.gz](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.37.tar.gz) sounds okay DNS name to me. Checked and rechecked it few times, so it's written correctly.

Also, it was working BEFORE the reinstallation. Then it wasn't installed by me. I had to reinstall OS, because I screwed up the kernel. In fact, I'm trying to do it now.

---

