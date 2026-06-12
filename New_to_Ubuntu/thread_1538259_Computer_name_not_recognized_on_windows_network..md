---
title: "Computer name not recognized on windows network."
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Rayn on 2010-07-24
I upgraded to 10.04.  I used to be able to access the box via \\myth (the computer name).  I can no longer.  I have editted my host file to point to the static IP and that works, but what I want to know is why this has happened?  What can I do to fix it?
```
root@myth:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:60:a1:5e:15
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fea1:5e15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:204025578 (204.0 MB)  TX bytes:12055121 (12.0 MB)
          Interrupt:21 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5814973 (5.8 MB)  TX bytes:5814973 (5.8 MB)

```

---

### Post by Rayn on 2010-07-25
Solved.

NMBD was failing to start due to a test param call to see if netbios was disabled or not.

This parameter was missing from my smb.conf file probably because I did not merge in the changes and just kept what I had.

The solution is to add the following line in smb.conf and restart nmb.  It should load on boot thereafter:

```
disable netbios = no
```

Computer now appears in Windows network and is accessible via computer name.  If this doesn't work for you, verify the workgroup that samba is in matches your windows network.

---

### Post by Goolie on 2010-07-25
Awesome, I never solve my own problems, I just happen to recursively search Google. . . never am sure how I manage to do things.  

Sometimes, I just forget and remember then later on.

O.o

---

