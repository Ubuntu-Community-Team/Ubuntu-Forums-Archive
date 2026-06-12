---
title: "Hardware list"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by nerdking on 2009-01-23
how do i find out exactly what is inside of my computer? im trying to figure out what drivers i need for my windows computer that happens to be the same model as this computer.

---

### Post by dnRoyston on 2009-01-23
Well, something you don't want to do is install drivers you don't need, so why bother to install drivers if it works?

This brings the question: Does everything work?

---

### Post by spiderbatdad on 2009-01-23
```
sudo lshw
```

---

### Post by halitech on 2009-01-23
you can actually do
```
lshw > hardware.html
``` to get a browser readable version which should be easier to look at with the file being outputted to whatever directory you are in

---

### Post by spiderbatdad on 2009-01-23
```
WARNING: you should run this program as super-user.

```
lol what a mess that makes: lshw >hardware.html
users might need to know it writes the file to their home directory. When I launched it from there...it was one long string with no newlines, no spaces.

---

### Post by halitech on 2009-01-23
I know it gives the warning that you should but the output is the same either way. 

Just looked at mine and not sure why its not broken up in iceweasel but opening it in Abiword has it looking nice so maybe open it in that or change it to lshw >hardware.txt instead

---

### Post by hyper_ch on 2009-01-24
> **halitech said:**
> you can actually do
```
lshw > hardware.html
``` to get a browser readable version which should be easier to look at with the file being outputted to whatever directory you are in

I'd rather suggest;
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

