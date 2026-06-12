---
title: "Cann't use software center"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by dnot on 2010-05-30
ubuntu 10.04 32bit

I get "Previous Installation hasn't been completed". 

So, how do I stop the other install or restart it?

---

### Post by Guitar John on 2010-05-30
Tr updating your system.  I just did a clean install on my wife's computer and there were over 100 updates, including a kernal update.  

After updating, restart (always necessary with a kernal update) and see what happens from there.

---

### Post by ranch hand on 2010-05-30
> **dnot said:**
> ubuntu 10.04 32bit

I get "Previous Installation hasn't been completed". 

So, how do I stop the other install or restart it?
First go to System>Administration>Synaptic and pull it up.  Down on the bottom bar there are some messages about the condition of your package management system.  Are there any broken packages?

If you had used synaptic in the first place you would have gotten a similar message with the added information that you need to run;
```

sudo dpkg --configure -a

```
This is done in your terminal found at Aplications>Accessories>Terminal

Hopefully this will fix it.

Dpkg is the foundation of your package management system.  Every thing else is a layer on top of it (apt or aptitude) or on top of another like synaptic on top of apt.

As far as I am concerned USC is just another, unneeded layer that may be nice but will cause more grief than it is worth.

---

