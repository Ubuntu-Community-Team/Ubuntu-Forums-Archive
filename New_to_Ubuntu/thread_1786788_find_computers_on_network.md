---
title: "find computers on network"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by ashesdangol on 2011-06-20
How to find available computers and its users on network?

I tried arp -a, it shows me the ip address of available computer on my network but how do i find who the user is of that ip address.

Thank you in advance

---

### Post by crispy_420 on 2011-06-20
You want to find who is on the PC right then?

---

### Post by Frogs Hair on 2011-06-20
You may find something helpful here .[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by ashesdangol on 2011-06-20
I am u**sing ubuntu** and my **friend is mac**..we are using **same router**. what I am trying to learn is how to** find** the **available compute**r that is **my fren's mac**,,,although i know his username and ip address by using his mac. But i was wondering if i didnt know **who is connected** on my **network.** How would i find **who the user is** and t**he computer name/ip **on my network?

So far I understood ..by doing **arp -a gives** me** computer name and ip on my network**. But how do i find its user?

---

### Post by ashesdangol on 2011-06-20
> **crispy_420 said:**
> You want to find who is on the PC right then?

 I am u**sing ubuntu** and my **friend is mac**..we are using **same router**. what I am trying to learn is how to** find** the **available compute**r that is **my fren's mac**,,,although i know his username and ip address by using his mac. But i was wondering if i didnt know **who is connected** on my **network.** How would i find **who the user is** and t**he computer name/ip **on my network?

So far I understood ..by doing **arp -a gives** me** computer name and ip on my network**. But how do i find its user?

---

### Post by doas777 on 2011-06-20
you cannot determine the user of the computer based on network stack information (at least not without some sophisticated sniffing of their traffic, which is very hard on a switched network).

your best bet is to discover a machines IP address, and connect to it using ssh or another remote shell, and examine the ttys or the output of the command 
```
w
``` or ```
who
```

if you cannot connect, then you probably won't be able to get this info.

---

### Post by idoitprone on 2011-06-20
nvm

---

