---
title: "Permission Issue"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Failboat88 on 2010-06-25
I had a htpc that broke. So, I took the HDD out and connected it to my main PC to save some of my media. The media was in a smb share. When I try and drag the media into my other HDD, the PC tells me I don't have read permission.

---

### Post by ubunterooster on 2010-06-25
try in the terminal ```
sudo nautilus
``` 

ie:running the file manager as root

---

### Post by -kg- on 2010-06-25
> **ubunterooster said:**
> try in the terminal ```
sudo nautilus
``` 

ie:running the file manager as root

Actually, it is recommended that you use:

```
gksu nautilus
```

...if possible.  A good explanation of the reason is here:

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by ubunterooster on 2010-06-25
> **-kg- said:**
> Actually, it is recommended that you use:

```
gksu nautilus
```

...if possible.  A good explanation of the reason is here:

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")
Because I have my nautilus slightly different than default (bookmarks and such), I will lose them while running gksu. If anyone else who has bookmarks (or other configurations) they will not be able to be used in gksu. [COLOR=Red]And the home folder is not your home folder; when running gksu nautilus, any files put into home, go to the home of root.[/COLOR]

---

### Post by Failboat88 on 2010-06-26
Thanks, the gksu nautlius managed to work for me. After I got them into the right place; I changed the permission.

---

