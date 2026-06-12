---
title: "how to unistall virtualbox 3 from my system?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-20
i recently installed virtualbox 3 from the website but for some reason i want to unistall/remove it from my system
until now i tried 2 things but none of them worked

1)i typed on the terminal:
```
sudo apt-get remove virtualbox
```
but then it gives me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package VirtualBox

```

2)i opened the synaptic, but didnt find any package installed with the name virtualbox

any ideas?

---

### Post by falconindy on 2009-09-21
If you installed it from the website and not via apt-get, then you can't uninstall it via apt-get. Did you build from source? Do you have the option of doing `make uninstall`?

---

### Post by heyyy on 2009-09-21
i installed it with the deb package from the official website and managed to unistall it through apt-get .
my mistake was that i was giving it the wrong name so it wasnt able to find it. 
for others that might face the same problem just run: 
sudo apt-get remove virtualbox-3.0

---

### Post by blackened on 2009-09-21
Best practice in scenarios like these is to just do a search in Synaptic and narrow your results by package status.

---

### Post by heyyy on 2009-09-21
> **blackened said:**
> Best practice in scenarios like these is to just do a search in Synaptic and narrow your results by package status.

i tried this way but couldnt find the package

---

### Post by blackened on 2009-09-21
> **heyyy said:**
> i tried this way but couldnt find the package

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=129251&d=1253510293[/IMG]

---

### Post by TuckLive on 2009-09-21
Try:

```
whereis VirtualBox
```

Should be located in /usr/bin.  Look for VirtualBox-uninstall or something similar and then run that.

```
sudo ./uninstall file name here
```

Sorry I'm not at my linux box now, but I believe that's right.

---

### Post by ~sHyLoCk~ on 2009-09-21
> **heyyy said:**
> i installed it with the deb package from the official website and managed to unistall it through apt-get .
my mistake was that i was giving it the wrong name so it wasnt able to find it. 
for others that might face the same problem just run: 
sudo apt-get remove virtualbox-3.0

I believe the OP has already fixed his problem and yet suggestions are flying in. :D

---

### Post by TuckLive on 2009-09-21
Ahhhh and I thought I read the whole thread.  #-o

---

