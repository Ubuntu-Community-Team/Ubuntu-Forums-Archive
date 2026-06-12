---
title: "Reconnecting to a wired LAN after the connection is dropped"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by SGC on 2005-05-03
Is there is another way to reconnect to a wired LAN after the connection is dropped beside restarting the computer?  I searched the fourm and I can only find solutions for wireless lans.

---

### Post by lao_V on 2005-05-03
Yes, most of the tasks in Linux can be achieved without having to re-start the computer. To re-connect your wired lan (eth0) you could try the following:

 ```
sudo ifup eth0
``` 

or 

 ```
sudo /etc/init.d/networking restart
```

---

### Post by SGC on 2005-05-03
Thanks lao_V, 

Is there is an automatic way to do the same thing?

---

### Post by lao_V on 2005-05-04
You should try to investigate why exactly your wired network "drops". Normally, this should only happen with a wireless connection.

---

### Post by SGC on 2005-05-04
[QUOTE=lao_V]You should try to investigate why exactly your wired network "drops". Normally, this should only happen with a wireless connection.[/QUOTE]
 The connection dropping does not happens alot, but to have a way to reconnect when that happens will be usefull, especially when downloading a large file over the night.

---

### Post by lao_V on 2005-05-04
An inefficient way to do that would be to put the line "/etc/init.d/networking restart" in cron/kcron which can execute that task for you at a given time.

Alternatively, if you can have a script that checks every so often to see if your network if up or not. Not really sure what code/line could achieve this. :?

---

### Post by SGC on 2005-05-04
Thanks lao_V very much for you help

---

### Post by lao_V on 2005-05-04
you're welcome!

---

