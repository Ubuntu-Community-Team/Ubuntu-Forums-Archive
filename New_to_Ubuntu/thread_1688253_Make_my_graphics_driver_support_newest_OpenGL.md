---
title: "Make my graphics driver support newest OpenGL"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by pepe machine on 2011-02-15
hello everyone, 

Im new to this, I have a software that needs my graphics card to atleast support OpenGl 2.0 to work properly. Im using the nvidia driver from the 'Additional Drivers' menu of ubuntu. I dont know if this driver support openGL 2.0 or later.

I think i need to install the newest  driver from the nvidia site but it is not supported by ubuntu. However there are ways to install it manually but it was very confusing. I have added xswat ppa, and install the updates but theres no change at all.

Kindly please give me the steps of what should i be doing? Im really confused. 
My video card is nvidia geforce 8800g 

how can i know what version of opengl is installed in my pc?
Thank you everyone.

---

### Post by realzippy on 2011-02-15
Open terminal & run

```
glxinfo | grep OpenGL
```

Afaik it is at least 3.0 or 3.3....
Which software do you run?

---

### Post by mikewhatever on 2011-02-15
If you had a new graphics card, installing the newest driver would make sense, but you don't, and the driver from the repositories should work just fine. What makes you think it doesn't have OpenGL support?

---

