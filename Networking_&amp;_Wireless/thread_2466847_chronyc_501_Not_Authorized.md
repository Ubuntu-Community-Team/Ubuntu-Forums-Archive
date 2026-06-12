---
title: "chronyc 501 Not Authorized"
date: 2021-09-07
forum: Networking &amp; Wireless
---

### Post by stephenstark on 2021-09-07
I am attempting to setup chrony as an NTP server on Ubuntu 16.04.  Chrony installs properly, but when I try to run sudo chronyc clients to validate that clients are connecting properly I get a "501 Not Authorized" error message.  It appears that chrony did not create the [FONT=Georgia][COLOR=#000080]*/var/run/chrony/chronyd.sock domain socket, though I am not sure why?*[/COLOR][/FONT]

---

### Post by TheFu on 2021-09-11
16.04 became EoL last April. Move to a supported release.  

I'm 100% positive that the 18.04 Server release with chrony as a server works fine.

```
$ ll  /etc/chrony/chrony*
-rw-r--r-- 1 root root 1894 Apr  9 11:20 /etc/chrony/chrony.conf
-rw-r----- 1 root root  489 Aug 25  2020 /etc/chrony/chrony.keys

$ sudo ls -l /var/run/chrony/
total 0
srwxr-xr-x 1 _chrony _chrony 0 Aug 21 14:11 chronyd.sock

$ uptime
 09:02:27 up 20 days, 18:52, .... 
```

FYI.

---

