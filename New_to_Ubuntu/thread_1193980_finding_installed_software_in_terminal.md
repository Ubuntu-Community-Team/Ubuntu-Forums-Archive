---
title: "finding installed software in terminal"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by sslhbala on 2009-06-22
i installed three pc's which has ubuntu os , by ssh i commuicate other pc's. how do i find installed software by dates using terminal 
dpkg- l
dpkg- l | awk '{print $2}' > installed_packages.txt 
 but i need by showing dates like example today date what are the softwares installed?

---

### Post by Revolutionary101 on 2009-06-22
You can find a list of all the software you have installed by typing

```
dpkg --get-selections
```

or if you want to write that list to a file

```
dpkg --get-selections > filename
```

For filename just make it a .txt file

This list will not give you the dates though, but this is the closest you can get, that I know of.

Hope it helps

---

