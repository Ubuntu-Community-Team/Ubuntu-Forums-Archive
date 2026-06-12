---
title: "lost the internet"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by WriteGirl on 2008-12-04
I just got my system board replaced/fixed for the second time and when I got my laptop again, I can't connect to the internet. It doesn't show me any options to use as a connection when I click it and if I try to connect to hidden wireless connection or add VPN connection, I can find the right one, but my computer tries to use it and says it can't find it. The first time I got the system board replaced, it worked fine, so I'm not sure what's going on this time. 

Thanks!

---

### Post by linux_tech on 2008-12-04
what is output of ```
ip addr show
```

---

### Post by WriteGirl on 2008-12-04
Here

```
1:<LOOPBACK,UP,LOWER_UP> mtu 16436 gdisc noqueue state UNKNOWN
  link/loopback 00:00:00:00:00:00 brb 00:00:00:00:00:00
  inet 127.0.0.1/8 scope host lo 
  inet6 ::1/128 scope host 
     validift forever preferred_lft forever
```

---

### Post by linux_tech on 2008-12-04
boot with the Ubuntu LiveCD  
run ```
sudo ifup eth0 --force
```
```
sudo ifup eth1 --force
```

---

### Post by linux_tech on 2008-12-04
what version of ubuntu do you have?

---

### Post by linux_tech on 2008-12-04
what is output of
```
sudo lshw -C network
```

---

