---
title: "Running openvpn client without root privileges"
date: 2018-05-21
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2018-05-21
Hello,

     I use ubuntu 16.04 LTS desktop version. My question is about OpenVPN client security. Usually the OpenVPN client is run with sudo privileges. Isn't this a security risk? Someone could exploit a vulnerability in the OpenVPN connection and execute code with root privileges on my system. To protect against this, is there any way to set up the OpenVPN client so that it can be run by a regular user without sudo privileges??

---

### Post by jsvidyad on 2018-05-21
I found this web page : [https://community.openvpn.net/openvpn/wiki/UnprivilegedUser](https://community.openvpn.net/openvpn/wiki/UnprivilegedUser)

But, in this page it is mentioned that it does not apply to ubuntu machines. How can I adapt it to an ubuntu 16.04 system??

---

### Post by jsvidyad on 2018-05-21
Should this be moved to the security forum??

---

### Post by SeijiSensei on 2018-05-21
Usually the OpenVPN daemon starts as root but spawns subprocesses that run under an unprivileged account, often nobody:nobody or nobody:nogroup.  That's what the "user" and "group" directives in the configuration file are intended for. 

After the client has started, look at the results of "ps aux | grep openvpn" and see which user owns the process.  I'd bet it's not root.  On my (CentOS) systems running OpenVPN, that command returns

```
**nobody**    8605  4.1  0.0  46520   932 ?        Ss   Feb13 5718:19 /usr/sbin/openvpn --daemon --writepid /var/run/openvpn/myserver.pid --cd /etc/openvpn --config myserver.conf --script-security 2
```

I'd be surprised if the Ubuntu implementation is any different.  Even if it is, you can change the "user/group" directives in the configuration file yourself.

---

### Post by Skaperen on 2018-05-22
there is nothing wrong with running openvpn via sudo if sudo is configured to only allow trusted (trusted to be careful and not exploit it) non-root users to run it.

---

