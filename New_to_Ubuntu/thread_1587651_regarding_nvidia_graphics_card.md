---
title: "regarding nvidia graphics card"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by utkarshjadhav on 2010-10-03
Just installed LUCID LYNX .changed from 9.04.
I do have 1 GB nvidia graphiocs card.
When I opt for the Extra features through
change Desktop Background>visual effect
It didnt allow me to change to extra features.
Desktop effect could not be enabled.


At the same time I am  facing the problem-

regarding the 
1,UPDATE MANAGER
and upgrades through 
2.sudo apt-get install update 
sudo apt-get install upgrade
in first case and  later case it shows that it cannot fetch all files .although it fetches some files.


Are these problems connected?
I never got the graphics card problem in 9.04.
please help me!

---

### Post by andrewthomas on 2010-10-03
> **utkarshjadhav said:**
> Just installed LUCID LYNX .changed from 9.04.
I do have 1 GB nvidia graphiocs card.
When I opt for the Extra features through
change Desktop Background>visual effect
It didnt allow me to change to extra features.
Desktop effect could not be enabled.
 
 
At the same time I am facing the problem-
 
regarding the 
1,UPDATE MANAGER
and upgrades through 
2.sudo apt-get install update 
sudo apt-get install upgrade
in first case and later case it shows that it cannot fetch all files .although it fetches some files.
 
 
**Are these problems connected?**
I never got the graphics card problem in 9.04.
please help me!
 **Are these problems connected?**
 
**No.**
 
Post the full output of 
 
```
 
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by utkarshjadhav on 2010-10-04
output for 
```

sudo apt-get update
sudo apt-get upgrade

```-------------------------------------

```

root@utkarsh-desktop:/media# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

```Please temme why graphics problem???
F1!!!

---

### Post by emoguitarist06 on 2010-10-04
> **utkarshjadhav said:**
> output for 
```

root@utkarsh-desktop:/media# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

```Please temme why graphics problem???
F1!!!

First the graphics problem. Did you install the drives for Nvidia? From System > Administration > Hardware Drivers?

The output of sudo apt... tells me that another package manager is opened like Synaptic or maybe software manager is opened. If you're not sure what else may be opening using APT then you can always Reboot and then open nothing else but the terminal and try and it should work

---

