---
title: "Font Error, Unknown Font : fixed"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2011-07-01
Hey, I have some Problems with ScicosLab .... How can i fix this Problem?

Thanks for your help :-)

```

 Unknown font : -adobe-courier-medium-r-normal--*-80-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
 Unknown font : -adobe-courier-medium-r-normal--*-100-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
 Unknown font : -adobe-courier-medium-r-normal--*-120-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
 Unknown font : -adobe-courier-medium-r-normal--*-140-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
 Unknown font : -adobe-courier-medium-r-normal--*-180-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
 Unknown font : -adobe-courier-medium-r-normal--*-240-*-*-m-*-iso8859-1
 I'll use font: fixed 
 Unknown font : fixed
  Please call an X Wizard !
```

---

### Post by kamaji792 on 2011-07-01
Hi Dude,

Try adding the following packages: **xfonts-75dpi** **xfonts-100dpi**

From the command line:
```
sudo apt-get install xfonts-75dpi xfonts-100dpi
```

atb K

---

### Post by Krabby.Linux on 2011-07-05
Still the same errors...

---

### Post by marli on 2011-07-20
I am also having this problem even after installing the 75dpi and 100dpi font packages.  Anyone have a solution??

---

### Post by Jay Christnach on 2013-02-17
The same here. Has anybody found a remedy to this?

Maybe I will try to compile the whole thing from the sources and see what I can do (often not much :-) )

---

