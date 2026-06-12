---
title: "connectivity problems after updates"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by jfloydb on 2009-02-26
I re-installed 8.10. Things seemed to be getting off to a good start; UNTIL I downloaded the updates (259 of them). Now I cannot connect to the internet using my ethernet cable. Can someone please tell me how to restore my ethernet internet connection (so I can address my wireless and screen resolution problems at a later date...)

---

### Post by Michael.Godawski on 2009-02-27
hi,
some start-up info would be helpful. Please post the output of these terminal commands:

```
sudo lshw -C network
cat /etc/network/interfaces
ifconfig
```

---

### Post by jfloydb on 2009-04-26
The answer is: upgrade to 9.04 for the acer Aspire One... Thanks everyone...

---

