---
title: "recover sudo in ubuntu 8.04"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by jagaprakash on 2008-12-02
i can,t get sudo in my ubuntu 8.04. please anybody help me to recover sudo...

---

### Post by aysiu on 2008-12-02
Here you go:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by prshah on 2008-12-03
> **jagaprakash said:**
> i can,t get sudo in my ubuntu 8.04. please anybody help me to recover sudo...

If you get an error "Cannot resolve hostname" (or words to that effect) when using sudo in a terminal (Applications, Accessories, Terminal) see below for a solution.

you have to edit /etc/hosts and make sure that 127.0.0.1 is linked to your hostname. But to edit the /etc/hosts file, you need to use sudo; you can get around this catch 22 situation by either rebooting to recovery mode, 

== OR == 

Open a terminal (Applications-Accessories-Terminal) then give the command
```

hostname
```
Note the name shown and then give the command
```

gksudo
```

Give your password, then a window will open up, in the command box, type
```
gedit /etc/hosts
```

and choose "user" as "root", then OK/Enter. A new window will open up, look for the line beginning with
```
127.0.0.1
```

and change the word following that number to the same as in the hostname command above Note that case (UPPER/lower/Mixed) is important. Then save and quit.

Now your sudo should be working fine. (No need to reboot)

---

