---
title: "net connection in pshyco"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by danieldangol@yahoo.com on 2009-04-04
i'm using linux since 6.o4 long term support version.literally to be said i don't have any geek knowledge in *nix but some how i used it for internet security.
recently i'm uploaded to 8.10.
i use tp link 8620 chinesse router .
(in which there is no option for saving username and password inside router)
_ i simply make pppoeconf
and then do the sudo pon dsl-provider
i'm amazed that it does't show connection.
then go to network manager 
i don't know what i have done there and connection established
but after the reboot. 
it doesn't seem to connect.
please help me
i'm jammed between the terminal and the network manager 
amen

---

### Post by zvacet on 2009-04-04
```
sudo /etc/init.d/networking restart
```

---

### Post by danieldangol@yahoo.com on 2009-04-05
thank u 4 advice
but i solve it by logging off and again logging on

---

