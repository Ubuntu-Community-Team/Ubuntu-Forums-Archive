---
title: "Laptop touchpad configuration?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by valros on 2009-01-04
Ok so I finally have Ubuntu on my laptop(thank god 8.10 accepted my network card), theres this little quirk which is very annoying. I have a standard touchpad with vertical scrolling, except Ubuntu thinks the vertical scrolling section is larger than it really is. Is there a configuration file that specifies the layouts and such, hopefully just changing a number is required.

---

### Post by adult swim on 2009-01-04
[http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/](http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/)

---

### Post by valros on 2009-01-04
My x config file didnt have the section for an input device, no big deal I imagined. I created the section and threw in the identifier and option, then the EndSection line. However the X server didnt like it and booted in low graphics mode. Did this twice so I dont think it was a typo.

---

### Post by adult swim on 2009-01-04
edit:  i always forget that hal is in charge of mice and such these days.  im not 100 percent sure what to do here but i can give you  a few links taht may point you in the right direction
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
[http://ubuntuforums.org/showthread.php?t=970277](http://ubuntuforums.org/showthread.php?t=970277)
hopefully someone who knows for sure will see!

---

