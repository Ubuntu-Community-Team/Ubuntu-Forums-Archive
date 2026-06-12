---
title: "installing debian package in 9.04 jaunty"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by freeburn on 2009-05-31
My cpu is  pentium 4. i downloaded some debian package with a "i386" tag on them. but when i try to install them using dpkg it gives a error massage 'wrong architecture'. what should i do?

---

### Post by SunnyRabbiera on 2009-05-31
Are you sure you are not using the 64bit version of Ubuntu?
It should work

---

### Post by Tibuda on 2009-05-31
What package are you trying to install and what is the terminal output of **uname -m**?

---

### Post by freeburn on 2009-05-31
i got this 9.04 from a friend, its a burned disk. i dont know which version it is,how can i know which version of ubuntu i'm using?

---

### Post by freeburn on 2009-05-31
how can i know that my ubuntu is 32 bit or 64

---

### Post by freeburn on 2009-05-31
> **danielrmt said:**
> What package are you trying to install and what is the terminal output of **uname -m**?

wvdial,

what does this command do?

---

### Post by Tibuda on 2009-05-31
> **freeburn said:**
> what does this command do?

it answer this question:
> **freeburn said:**
> how can i know that my ubuntu is 32 bit or 64

---

### Post by freeburn on 2009-05-31
output is x86_64.....i'm kind of puzzled. as far as i know x86 means 32 bit processors....then why a 64 is followed by it?

---

### Post by freeburn on 2009-05-31
as i found it refers to an AMD RISC archiecture........so my ubuntu is designed to run in AMD machines?(cause as far as i know intel does not have any parallel to this x86-64 architecture....)

so why it is running in my machine?

and should i change my ubuntu?(i guess i should....)

---

### Post by durand on 2009-05-31
It means that you are using 64 bit ubuntu so you need to get the 64bit version of that package.

EDIT: Intel has IA64 but amd's 64 bit architecture is more popular. It doesn't matter that it was made by amd, intel use it as well. You don't need to change to 32bit ubuntu. 64bit is the future and unless you plan on doing complex stuff on it that requires 32bit, you can just use it. Most programs will work in the same way.

---

