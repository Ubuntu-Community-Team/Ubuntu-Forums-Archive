---
title: "Shared Libraries?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by JJjester on 2009-06-15
Hello

I have been trying to install Alliance tools. When I run an exe file, I get this error.

vasy: error while loading shared libraries: libRtd.so.1: cannot open shared object file: No such file or directory


The library file libRtd.so.1 comes with the binaries, do I need to add it to the shared library so the exe file can access it?

Sry I have never done anything like this before!

---

### Post by Bachstelze on 2009-06-15
Copy the lib into /usr/local/lib and run [font="monospace"]ldconfig[/font].

```
sudo cp libRtd.so.1 /usr/local/lib
sudo ldconfig
```

---

