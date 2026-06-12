---
title: "32 Bit compilatipon on 64 bit machine"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by newport_j on 2010-01-25
I am using a 64 Bit version of Ubuntu 9.10. I want to compile something for 32-bit mode. I do not know the command for 32 bit compilation. I am assume that the gcc command compiles for 64 bits.  

What is the command for 32 bit compilation on a 64 bit version of Ubuntu?

Newport_j

---

### Post by Ubu2010 on 2010-01-25
What language? I created a C program today using a 32-bit app in Windows. My machine is a 64-bit but it was able to compile and run it successfully. Compiled it within Ubuntu 9.10 and successfully ran it there as well.

---

### Post by avidday on 2010-01-25
gcc -m32

It is right in the gcc man page if you care to look.

---

### Post by Ubu2010 on 2010-01-27
I am interested in reading your tip,avidday. However, when I typed ```
cat man
```from within /usr/bin in the Terminal, most of what I was able to see whas gibberish mixed with text. How can I view man pages within the terminal, and specifically, more about the gcc -m32 option ?

---

### Post by jd65pl on 2010-01-27
Try

```
man gcc
```

---

### Post by MarcDam on 2010-01-27
Try ```
man <name of application>
```

---

### Post by Ubu2010 on 2010-01-27
Thanks to both of you !

---

