---
title: "How Do I Stop Network Manager?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by AxelMan0 on 2009-08-14
sudo /etc/dbus-1/event.d/25NetworkManager stop
and
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

do not work, they say 'command not found'.

I'm trying to use my phone as a bluetooth modem but I need to disable network manager first.

---

### Post by sblunix on 2009-08-14
Go ahead and go to "System>Administration>System Monitor" and kill it from there...

---

### Post by zeroseven0183 on 2009-08-14
How about this

```
sudo /etc/init.d/NetworkManager stop
```

---

### Post by AxelMan0 on 2009-08-15
.

---

### Post by zeroseven0183 on 2009-08-18
Were you able to do a stop on your Network Manager?

---

### Post by guix on 2009-11-11
I need too...

---

### Post by OffAxis on 2009-11-11
in 9.10 it's 

```
sudo service network-manager stop
```

Previous to that I believe it's


```
sudo /etc/init.d/network-manager stop
```

---

