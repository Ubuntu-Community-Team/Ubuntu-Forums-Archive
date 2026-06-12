---
title: "Fluxbox (bash) : how to copy a JPG file into the Clipboard ?"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-23
Hello,

Any ideas how to copy a JPG file into the Clipboard ? I would like from bash to store a given jpg to the clipboard content (no gnome , nor kde)

---

### Post by TeoBigusGeekus on 2010-10-23
[http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/]("http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/")

---

### Post by honeybear on 2010-10-23
> **TeoBigusGeekus said:**
> [http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/]("http://linuxtidbits.wordpress.com/2008/02/22/command-line-to-clipboard/")

I did already try before : not working 

```
cat myfile.jpg | xclip 
```

I cannot paste anything into gimp using xclip :(

---

### Post by honeybear on 2010-11-05
from clipboard to file ? 

is 

> xsel --clipboard > Baada-Boom.txt


---

