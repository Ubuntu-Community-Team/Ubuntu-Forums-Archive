---
title: "having trouble with wired"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by angelice on 2010-04-07
sorry i am still somewhat of a newb with linux distros however am not a newb all around ... i am having some trouble getting the wired interenet to work and was hoping someone could point me in the right direction so i can get this up and running correctly ... any help would be greatly appreciated ... this is slitaz ... so yeah ... just making sure i made that evident another member was having somewhat similar issues and i was just hoping that someone would have an idea

---

### Post by whoop on 2010-04-07
You could start by stating what the exact problem is...
post output of:
```

ifconfig

```

---

### Post by angelice on 2010-04-07
sorry i thought when i edited i put that in it says unable to start command: ifconfig sorry about that

---

### Post by whoop on 2010-04-07
Huh? what does:
```

sudo aptitude search net-tools

```
give?

---

### Post by angelice on 2010-04-07
> **whoop said:**
> Huh? what does:
```

sudo aptitude search net-tools

```
give?
 
oh ... the network status says "unable to start ifconfig" that sorry when i wrote the post the first time all this info was there but ... i hit wrong button and had to rewrite it and i guess i forgot some stuff ..

---

### Post by whoop on 2010-04-07
Still, if you enter:
sudo aptitude search net-tools
in a terminal, what do you get?

---

### Post by angelice on 2010-04-07
when i run ifconfig through the terminal it says 
"link encap:local llopback
inet addr:127.0.0.1 mask : 255.0.0.0
up loopback running mtu:16436 metric:1
rx packets:0 errors:0 dropped:0 overruns:0 frame:0 
tx packets :0 errors:0 dropped:0 overruns:0 carier:0
collisions:o txqueueler :0
rx bytes:0 (0.0 B) tx bytes:0 (0.0 B)
Maybe this is what was wanted?
so obviously it has no connection whatsoever ... and im not sure what to do ... my internet works fine through the vista side just not through this side
when i run sudo aptitude search net-tools it says 
-sh: sudo: not found
 
Sorry misunderstood question first time ... sorry its been a long day already ..

---

### Post by angelice on 2010-04-07
so do we have no idea what to do ??? cause im lost and i cannot figure out what to do next obviously its seeing some kind of connection hence the ip adress ... but its unable to connect or send ??? so i dont know what to do

---

### Post by Paqman on 2010-04-07
Have you tried the [SliTaz forum]("http://forum.slitaz.org/")? Folks there will be more familiar with the system.

---

### Post by angelice on 2010-04-07
k just when i searched the interenet someone was talking about siltaz wireless connections?

---

### Post by angelice on 2010-04-07
and there kinda not answering me on the other site i was hoping since someone else had gotten help for a similar issue through yall ... so you seemed by far more helpful i figure it couldnt hurt to try

---

