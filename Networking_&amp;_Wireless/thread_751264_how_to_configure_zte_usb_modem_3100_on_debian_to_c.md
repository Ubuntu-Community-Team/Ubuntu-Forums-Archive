---
title: "how to configure zte usb modem 3100 on debian to connect internet"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by debianLAM on 2008-04-10
hi 

i am using a debian linux  
i connected a zte usb modem 3100 
but at here  i dont know how to configure a modem 
and create a new connection 
if any one have idea please give me a solution to solve my problem


thanks 
debianlam

---

### Post by SpaceTeddy on 2008-04-10
```
sudo apt-get install pppoeconf
sudo pppoeconf
```

that should do the job... if you modem was detected, this will let you configure the connection to show up in network manager.

---

### Post by debianLAM on 2008-04-10
ok thanks i will try your solution

---

