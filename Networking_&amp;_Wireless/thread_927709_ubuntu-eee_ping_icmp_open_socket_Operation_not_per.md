---
title: "ubuntu-eee ping: icmp open socket: Operation not permitted"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by asbesto on 2008-09-23
Hi, this is my weird problem on Asus eeepc 701, ubuntu-eee installed and fresh-upgraded:

> asbesto@lem:~$ ping google.it
ping: icmp open socket: Operation not permitted

:confused:

Instead, from root I have:

> asbesto@lem:~$ sudo bash
root@lem:~# ping google.it
PING google.it (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=240 time=133 ms
64 bytes from 216.239.59.104: icmp_seq=2 ttl=240 time=132 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=240 time=132 ms

--- google.it ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10487ms
rtt min/avg/max/mdev = 132.178/132.744/133.488/0.549 ms
root@lem:~# 


](*,)


Why this ?!? 

:confused::confused::confused:

---

### Post by nixscripter on 2008-09-23
Check to ensure that the ping binary is setuid root:

```
ls -l `which ping`
```

It should come back:

```
-rw_s_r-xr-x 1 root root 30856 2007-07-06 02:40 /bin/ping
```

If that's not an s, you can fix it with:

```
sudo chmod u+s `which ping`
```

Then you will be allowed to ping as anyone.

Hope this helps.

---

### Post by asbesto on 2008-09-24
I already note that yesterday night (sorry for not telling here); now the question is... WHY? :)

chmod fixed, anyway :)

thanks :)

---

### Post by koecing on 2010-05-17
try this one
```
chmod u+s /bin/ping
```

---

