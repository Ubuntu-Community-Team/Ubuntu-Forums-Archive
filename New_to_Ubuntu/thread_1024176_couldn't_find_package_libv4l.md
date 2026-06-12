---
title: "couldn't find package libv4l"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by nfbueno on 2008-12-28
After issuing the following command

$ sudo apt-get install kernel-package linux-headers-2.6.27-7-generic build-essential libv4l

I got the following messages

Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
E: Couldn't find package libv4l

Using synaptic package manager, I checked and libv4l is already installed. 
Now, what could be the problem? Why does it say it couldn't find the package?

---

### Post by Partyboi2 on 2008-12-28
The package name is libv4l-0 not  libv4l try
```
sudo apt-get install libv4l-0 
```

---

### Post by nfbueno on 2008-12-28
> **Partyboi2 said:**
> The package name is libv4l-0 not  libv4l try
```
sudo apt-get install libv4l-0 
```


Thank you for the reply. I just replaced libv4l with libv4l-0 and the installation run ok.

---

### Post by El Viejo Lobo on 2009-02-15
I found libv4l installed and started skype by using:
Comand line : LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

The only thing that I got is a **BLACK** screen instead of[COLOR="YellowGreen"]** GREEN**[/COLOR] ONE.
What I am  missing? 
1. A fix that works.
2. A new webcam that work with Intrepid Ibex.
3.May be I will have to wait to  "Jaunty Jackalope" to see my children and grandchildren.
:(

---

