---
title: "Wired Connection Problems"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by mlnsharma on 2008-10-05
I am new to Ubuntu and Linux too. I have recently installed ubuntu 8.04 in my system. My ethernet card is not configured automatically. So i tried configuring it manually. Even then it was not detected.I connect in a Lan to the ISP.

              I use an INTEX Ethernet Card. In Windows we have driver CD to setup the connection. So i had no problems in Win'XP. 

              DO we need something similar to driver setup in UBUNTU. Can anyone guide me through this problem??
 
              I have posted earlier in different threads and got various responses, which i dont understand and they hav asked me to start a new thread. Thanks for their suggestion. Kindly give me a solution !!

---

### Post by jmbargar on 2008-10-05
Buy a new network card is the easiest solution. The wired cards based on Realtek chipsets usually don't cause problems for configuring it with Ubuntu systems. It cost about 5&#8364;.

---

### Post by cariboo on 2008-10-05
We need more information to help you. Please post the output of:

```
lspci
```

and 

```
sudo lshw -C network
```

Both commands have to run in a Applications--Accessories--Terminal. Copy and paste the output in your next post.

Jim

---

