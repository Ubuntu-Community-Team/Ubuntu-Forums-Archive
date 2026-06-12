---
title: "Apache 2 - Images appear broken."
date: 2011-01-10
forum: New to Ubuntu
---

### Post by AlbuquerqueApache on 2011-01-10
Ok guys, I need some help with Apache2. 
 
I am having issues with images appearing on my index.html page in /var/www . 
 
They appear as broken links. I use <img src="picture.jpg"/> assuming that /var/www is the default directory. I guess that httpd.conf has been deprecated so it is blank. (I already tried adding Document Directory /var/www to the file and it made no difference.) 
 
Everything else works superbly. Any tips?

---

### Post by wojox on 2011-01-10
```
<img src="picture.jpg" alt="picture.jpg" width="400" height="240" />
```

The image needs these to be valid. Adjust W/H accordingly. Also a space before />. Is the pic in /var/www/?

---

### Post by AlbuquerqueApache on 2011-01-10
Yes they are in /var/www until I can find a better place for them. 
 
Omitting the H/W parameters would cause this? I will add them to see if it corrects them.

---

### Post by AlbuquerqueApache on 2011-01-10
I'm having the same issue and there in my error log other than a cannot find favicon.img message....


:( Kind of at a loss....

---

