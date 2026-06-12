---
title: "Download A List Of Links"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by spikoley on 2010-05-18
I have a list of links for .pdf files I am downloading.  Is there a program or a script I could use to make it less tedious?  There are over 50 links.

---

### Post by lykwydchykyn on 2010-05-18
If it's just one URL on a line with nothing else, you could do this:

```

for i in `cat file_of_links.txt`; do wget $i; done

```

---

### Post by MCVenom on 2010-05-18
If this link list is online, (or if you put it online) you could use the DownThemAll extension for Firefox to download them. :D

---

### Post by pizza-is-good on 2010-05-18
> **BlackOtaku said:**
> If this link list is online, (or if you put it online) you could use the DownThemAll extension for Firefox to download them. :D

DownThemAll is amazing! I love it every time I use it.

wget works too. Just be careful and trust the links.

---

### Post by BoneKracker on 2010-05-18
```
wget -i pdflist
```
(Where "pdflist" is the filename containing your list of URLs.)

---

### Post by spikoley on 2010-05-18
Thanks for the help.  I ended up making a very basic bash script with wget before each URL and it worked.

BoneKracker - I wish I would have saw your post because that would have been easier.

---

