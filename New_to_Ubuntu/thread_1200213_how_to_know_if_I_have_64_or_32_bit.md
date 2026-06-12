---
title: "how to know if I have 64 or 32 bit?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by jadu on 2009-06-29
hello
To install a program, it asks me to choose between Ubuntu x64 (64 bit) and Ubuntu x86. I think I've figured out that 64 bit is the more advanced kind, and 86 would be another name for 32 bit, the simpler kind?  Is that right? So I assumed that I had 86. But when I try to install,  it only lets me install the 64 kind. How do I find out for sure which one I have? The person who installed it isn't around anymore to ask, unfortunately.
thanks

---

### Post by ~sHyLoCk~ on 2009-06-29
That depends on what type of OS you have installed.Is it 64bit or 32bit?
What is the output of ```
uname -m
```

---

### Post by mikewhatever on 2009-06-29
Run **uname -m** in Terminal. If the output is amd64 or x86_64 then you have a 64 bit OS.

---

### Post by jadu on 2009-06-29
thanks so much that was it!

---

