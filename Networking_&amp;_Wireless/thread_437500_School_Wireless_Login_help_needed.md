---
title: "School Wireless Login help needed"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Atow on 2007-05-08
alrighty, now this one is really kinda tricky and i couldt find the options in the knetowrk-manager to be able to use the wireless at my college. here are the instructions for windows so you have sorta an idea on what im facing to try and login there. 

[http://www.olympic.edu/stafffaculty/informationtechnology/oc+wireless+network.htm](http://www.olympic.edu/stafffaculty/informationtechnology/oc+wireless+network.htm)

i tried asking IT there but their like....... "i tried linux once but it took to much space so i got rid of it." the other guys had never tried before so yeah

thoughts, ideas, opinions?

---

### Post by josephus on 2007-05-08
never done this before myself but try xsupplicant to get PEAP

---

### Post by Atow on 2007-05-09
> **josephus said:**
> never done this before myself but try xsupplicant to get PEAP

alright im working on trying to make it work but im having some errors during the compile process 

the current one im getting while typing in ./configure  

> configure: error: cannot find sources (src/xsup_driver.c) in . or ..

so im working on getting that to work

---

### Post by jfinkels on 2007-05-09
> **Atow said:**
> alright im working on trying to make it work but im having some errors during the compile process 

the current one im getting while typing in ./configure  



so im working on getting that to work

```
sudo aptitude install xsupplicant
```

---

### Post by Atow on 2007-05-09
> **jfinkels said:**
> ```
sudo aptitude install xsupplicant
```

sweet it seems like it installed fine but looking through the config im confused on how exactly this works. will it change the options features in my knetwork-manager? and will it mess up my home normal WEP configuration?

---

### Post by jfinkels on 2007-05-09
> **Atow said:**
> sweet it seems like it installed fine but looking through the config im confused on how exactly this works. will it change the options features in my knetwork-manager? and will it mess up my home normal WEP configuration?

I'm afraid I don't know anything about knetwork-manager (I'm purely GNOME) and I know even less about xsupplicant. It probably won't screw up your normal home network connection, but who knows? Somebody does, but not me.

Take a look at the man page for xsupplicant:
```
man xsupplicant
```

---

### Post by Atow on 2007-05-09
> **jfinkels said:**
> I'm afraid I don't know anything about knetwork-manager (I'm purely GNOME) and I know even less about xsupplicant. It probably won't screw up your normal home network connection, but who knows? Somebody does, but not me.

Take a look at the man page for xsupplicant:
```
man xsupplicant
```

ok i think i got it working i can try and enter my information but it doesnt seem to configure. it stops at 28%. it has alot of non-needed options and im wondering if those are confusing it

---

