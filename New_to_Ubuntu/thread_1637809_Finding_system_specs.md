---
title: "Finding system specs"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by at2smithjason on 2010-12-04
I need to find my system specs because I just started using ubuntu 8.10 and my laptop is slow (its old).  I want to d/l mint because I hear that its good for older systems.  Need to know the command line for it.  thanks.

---

### Post by sikander3786 on 2010-12-04
For detailed info,

```
sudo lshw
```

For RAM,

```
free -m
```

Graphics,

```
lspci | grep VGA
```

Processor,

```
sudo lshw | grep Processor
```

Some graphical tools are available but I don't know much about them.

---

### Post by drpjkurian on 2010-12-05
Hi
for GUI, you can try Administration-> system Monitor

---

### Post by at2smithjason on 2010-12-05
total       used       free     shared    buffers     cached
Mem:           374        352         21          0         29         84
-/+ buffers/cache:        239        134
Swap:         1098         41       1056

This is what the terminal told me.  So with this will I be able to run mint?  If not is there another distro that I can use?  Also I am using a laptop and I would like to disable the touchpad.  Thanks!!!

---

### Post by sikander3786 on 2010-12-05
I would suggest Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

---

### Post by Megaptera on 2010-12-05
... or possibly Peppermint ( a sort of Lubuntu for Mint) 

[http://peppermintos.com/](http://peppermintos.com/)

---

