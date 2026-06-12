---
title: "Unzipping in the terminal"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Blueball32 on 2009-02-08
Hey everyone :)

How do I unzip with the "unzip"-command to a specific directory...I tried:

cd /Dir where zip is
unzip filename.zip /Dir where I want to have it

but this doesn't work.

Anyone got the solution? :)

---

### Post by ibuclaw on 2009-02-08
To unzip a zipped file into a directory, you use the "-d" argument.
```
unzip **file.zip** -d **extraction_folder**
```

For more information on unzip:
```
man unzip
```

Regards
Iain

---

### Post by Blueball32 on 2009-02-08
Yeah thats it, thanks alot!! :)

---

