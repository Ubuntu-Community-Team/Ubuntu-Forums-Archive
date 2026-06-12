---
title: "remove web installed games"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by grewolf on 2010-01-30
I have added some demos loki and some games from getdeb.net and now wish to remove them.  I have tried to use the loki uninstaller with no success.  ```
sudo: loki_uninstall: command not found
```
Looked in Ubuntu software Center and Synaptic and not able to find.  Loki is no longer in business.  and this site for the uninstall tool tells me nothing [http://icculus.org/loki_setup/]("http://icculus.org/loki_setup/").  

The games are gets and guns demo Majesty demo

---

### Post by Leppie on 2010-01-30
you can find the packages with dpkg:
```
dpkg -l | grep <partialgamename>
```

---

### Post by grewolf on 2010-02-28
> **Leppie said:**
> you can find the packages with dpkg:
```
dpkg -l | grep <partialgamename>
```

Just leaves me with the terminal bar
```
jwilson@Crash-Burn:~$ dpkg -l | grep Jets
jwilson@Crash-Burn:~$ 
```

---

