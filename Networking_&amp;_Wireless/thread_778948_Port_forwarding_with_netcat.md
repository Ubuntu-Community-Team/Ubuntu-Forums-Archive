---
title: "Port forwarding with netcat"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by emreege on 2008-05-02
Hi;
I have 3 machines say A, B and C and i want send data from A to C over B. A->B->C.
I am using netcat. I must forward the incoming port of machine B (say 5000) to the machine C port. (say 10000). That is:
A:5000 -> B:5000 - B:10000 -> C:10000

I have used in B
netcat -l -p 5000 | netcat C_IP_NUMBER 10000

It sends data for nearly 1 or 2 seconds then the connection break.
How can i solve this?

---

### Post by emreege on 2008-05-03
Any idea?

---

### Post by go_beep_yourself on 2011-03-22
I don't have the answer. I am trying to do the same thing you are. Did you ever figure out how to do it, and if you did would you let me know?

Thanks

---

