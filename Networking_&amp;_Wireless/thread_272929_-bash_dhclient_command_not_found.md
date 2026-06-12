---
title: "-bash: dhclient: command not found"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by twiggy on 2006-10-07
Hi all,

I have just got my server back up and running after a move and for some reason can not get dhclient to work.

The net is up fine, computer connected to it fine, external ip and internal ips working.  This is the output i get

```

jon@betty:~$ dhclient eth0
-bash: dhclient: command not found
jon@betty:~$ sudo su
root@betty:/home/jon# dhclient eth0
bash: dhclient: command not found

```

any ideas please?

Cheers

Twiggy

---

### Post by davesgonebananas on 2006-10-07
On my system dhclient is a symlink to dhclient3 and they reside in /sbin.  Try /sbin/dhclient3 or /sbin/dhclient.

```
lrwxrwxrwx 1 root root      9 2006-10-06 20:49 /sbin/dhclient -> dhclient3
-rwxr-xr-x 1 root root 422324 2006-05-05 16:02 /sbin/dhclient3

```

If the symlink is missing you could recreate it by typing

```
ln -s /sbin/dhclient3 /sbin/dhclient
```

---

### Post by twistedtwig on 2006-10-09
Hi,

I dont seem to have a dhclient of any form in /sbin/

i did locate dhclient3 and found nothing.

had a look in /etc and /etc/init.d and found nothing that looked like it.

I am most confused to be honest.

---

### Post by amo-ej1 on 2006-10-09
with me (i don't think edgy will differ from dapper on this) it is in the package dhcp3-client and dhcp3-common. Are these installed ?

---

### Post by twistedtwig on 2006-10-09
Wooh!

that was the error... i swear it used to be installed as i KNOW i have used it before.  Very odd.  But THANK YOU!!!!!!!!!!!!

one VERY happy person on a wet and cold monday morning :D

---

