---
title: "can someone show me what their /etc/hosts file looks like BY DEFAULT?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-12-20
i think i did something wrong while changing the computer name. also, is it a bad idea to have a space in the computer name?

---

### Post by taurus on 2008-12-20
Yes, it's not a good idea to have a space in the computer name.  Remember, the name in /etc/hostname should be the same as in /etc/hosts or you will be logged out of sudo even if you belong to groups adm & admin.

```

127.0.0.1	localhost
127.0.1.1	linux

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by adult swim on 2008-12-20
```
huff@jaunty:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	jaunty

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by andrewwg94 on 2008-12-20
> **taurus said:**
> Yes, it's not a good idea to have a space in the computer name.  Remember, the name in /etc/hostname should be the same as in /etc/hosts or you will be logged out of sudo even if you belong to groups adm & admin.

```

127.0.0.1	localhost
127.0.1.1	linux

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

thanks for the quick reply. in your case, is "localhost" the computer name or is "linux" the computer name? i think my problem is that i made them both the same.

---

### Post by taurus on 2008-12-20
In my case, linux is the computer name; that is the same name in my /etc/hostname.

---

### Post by andrewwg94 on 2008-12-20
> **taurus said:**
> In my case, linux is the computer name; that is the same name in my /etc/hostname.

thanks again. so what does "localhost" mean?

---

### Post by taurus on 2008-12-20
You definitely need the first line "127.0.0.1 localhost" for X.

---

