---
title: "Temporary files?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-22
Whenever you download something sudo apt-get install ** for example, where do the temporary package files get installed and what not?
And what happens if its downloading what you requested and you close the terminal, and then want to clear the half downloaded files?

Where are they located or is there some kind of file cleaning app?

---

### Post by Mornedhel on 2009-06-22
The files are in /var/cache/apt/archives. Partially downloaded files should be in the partial subdirectory.

You can clean it all with sudo apt-get clean.

---

### Post by Cheesemill on 2009-06-22
```
sudo apt-get clean
```

---

