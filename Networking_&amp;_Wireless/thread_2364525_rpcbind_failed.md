---
title: "rpcbind failed"
date: 2017-06-24
forum: Networking &amp; Wireless
---

### Post by zkab on 2017-06-24
My server runs 16.04.2 LTS (4.8.0-56) and after a reboot I receive following:

jurka@farbaute:~$ dmesg | grep -i fail
jurka@farbaute:~$ cat /var/log/syslog | grep -i fail
Jun 24 09:29:52 farbaute thermald[675]: sysfs read failed constraint_0_max_power_uw
Jun 24 09:30:06 farbaute rpcbind[986]: rpcbind: xdr_/run/rpcbind/rpcbind.xdr: failed
Jun 24 09:30:06 farbaute rpcbind[986]: rpcbind: xdr_/run/rpcbind/portmap.xdr: failed
Jun 24 09:46:05 farbaute thermald[663]: sysfs read failed constraint_0_max_power_uw
Jun 24 09:46:19 farbaute rpcbind[993]: rpcbind: xdr_/run/rpcbind/rpcbind.xdr: failed
Jun 24 09:46:19 farbaute rpcbind[993]: rpcbind: xdr_/run/rpcbind/portmap.xdr: failed
Jun 24 09:50:27 farbaute thermald[662]: sysfs read failed constraint_0_max_power_uw
Jun 24 09:50:40 farbaute rpcbind[984]: rpcbind: xdr_/run/rpcbind/rpcbind.xdr: failed
Jun 24 09:50:40 farbaute rpcbind[984]: rpcbind: xdr_/run/rpcbind/portmap.xdr: failed

What is wrong ?

---

### Post by steeldriver on 2017-06-24
Hmm... rpcbind isn't normally running on my 16.04 box but if I start it I see the same

```

steeldriver@xenial-vm:~/forums/tests$ sudo systemctl start rpcbind.service
[sudo] password for steeldriver:
steeldriver@xenial-vm:~/forums/tests$ systemctl status rpcbind.service
&#9679; rpcbind.service - RPC bind portmap service
   Loaded: loaded (/lib/systemd/system/rpcbind.service; indirect; vendor preset: enabled)
  Drop-In: /run/systemd/generator/rpcbind.service.d
           &#9492;&#9472;50-rpcbind-$portmap.conf
   Active: active (running) since Sat 2017-06-24 08:57:16 EDT; 4s ago
 Main PID: 14928 (rpcbind)
   CGroup: /system.slice/rpcbind.service
           &#9492;&#9472;14928 /sbin/rpcbind -f -w

Jun 24 08:57:16 xenial-vm systemd[1]: Starting RPC bind portmap service...
Jun 24 08:57:16 xenial-vm rpcbind[14928]: rpcbind: xdr_/run/rpcbind/rpcbind.xdr: failed
Jun 24 08:57:16 xenial-vm rpcbind[14928]: rpcbind: xdr_/run/rpcbind/portmap.xdr: failed
Jun 24 08:57:17 xenial-vm systemd[1]: Started RPC bind portmap service.

```

It doesn't appear to prevent the service from starting - are you actually having any rpc / portmapper issues?

---

### Post by zkab on 2017-06-24
NFS is installed on the server ... both NFS Client & server ... could that be the problem ?

---

### Post by steeldriver on 2017-06-24
It appears to be a known bug - as described here: [In Ubuntu 16.04 not start rpcbind on boot]("https://askubuntu.com/questions/771319/in-ubuntu-16-04-not-start-rpcbind-on-boot/771706")

Actually it looks like the service *does *start - so I'd suggest only trying the patch if you are experiencing issues beyond simply getting an error in your dmesg log)

---

### Post by zkab on 2017-06-25
OK - strange that the bug has not been fixed yet ...

---

