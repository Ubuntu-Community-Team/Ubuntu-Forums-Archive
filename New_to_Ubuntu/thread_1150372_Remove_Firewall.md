---
title: "Remove Firewall"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Frank_F on 2009-05-06
Hello

I am currently behind a router, and would prefer to remove my software firewall in ubuntu 8.01......what is the command line


Thanks

---

### Post by nhasian on 2009-05-06
which firewall package did you install?

---

### Post by HermanAB on 2009-05-06
Basically just:
iptables -F

---

### Post by Frank_F on 2009-05-06
I have firestarter as my gui.....dumb question, by removing this will it remove the firewall (iptables) ? 

Thanks

---

### Post by Frank_F on 2009-05-06
doesnt iptables -F just temporarily remove the firewall and upon reboot the firewall will be back ?  thanks

---

### Post by nhasian on 2009-05-06
removing firestarter will only remove the graphic front end tool.  to flush all the rules from the firewall do like HermanAB suggested:

```
iptables -F
```

---

### Post by Frank_F on 2009-05-06
thats what I thought thanks. But isnt iptables -F temporary as well ?

---

### Post by Didius Falco on 2009-05-06
Yes, it is temporary, according to the man page, but I just added it to my start-up program list successfully, so you could do that and move it to the top of the list and it _should_ turn it off at every boot.

---

