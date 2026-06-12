---
title: "Network History"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by mackayam on 2011-08-06
My System Monitor says that I am receiving stuff over the network. How do I find out *what* I am receiving?

---

### Post by haqking on 2011-08-06
> **mackayam said:**
> My System Monitor says that I am receiving stuff over the network. How do I find out *what* I am receiving?

use a network monitor such as Wireshark.

it is in the software centre or synaptic

---

### Post by mackayam on 2011-08-08
Thanks man, appreciate it.

---

### Post by carverj on 2011-08-09
Wireshark doesn't so much as give a history, but more allows you to capture the packets that enter a chosen interface to analyze the data at a time that you choose.
Is there a particular piece of data from the past that you are trying to capture?

---

### Post by mackayam on 2011-08-09
I share an internet connection with some neighbors at my apartment complex. About a week ago, the network slowed down (the administrator hasn't been able to fix anything) and my network monitor shows that my computer is *constantly* receiving about 45 - 50 kB/s. I want to know what I am receiving and try to figure out from where and why it's coming.

---

### Post by CVGH on 2011-08-09
```
sudo iptraf
```or:
```
netstat -atpvn
```

---

### Post by haqking on 2011-08-09
> **carverj said:**
> Wireshark doesn't so much as give a history, but more allows you to capture the packets that enter a chosen interface to analyze the data at a time that you choose.
Is there a particular piece of data from the past that you are trying to capture?

the title and the post are in conflict.

Yes wireshark can capture what you are trying to achieve

---

### Post by carverj on 2011-08-10
> the title and the post are in conflict.
Yes wireshark can capture what you are trying to achieve 
Yes I see and true, wireshark can capture and allow you to analyze the packets you seem to be receiving erroneously.
Etherape is another network monitoring tool which gives a graphical representation of connections that are established on the network.

---

