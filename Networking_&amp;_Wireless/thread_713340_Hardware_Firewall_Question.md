---
title: "Hardware Firewall Question"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by blx_286 on 2008-03-02
I would like to setup an ubuntu box to serve just as a secure FTP server for sharing company projects with clients.

I have the base server and openssh installed and I have moved it from my network to my DMZ that is behind a hardware firewall. When the server was on my network, I was able to update the repositories. Now that the server is in the DMZ, I opened a port for SSh and I can SSH into it from the Internet, but I cannot install any packages to it. I get the follow message when trying to install rssh:

```
sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err http://us.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
```

I have port 80 and my SSH port open on my hardware firewall, can someone tell me what ports I need open for Aptitude and some networking tools like nslookup?

Thanks,
Tim

---

### Post by SpaceTeddy on 2008-03-02
aptitude usually uses port 80 (http) to download. 
it looks like your DNS server is gone... or your error message suggests so. Make sure that you /etc/resolv.conf contains nameservers that can be reached.
Also, check if your firewall is allowing tcp&udp port 53 (dns) in the appropriate Networks/Internet so the server can query the DNS...

---

