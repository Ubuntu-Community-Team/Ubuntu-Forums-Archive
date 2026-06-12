---
title: "Ubuntu systemd-resolve"
date: 2021-04-03
forum: Networking &amp; Wireless
---

### Post by juanbosh on 2021-04-03
i have no idea how works this service, but if i do systemctl status systemd-resolved, 

systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-04-03 20:54:15 CEST; 5h 37min ago
       Docs: man:systemd-resolved.service(8)
             [https://www.freedesktop.org/wiki/Software/systemd/resolved](https://www.freedesktop.org/wiki/Software/systemd/resolved)
             [https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers](https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers)
             [https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients](https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients)
   Main PID: 622 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 9407)
     Memory: 8.8M
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;622 /lib/systemd/systemd-resolved

abr 04 01:42:50 spiderman systemd-resolved[622]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2>
abr 04 01:47:50 spiderman systemd-resolved[622]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2>

i have read than there are a symbolic link in /etc/resolv.conf for me is point to  /run/systemd/resolve/stub-resolv.conf and i dont know if this is the correct link. or how to fix the error.

---

### Post by chili555 on 2021-04-04
> i have read than there are a symbolic link in /etc/resolv.conf for me is point to /run/systemd/resolve/stub-resolv.conf and i dont know if this is the correct link.Let's find out. Please open a terminal and run:

```
ls -al /etc/resolv.conf
```Please post the result.

The usual and correctly working result is:

```
lrwxrwxrwx 1 root root 32 May 13  2020 /etc/resolv.conf -> /run/systemd/resolve/resolv.conf
```If not, we'll fix it.

A link to stub-resolv.conf is probably fine.

---

### Post by juanbosh on 2021-04-04
Thanks i relink the resolv.conf

root@spiderman:/etc# ls resol* -la
lrwxrwxrwx 1 root root 39 abr  3 20:33 resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
root@spiderman:/etc# rm resolv.conf 
root@spiderman:/etc# ln -s /run/systemd/resolve/resolv.conf resolv.conf
root@spiderman:/etc# ls resol* -la
lrwxrwxrwx 1 root root 32 abr  5 03:12 resolv.conf -> /run/systemd/resolve/resolv.conf

---

