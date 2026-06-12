---
title: "Router does not detect wired connection"
date: 2013-12-24
forum: Networking &amp; Wireless
---

### Post by ProgramErgoSum on 2013-12-24
Hi,
When I connect a network cable from my laptop to the router, the router does not detect this connection. The LED for the port (on the router) does not turn on. However, with the same cable and router, when I connect my other laptop, the wired connection works. The wireless connection works successfully for both laptops. 

I have been working with this laptop for quite some time and there was never an issue until now. Most questions in this forum are around lack of internet connection i.e. their router has detected the connection. In my case though, the connection itself isn't detected.

Help !

Ubuntu-12.04, 64-bit.

```

user@host:~$ uname -a
Linux host 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Bucky Ball on 2013-12-24
How about the output from these two:

```
sudo lshw -C network
ifconfig
```

... with the cable plugged it. 

Have you confirmed this is NOT the slot on the router that is dead? There's usually four. Try another.

---

### Post by ProgramErgoSum on 2013-12-24
Thanks for the quick response.

This is embarassing...I switched off the router (couldn't do earlier as the other laptop needed to be online), turned on again, plugged the cable. And, now it works !

In case, it dies out again, I will come back.

---

### Post by Bucky Ball on 2013-12-24
It happens. Perhaps give it twenty four hours then mark the thread as solved if all good. Fingers crossed. ;)

---

