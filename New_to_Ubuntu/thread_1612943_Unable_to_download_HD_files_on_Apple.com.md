---
title: "Unable to download HD files on Apple.com"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by NonStop on 2010-11-03
I have been trying to download trailers in HD off apple.com, like this for example; [http://trailers.apple.com/trailers/wb/suckerpunch/](http://trailers.apple.com/trailers/wb/suckerpunch/)

Although I can watch the trailer, if I click to download it nothing happens. Any advice? I am using 10.10 by the way.

Thanks in advance.

---

### Post by CharlesA on 2010-11-03
Try using wget from a terminal.

---

### Post by NonStop on 2010-11-09
I am afraid I don't know how to do that, any other methods or could you give me some more detail? Thanks, and sorry for the late reply.

---

### Post by CharlesA on 2010-11-09
just run this in a terminal:

```
wget URL
```

You could also try right clicking and save link as inside firefox to see if it'll save it.

---

### Post by philinux on 2010-11-09
Seems Apple does not want this to happen unless your using quicktime and windows I guess. Even this does not work now,

wget -U QuickTime/7.6.6 [http://trailers.apple.com/movies/wb/suckerpunch/suckerpunch-tlr1_480p.mov](http://trailers.apple.com/movies/wb/suckerpunch/suckerpunch-tlr1_480p.mov)

It only downloads a very small file.

---

### Post by CharlesA on 2010-11-09
> **philinux said:**
> Seems Apple does not want this to happen unless your using quicktime and windows I guess. Even this does not work now,

wget -U QuickTime/7.6.6 [http://trailers.apple.com/movies/wb/suckerpunch/suckerpunch-tlr1_480p.mov](http://trailers.apple.com/movies/wb/suckerpunch/suckerpunch-tlr1_480p.mov)

It only downloads a very small file.

I tried the right click method too and it did the same. 

I also checked it on a Windows box and a Linux box with same results. It looks like they want you to open it in yer browser to watch it. *shrug*

---

### Post by NonStop on 2010-11-09
So, this is simply an issue that cannot be resolved. Could one submit it to the Ubuntu development team?

---

### Post by CharlesA on 2010-11-09
I'd say it's a problem with the Apple site, not Ubuntu.

---

