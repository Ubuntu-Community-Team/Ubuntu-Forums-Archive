---
title: "sound disappeares"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by svetlinux on 2009-12-06
Hi, i installed Xubuntu before a few days and at first everything was OK.
But then a problem occurred - sometimes when i log in there is no sound and i can't play any mp3 file or any movie... The strange in all this is that it's not constant, but when it happens it's very irritating.
Any ideas what the problem might be???

---

### Post by cartisdm on 2009-12-06
Try keeping the alsamixer window open and see if anything changes between when you have sound and when you don't

To install, open a terminal and type:
```
sudo apt-get install gnome-alsamixer
```

To run, open a terminal and type:
```
gnome-alsamixer
```

Also keep an eye on your volume control:
```
gnome-volume-control
```

---

### Post by svetlinux on 2009-12-06
hahhahaha 10x man
It seems that a package connected to 

gnome-volume-control 

has not been installed.
For now everything is just OK. I hope there will be problems no more.

---

### Post by cartisdm on 2009-12-06
> **svetlinux said:**
> hahhahaha 10x man
It seems that a package connected to 

gnome-volume-control 

has not been installed.
For now everything is just OK. I hope there will be problems no more.

hmmm, weird.  Check back if you continue to have problems

---

