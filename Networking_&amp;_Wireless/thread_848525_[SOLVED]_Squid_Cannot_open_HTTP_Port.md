---
title: "[SOLVED] Squid: Cannot open HTTP Port"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by computer_freak_8 on 2008-07-03
I don't understand what is happening. I have port 3128 free, I closed down LAMPP, but when I try to start Squid, I get what is says in the attachment "errors_from_squid.txt".

My squid.conf file is too big to attach.


I have tried both the 

```
sudo squid
```

and 

```
sudo /etc/init.d/squid start
```

commands, both do the same thing (shown above).

---

### Post by computer_freak_8 on 2008-07-08
I solved my problem. I reinstalled Squid, but what really did it was one line in my /etc/squid/squid.conf file.

I had to change 

```
http_port 127.0.0.1:3128
```

to

```
http_port 3128 transparent
```

and then restart squid using 

```
sudo /etc/init.d/squid restart
```


I hope this helps others with the same problem.


computer_freak_8

---

