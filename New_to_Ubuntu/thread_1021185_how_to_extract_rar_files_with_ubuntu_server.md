---
title: "how to extract rar files with ubuntu server"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-25
Is there a program I can get from repositories that will let me extract rar files on intrepid server?

---

### Post by adobrakic on 2008-12-25
Not sure about Ubuntu Server, but normally you just right click the .rar and press "extract here."

---

### Post by zvacet on 2008-12-25
Be sure that you have **multiverse repo** enabled and 

```
sudo apt-get install unrar
```

---

### Post by pshootr on 2008-12-27
> **zvacet said:**
> Be sure that you have **multiverse repo** enabled and 

```
sudo apt-get install unrar
```

Thank you for the helpful reply. I am going to install it and see how I do at working it. :popcorn:

---

### Post by Bachstelze on 2008-12-27
> **pshootr said:**
> Thank you for the helpful reply. I am going to install it and see how I do at working it. :popcorn:

```
unrar x filename.rar
```

---

