---
title: "Networking problem 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Lamb Chop on 2008-04-26
Hello people,

I've had a 7.10 server (ubuntu server edition) running in a datacenter for quite some time and all was fine until I recently upgraded to 8.04 (using do-release-upgrade). This all went fine and after the reboot things seemed normal. BUT, after the update my networking went tits up. I can view the server's apache2 server, do ftp and login through ssh from a remote machine, but the server has no "internet" which means i cannot connect to any other servers from my server. ping google.com for instance wouldn't work. When I run "apt-get update" it cannot connect to the update servers. My network device seems configured properly so my guess is that DNS might be wrong? I hope anybody out here can help :)

Thanks in advance :)

```

eth0      Link encap:Ethernet  HWaddr 00:16:e6:d3:d6:41
          inet addr:85.17.181.26  Bcast:85.17.181.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fed3:d641/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:136244 (133.0 KB)  TX bytes:217577 (212.4 KB)
          Interrupt:16

```

---

### Post by Monicker on 2008-04-26
Can you ping remote sites by ip address? Try to ping 4.2.2.2

Also, give the results of the following commands:


```
netstat -rn

cat /etc/resolv.conf
```

---

