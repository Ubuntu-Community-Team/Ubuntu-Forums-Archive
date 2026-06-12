---
title: "unable to reach repository servers behind company proxy"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by headlice on 2008-07-11
Hi,

Ok, I set up ubuntu hardy server and can ping google.com, can nmap the company network (installed from CD) and can ssh into it but apt-get update returns a bunch of
-404 object not found
-error reading from server
-failed to fetch

Like so:

```
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages
  404 Object Not Found
Err http://us.archive.ubuntu.com hardy-updates/multiverse Sources
  404 Object Not Found
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  404 Object Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  404 Object Not Found

```

I only posted results for a few results but it is like this for all repos.

I also have a virtual machine (virtualbox) running debian etch and it does the same thing.

Yes, I tried 

```
export http_proxy=http://company.proxy.com:8080
```

still nothing.

I have wireshark monitoring the virtual machine and it looks as if it reaches my company's DNS yet it returns a 404 object not found

```
Request Version: HTTP/1.1
Response Code: 404
Server: Microsoft-IIS/5.0\r\n
```

---

### Post by headlice on 2008-07-11
anyone have a clue?

---

