---
title: "Flash not working..."
date: 2010-04-17
forum: New to Ubuntu
---

### Post by camn on 2010-04-17
When I try to do ```
sudo apt-get install flashplugin-nonfree
``` I get an error message saying ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

```... Help D:

---

### Post by Steam. on 2010-04-17
Look for it manually in synaptic, i think you will find it there.

---

### Post by camn on 2010-04-17
What do I do in synaptic? I'm such a noob xD

---

### Post by wojox on 2010-04-17
What if you run:

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by theozzlives on 2010-04-17
Just run:
```
sudo apt-get install ubuntu-restricted-extras
```
it'll install flash, java, and other things.

---

