---
title: "Ubuntu - Permissions Problem"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by sharks on 2010-02-04
When I wanted to install a forum , it showed me 
Error: Can not write to directory: "cache", please CHMOD to 777

Error: Can not write to directory: "cache/lang_cache", please CHMOD to 777

Error: Can not write to directory: "cache/lang_cache/1", please CHMOD to 777

Error: Can not write to directory: "cache/skin_cache", please CHMOD to 777

Error: Can not write to directory: "public/style_images", please CHMOD to 777

Error: Can not write to directory: "public/style_css", please CHMOD to 777

Error: Can not write to directory: "cache/tmp", please CHMOD to 777

Error: Can not write to directory: "hooks", please CHMOD to 777

Error: Can not write to directory: "uploads", please CHMOD to 777


How do I change it?

---

### Post by nhasian on 2010-02-04
```
sudo chmod 777 cache/lang_cache
```

for more info see

```
man chmod
```

---

### Post by sharks on 2010-02-04
:D
Solved . Thanks.

---

