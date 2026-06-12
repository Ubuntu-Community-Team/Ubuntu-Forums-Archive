---
title: "how do i turn off all network devices via terminal"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by cosmoshell on 2009-08-03
how do i turn off all network devices via terminal?

---

### Post by juancarlospaco on 2009-08-03
**sudo /etc/init.d/networking stop**

---

### Post by wojox on 2009-08-03
```
sudo /etc/init.d/networking stop
```

---

### Post by cosmoshell on 2009-08-03
doesent work neather does ifdown -a

---

### Post by superprash2003 on 2009-08-04
the above command should work.. you mean network devices still continue to function even after typing that command?

---

### Post by cosmoshell on 2009-08-04
yes however the problem is solved. 
sudo ifconfig eth0 down. works
sudo ifconfig eth0 up. dosent work. sudo dhclient does work.

---

### Post by wizard10000 on 2009-08-04
> **cosmoshell said:**
> yes however the problem is solved. 
sudo ifconfig eth0 down. works
sudo ifconfig eth0 up. dosent work. sudo dhclient does work.

Strange.  Works on my test box (32-bit Jaunty).  That's how I gave the thing a static IP - added a MAC reservation on the router and then just restarted eth0.

---

