---
title: "Wget problem with '('"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-05-14
Hello I'm trying to download a file but continue to get error regarding the symbol '(' if you try to download [http://en.wikipedia.org/wiki/CBS_(disambiguation](http://en.wikipedia.org/wiki/CBS_(disambiguation)) using wget will you get a error regarding "(" .Is there any way to get around the problem?

---

### Post by Trebaruna on 2009-05-14
Surround the URL with quotation marks. Like so:

wget "http://en.wikipedia.org/wiki/CBS_(disambiguation)"

---

### Post by SpinningAround on 2009-05-14
Awsome, Thanks :D. That solved on part of the problem but I still got one more :( 

When I try to download all pictures from here [http://ubuntuforums.org/images/](http://ubuntuforums.org/images/) do I only get the index.html file while wget skip the rest

```
wget -r -l1 --no-parent "http://ubuntuforums.org/images/"
```

---

### Post by PGScooter on 2009-05-14
Are you sure that's the right url? My browser show's that there is just a blank page there.

---

### Post by SpinningAround on 2009-05-14
Well I simply presumed it where there since ):P is listed to be
```
http://ubuntuforums.org/images/smilies/smiley-faces-80.gif
```

---

### Post by kpkeerthi on 2009-05-14
Most websites do not allow browsing an arbitrary folder like [http://ubuntuforums.org/images/](http://ubuntuforums.org/images/)

---

### Post by kpkeerthi on 2009-05-14
Try:
```

wget -r --accept=jpg,jpeg "http://ubuntuforums.org/images/"

```

---

