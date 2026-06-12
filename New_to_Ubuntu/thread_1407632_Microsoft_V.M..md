---
title: "Microsoft V.M."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-02-15
How do you start a Virtual Machine for Microsoft XP, wine is becoming very frustrating?

---

### Post by Flying Pikachu on 2010-02-15
First off all you download Virtualbox from here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and when you finished downloading that and installed it click New and select windows XP and just go with the recommended settings start it up and mount your .iso image or put in your windows XP disc.

Any problems just reply back. Thanks.

---

### Post by gvoima on 2010-02-15
VirtualBox is indeed a good one and you can install it from the repositories. It is also easier to maintain between kernel updates.

Another one is VMWare Server, but after using alot of VMWare and VirtualBox, on ***personal desktop use*** I prefer VirtualBox.

Try the link above or then install it from repositories :)

---

### Post by muddpup64 on 2010-02-15
Ok thanks.

---

### Post by Merk42 on 2010-02-15
Be aware that it is more intensive to run a VM (as you need to have the ram to run Ubuntu and XP at the same time)
Also 3D support is experimental at best, so don't expect to run all 3D games this way either.

---

### Post by muddpup64 on 2010-02-15
I downloaded and installed virtualbox but I can't find it.

---

### Post by dmaxel on 2010-02-15
You need to add yourself to the vboxusers group by using the follow command in Terminal:
```
sudo adduser [USERNAME] vboxusers
```
...and then restart.

---

### Post by muddpup64 on 2010-02-15
All good but now it won't let me make my password.

---

### Post by muddpup64 on 2010-02-15
I got it thanks.

---

