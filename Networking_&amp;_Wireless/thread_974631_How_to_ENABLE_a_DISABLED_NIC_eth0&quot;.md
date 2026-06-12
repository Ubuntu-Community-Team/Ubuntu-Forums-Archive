---
title: "How to ENABLE a DISABLED NIC eth0&quot;"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by lincoln32 on 2008-11-07
worked on first install then added synce and net card inop since but working on duel boot vista card works fine. formatted and reloaded with home partion and still not working. connected temp with wifi ecs 945gct m/1333 ver 3 with new bios e2200
todd@todd-desktop:~$ lshal | grep net.interface 
  net.interface = 'eth0'  (string)
todd@todd-desktop:~$ 
todd@todd-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93400 (91.2 KB)  TX bytes:93400 (91.2 KB)

todd@todd-desktop:~$ 
and module seems to be installed, any ideas????? Thanks

---

