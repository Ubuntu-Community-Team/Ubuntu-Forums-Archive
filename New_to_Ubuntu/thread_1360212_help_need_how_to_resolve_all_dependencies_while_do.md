---
title: "help need how to resolve all dependencies while doing configure"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by esquilomorto on 2009-12-20
Hello everyone.


I would like to know if it's possible to automaticly install all dependencies required in a configure file when i do configure in terminal. Because every times theres a error i have to pick every single package.

Regards and many thanks

---

### Post by Temposs on 2009-12-20
There isn't really a way to do that, that I know of. You just need to go installing them one at a time as you see the errors.

---

### Post by Temposs on 2009-12-20
The only way to be able to do all the dependencies automatically is if you found a .deb file for the application you're trying to compile. Installing the .deb file will automatically install all the dependencies.

---

### Post by esquilomorto on 2009-12-20
many thanks for the reply, as i imagined there was no other solution than to do manually.

cheers

---

### Post by Cheesemill on 2009-12-20
If you're compiling a newer version of a package that's in the repositories you can do:
```
sudo apt-get build-dep <packagename>
```

---

