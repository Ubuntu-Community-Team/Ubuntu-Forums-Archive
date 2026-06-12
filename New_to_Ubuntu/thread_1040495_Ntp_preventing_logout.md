---
title: "Ntp preventing logout?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-01-15
When i try to logout, i cannot. the same lines keep repeating:
```
stopping ntp
starting ntp
```
does anyone know how to fix this? can i kill ntp before i log out or something? any and all help is greatly appreciated!

---

### Post by Crafty Kisses on 2009-01-15
That's really weird, try looking at your NTP log and see if there's anything out of the ordinary:
```
/var/log/ntp.log
```
I know this was a problem a few months back as well. Look at your config file too, see if there's anything there out of the ordinary:
```
/etc/ntp.conf
```
Not sure if this could help/solve the issue but I know you can stop some of the NTP services from boot by doing the following:
```
/sbin/chkconfig ntp on
```
You can also stop it by doing the following:
```
/sbin/chkconfig ntp stop
```

---

### Post by mjheagle8 on 2009-01-15
what should i look for?
there is no ntp.log.
and the last two commands didnt work for me. said that there is no chkconfig.

---

