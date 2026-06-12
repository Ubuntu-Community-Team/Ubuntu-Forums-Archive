---
title: "unable to resolve host"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by quarkhirad on 2009-06-20
Hi. Okay now i dont know how but after i restarted my comp whenever i type the following in terminal  

```


khirad@jeena:~$ sudo apt-get update 
sudo: unable to resolve host jeena
[sudo] password for khirad: 


```

After entering my password it executes the command. Its just that i takes longer time and Its really bugging.

Please help.

---

### Post by nandemonai on 2009-06-20
Looks like something in your hosts file might be messed up.

Please post the output of this in terminal:

```
cat /etc/hosts
```

Edit:

There should be a line in there saying:

127.0.0.1 localhost jeena

Or:

127.0.0.1 localhost
127.0.0.1 jeena

---

### Post by zvacet on 2009-06-20
Before you do anything read [this.]("https://help.ubuntu.com/community/Nano")


Boot in recovery mode and type


```
nano /etc/hosts
```

and first two lines should be 

127.0.0.1 localhost
127.0.1.1 jeena

ctrl+O for saving file and ctrl+X for exit.

---

### Post by quarkhirad on 2009-06-23
```
nano /etc/hosts
```

and first two lines should be 

127.0.0.1 localhost
127.0.1.1 jeena

ctrl+O for saving file and ctrl+X for exit.[/QUOTE]


Thanks it read as 

12.0.1.1 jeena.dhabhr

changed it and now its ok

thanks

---

