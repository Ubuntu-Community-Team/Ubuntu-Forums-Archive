---
title: "opening a Brasero cd image"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by macanudokiosko on 2009-07-27
I've just tested creating an image of cd with brasero. Two files have been created:    cd    cd.toc Now... does anybody knows how to mount those for accessing?  Double clicking the *.toc prompts a window for burning.  macanudokiosko :)

---

### Post by swoll1980 on 2009-07-27
I would install gmount-iso it's a easy graphical way to mount isos. There's also some nautilus scripts that will get the job done.

alternatively you could do it like this

```

sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```

---

