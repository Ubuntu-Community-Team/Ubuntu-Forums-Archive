---
title: "Anyone know how to download Thunar? im gettin an error"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by nabeelsadiq on 2009-09-24
For some reason i dont have Thunar anymore. so i downloaded Thunar 10 from the internet, it was a .tar.bz2 file, so i unzipped it, but when i tried to do the ./configure command it says:

checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by ecmatter on 2009-09-24
```

sudo apt-get install thunar

```

---

### Post by scorp123 on 2009-09-24
> **ecmatter said:**
> ```

sudo apt-get install thunar

```

+1

---

### Post by halitech on 2009-09-24
the previous methods are better but if you are trying to compile from source, you need to install build-essential
```
sudo apt-get install build-essential
```

---

### Post by nabeelsadiq on 2009-09-24
Thanks guys, i got it :)

---

