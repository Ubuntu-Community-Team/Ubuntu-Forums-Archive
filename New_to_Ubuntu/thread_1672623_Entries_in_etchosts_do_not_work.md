---
title: "Entries in /etc/hosts do not work"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-01-21
It should be so simple, but it is not. I have the /etc/hosts files, as follows,


```
172.16.210.32   rafid-hamiz     # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     rafid-hamiz     localhost6.localdomain6 localhost6
127.0.1.1       rafid-hamiz

127.0.1.1 anothersite
127.0.1.1 mysite
127.0.1.1 mysite.test


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Some of the above entries were there, some were added manually by me for testing purpose.

Now, please see the command output,

```
masroor@rafid-hamiz:~$ host localhost
localhost has address 127.0.0.1
localhost has IPv6 address ::1

```

So, this works.


Now none of the following works,

```
masroor@rafid-hamiz:~$ host rafid-hamiz
Host rafid-hamiz not found: 3(NXDOMAIN)
```


```

masroor@rafid-hamiz:~$ host mysite.test
Host mysite.test not found: 3(NXDOMAIN)
```

Also, the newer entries by me do not work,

```
masroor@rafid-hamiz:~$ host anothersite
Host anothersite not found: 3(NXDOMAIN)

```

I even tried restarting the networking service without any avail. (I knew that this step is not necessary).

Please tell me what is it I am missing.


Other relevant files are,

/etc/resolv.conf is empty


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

---

### Post by Brandon Williams on 2011-01-21
The host utility is like dig and nslookup, it always checks with DNS. Use gethostip if you want to do a full lookup using all the methods configured in nsswitch.conf.

---

### Post by mmasroorali on 2011-01-21
Thanks. It works.

Which of these is used by the browsers?

---

### Post by Brandon Williams on 2011-01-21
gethostip uses the method that most applications will use, so if the hostname resolves with gethostip, it should work for any standard application.

---

