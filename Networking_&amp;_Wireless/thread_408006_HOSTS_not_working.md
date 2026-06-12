---
title: "HOSTS not working"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by 303 on 2007-04-12
/etc/HOSTS isn't blocking any ads, etc...

I have
127.0.0.1 localhost
then the rest of what I want blocked is set to
127.0.0.1  whatiwantblocked.address

what am I not doing right here?
I think I'm missing something
could someone also give the default entries as well? many thanks

I used gedit because it wouldn't show up in nano (550k file)

---

### Post by spd106 on 2007-04-13
Linux is case sensitive, so /etc/HOSTS != /etc/hosts.

Here is the default file, swap hostname for yours. 
```
spd106@hostname:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 hostname

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by 303 on 2007-04-14
Thank you.
I don't know how the file was saved in all caps, fixed now though
:D

---

