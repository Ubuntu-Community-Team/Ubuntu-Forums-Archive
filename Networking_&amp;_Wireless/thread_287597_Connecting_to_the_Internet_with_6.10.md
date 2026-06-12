---
title: "Connecting to the Internet with 6.10"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by ApolloCS on 2006-10-29
I have a cable connection, through a usb modem that worked flawlessly in 6.06 and after upgrading to 6.10 i could no longer connect to the internet.

in 6.06 at Networking Settings appers Ethernet connection at eth0 and thus the internet works fine

in 6.10 i don't get anything there, just the usual dial up modem and nothing else


any help?

---

### Post by ApolloCS on 2006-10-29
*bump*

:???:

---

### Post by chaotic_euphoria on 2006-10-30
This is for 6.06 but it might help with 6.10 too.  It's is a link to a thread with a similar problem.  read through it and there is a couple of posts that have some comands in the terminal that might help you.

---

### Post by chaotic_euphoria on 2006-10-30
lol forgot to put the link! [http://ubuntuforums.org/showthread.php?t=282663](http://ubuntuforums.org/showthread.php?t=282663)

---

### Post by GCR on 2006-10-30
Whats the output of ifconfig ? Try to ping to a site. Is it successful
?

---

### Post by ApolloCS on 2006-10-30
> **GCR said:**
> Whats the output of ifconfig ? Try to ping to a site. Is it successful
?

apollo@apollo-station:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



i guess eth0 is not even configured. how can i do it? i already tried some commands like sudo ifconfig eth0 up and nothing worked.

---

