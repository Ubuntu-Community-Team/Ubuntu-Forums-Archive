---
title: "Help opening .deb files"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by GOLDN on 2009-11-22
Hello,

My problem is that every time I try to open a .deb file I get this error: " could not open (filename) , the package may be corrupted or you are not allowed to open open the file. Check the permissions of the file."

Im sorry if this sounds dumb, I just installed ubuntu the other day so I don't know whole lot about it.

---

### Post by quinnten83 on 2009-11-22
Can you install software using the ubuntu software center?
And are you trying to open the .deb or install software from it.
usually a double click will start the install process.

---

### Post by emigrant on 2009-11-22
go to the directory where the file is located and type in the terminal:
```

sudo dpkg -i <.deb package name>

```

---

### Post by GOLDN on 2009-11-22
Yes, I try to double click on it, the installer will load and than I get that message.

---

### Post by GOLDN on 2009-11-22
> **emigrant said:**
> go to the directory where the file is located and type in the terminal:
```

sudo dpkg -i <.deb package name>

```
Thank you, I'll try that

---

### Post by MelDJ on 2009-11-22
i think the download is corrupt. try redownloading

---

### Post by GOLDN on 2009-11-22
I try downloading several files, none of them work.

---

### Post by GOLDN on 2009-11-22
I always have to enter my password when I try to change settings, do I have to do this in this situation, if so, how?

---

### Post by MelDJ on 2009-11-22
> **GOLDN said:**
> I always have to enter my password when I try to change settings, do I have to do this in this situation, if so, how?

do you mean in terminal?

in terminal, you password will be invisible while you type it. so just type it in and press enter

---

### Post by frenchn00b on 2009-11-22
> **GOLDN said:**
> Hello,

My problem is that every time I try to open a .deb file I get this error: " could not open (filename) , the package may be corrupted or you are not allowed to open open the file. Check the permissions of the file."

Im sorry if this sounds dumb, I just installed ubuntu the other day so I don't know whole lot about it.

you can open it with 
```
mc
```

and try ```
less *.deb
```
try eventually isomaster, but im not sure

---

