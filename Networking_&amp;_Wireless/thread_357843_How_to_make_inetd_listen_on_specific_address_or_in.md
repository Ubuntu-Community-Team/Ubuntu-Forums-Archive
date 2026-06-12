---
title: "How to make inetd listen on specific address or interface"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by automatthias on 2007-02-10
Hi,

I have installed inetutils-inetd package, needed by vmware. It put this line into /etc/inetd.conf:

902 stream tcp nowait root /usr/sbin/vmware-authd vmware-authd

This line made vmware-auth listen on port 902 on all network interfaces. I would like it to listen on the loopback (lo) interface only. How can I achieve that with inetd? I read man inetd but it doesn't say anything about specifying listen interface or listen IP address. Do you have any ideas?

Automatthias

---

### Post by tturrisi on 2007-02-10
you could try dpkg reconfigure vmware (or whatever the package name is)
and bridge to lo

---

### Post by simpe_user on 2007-12-19
I have installed inetutils-inetd package, needed by vmware. It put this line into /etc/inetd.conf:

902 stream tcp nowait root /usr/sbin/vmware-authd vmware-authd

This line made vmware-auth listen on port 902 on all network interfaces.

192.168.130.1:902 stream tcp nowait root /usr/sbin/vmware-authd vmware-authd

to listen on interface with addr 192.168.130.1

---

