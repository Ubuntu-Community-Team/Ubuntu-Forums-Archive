---
title: "Google Earth starts but disappears immediately"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by kramer65 on 2009-08-13
Hello,


I've got Ubuntu 8.04 installed and a while ago I installed google earth on my machine. It starts and I see the window for about 1 second, after which it immediately disappears.

Can anybody help me out here?

---

### Post by afroman10496 on 2009-08-13
How much Ram do you have on your graphics card?

---

### Post by afroman10496 on 2009-08-13
Check using ```
cat /var/log/Xorg.0.log | grep RAM
``` and type in the output of kbytes

---

### Post by kramer65 on 2009-08-13
After the comment you gave, it says this: (II) Initializing built-in extension XINERAMA

---

### Post by afroman10496 on 2009-08-13
> **kramer65 said:**
> After the comment you gave, it says this: (II) Initializing built-in extension XINERAMA
How about above that? My output was ```
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) Initializing built-in extension XINERAMA
```,
so I have 262144kb of Ram, or around 252MB.

---

### Post by kramer65 on 2009-08-13
It only said that:

```
pete@petes-desktop:~$ cat /var/log/Xorg.0.log | grep RAM
(II) Initializing built-in extension XINERAMA
```

But I don't think there is any problem with that. I've got quite a fast computer. I've got a quad-core 2.6GH with 4GB of RAM. I don't know exactly what kind of graphics card I've got, but it's not bad and if I remember correctly I also have around 265mb on that..

or doesn't that matter?  :confused:

---

### Post by philinux on 2009-08-13
How did you install GE. Also what you got under system>admin>hardware drivers?

---

### Post by kramer65 on 2009-08-13
Well well well! 

I installed version 4 of google earth back then, and I now saw that version 5 was out. I just downloaded that and installed and guess what! That works like a charm!!


Thanks anyway for your time and effort! I really apreciate it!

---

