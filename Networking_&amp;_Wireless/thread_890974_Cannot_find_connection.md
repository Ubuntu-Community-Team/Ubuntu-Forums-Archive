---
title: "Cannot find connection"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Rickyk on 2008-08-15
Hello Everyone,
i have a problem my little bro somehow got on my computer and was messing around on it (hes 3) and now the network manager does not show any connections but the computer im on now has perfect internet and is right next to my other one that is running ubuntu.
When i click on network manager it does not show a connection tom connect to like before any help pl0x?

Thanks,
Ricky

---

### Post by nickdbliss on 2008-08-15
> **Rickyk said:**
> Hello Everyone,
i have a problem my little bro somehow got on my computer and was messing around on it (hes 3) and now the network manager does not show any connections but the computer im on now has perfect internet and is right next to my other one that is running ubuntu.
When i click on network manager it does not show a connection tom connect to like before any help pl0x?

Thanks,
Ricky

go to terminal n give the output of code :
iwlist scan

---

### Post by Rickyk on 2008-08-15
I put that in and it says 

"
lo   interface dosent support scanning
eth0  interface doesnt support scanning
eth1 no scan results
irda0 interface doesnt support scanning
"

And this computer had internet 5 mins before my bro got on my computer.

---

### Post by Rickyk on 2008-08-15
help please

---

### Post by Iowan on 2008-08-15
Post contents of **/etc/network/interfaces** and results of **ifconfig -a**.

---

