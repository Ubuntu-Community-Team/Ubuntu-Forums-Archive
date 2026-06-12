---
title: "flash player wont install on 9.04"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by brando337 on 2009-09-03
hey everyone. I just installed 9.04 32 bit on my laptop from a usb drive, I downloaded flash player 10 from their site and when i goto install it I get an error message that says: Error: Dependency is not satisfiable: libnspr4-dev----any ideas? Thanks

---

### Post by zerhacke on 2009-09-03
In a terminal, type the following

sudo apt-get install ubuntu-restricted-extras

and press enter, then give it your password.  This will install flash and a host of other useful stuff you probably want to have.

---

### Post by brando337 on 2009-09-03
when i type that in the terminal I get this back
brandon@SeRvO:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for brandon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by snowpine on 2009-09-03
Try:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Or, if all you want is Flash: 

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by CatKiller on 2009-09-03
*ubuntu-restricted-extras* is in the Multiverse repository. If it's not enabled, you can do so with the System &#8594; Administration &#8594; Software Sources tool. It's described as "Software restricted by copyright or legal issues (multiverse)."

---

### Post by brando337 on 2009-09-03
Yeah that did it. damn you guys are geniuses, I need to learn these commands..THANKS!

---

