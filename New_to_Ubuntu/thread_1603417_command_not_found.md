---
title: "command not found"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Ishana on 2010-10-22
Hello there,

I was doing 

sudo aptitude install multiget

but then i got that error

```

sudo: aptitude: command not found

```

Help would be nice

---

### Post by sisco311 on 2010-10-22
Hi and welcome to the forums!

aptitude is not installed by default. Either use apt-get or install aptitude. 
```
sudo apt-get install multiget
```

---

### Post by Ishana on 2010-10-22
Thanks for your help it worked :)

---

### Post by sikander3786 on 2010-10-22
Aptitude is installed by default in all version prior to Maverick. If you are using Maverick, try

```
sudo apt-get install aptitude
```

---

