---
title: "sun-java6-bin, sun-java6-plugin, etc., not found"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Gameboyman99 on 2011-01-16
Sooooo

I got sun-java6-bin and all those other sun-java6-*'s installed on my Kubuntu 10.10 machine, but I'm having trouble FINDING it on my Xubuntu 10.10! Yes I have universal repositories enabled; at least I'm pretty sure :/ I did it with the console so I might be wrong x_x
Gimme an un-outdated link on how to get Xubuntu 10.10 universal repository open/usable
Or tell me why I can't find sun-java6-* on Xubuntu but I can on Kubuntu...
EDIT: As a bonus someone answer me as to why Sun/Java REFUSES to make the Java Firefox Plugin easier to install on Linux!!!!!!!!!!!!

Ty,

---

### Post by mick222 on 2011-01-16
Sun-java is in the partner repositories open software sources and tick the partner repository on the second tab. You can also do this in synaptic under settings repositories.

---

### Post by Jose Catre-Vandis on 2011-01-16
Just install:
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by mick222 on 2011-01-16
If the partner repos arent enabled that installs open java and the iced tea plugin i think.

---

### Post by Gameboyman99 on 2011-01-16
> **mick222 said:**
> Sun-java is in the partner repositories open software sources and tick the partner repository on the second tab. You can also do this in synaptic under settings repositories.
Define "partner repository" in greater detail and I might be onto it -_-
> Just install:
     Code:
     sudo apt-get install xubuntu-restricted-extras 
I did thet; it installed a bunch of things I dint need(but I did want Flash Player).
It dint do either the OpenJRE/JDK or IcedTea(both of which I hate and don't want) or any other Java thing...

[COLOR=Red]EDIT: K huge derp God took me 2hrs to figure that out ty got it now[/COLOR] -_-

---

### Post by mick222 on 2011-01-17
open synaptic 
system -> administration ->synaptic go to settings -> repositories go to the second tab and check the box next to canonical partners, close and reload in synaptic remove open-java and iced tea then instal sun java and the mozilla plugin.
 Open-java works fine for me so i have stopped using sun java.

---

### Post by Jose Catre-Vandis on 2011-01-19
> **mick222 said:**
> If the partner repos arent enabled that installs open java and the iced tea plugin i think.

Fair do's, and I agree this works OK in most situations for java, until I tried to use Andriod AppInventor, then I needed sun java :)

---

