---
title: "Cannot COPY items to /usr folder."
date: 2010-08-01
forum: New to Ubuntu
---

### Post by for9ott3n on 2010-08-01
Hi,

I installed Code::Blocks for programming in C/C++ and I wanted to add some libraries but when i try to copy and paste them in my /usr/include/c++ folder, I cannot do so because I'm not root and i don't have permission to write to that location.

Any way I can write to these folders so I can add the libraries?

Thanks
Harsh 
:)

---

### Post by TeoBigusGeekus on 2010-08-01
```
sudo cp /path/to/file/to/be/copied/filename.ext /usr/include/c++/filename.ext
```

---

### Post by for9ott3n on 2010-08-01
Thanks..but how do I copy multiple files? Do I have to do this for every single file?

---

### Post by TeoBigusGeekus on 2010-08-01
```
sudo cp /path/to/files/to/be/copied/* /usr/include/c++/
```

---

### Post by for9ott3n on 2010-08-01
Thank you so much :)

---

