---
title: "cp *.jar in terminal help"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by KevinJayGonz on 2011-07-23
How do i copy and past a *.jar file in terminal.

i tried using the code below:

cp -r *.jar 'wanted folder'

---

### Post by idoitprone on 2011-07-23
> **KevinJayGonz said:**
> How do i copy and past a *.jar file in terminal.

i tried using the code below:

cp -r *.jar 'wanted folder'

since i feeling lazy to post simple code

here a link
choose your favorite
[http://en.wikipedia.org/wiki/Xargs](http://en.wikipedia.org/wiki/Xargs)

---

### Post by spcwingo on 2011-07-23
> **KevinJayGonz said:**
> How do i copy and past a *.jar file in terminal.

i tried using the code below:

cp -r *.jar 'wanted folder'

You have to give a destination folder.  For example, if your file is in your downloads folder and you wanted to copy it to your home folder:

```
cp ~/Downloads/*.jar ~/
```

---

