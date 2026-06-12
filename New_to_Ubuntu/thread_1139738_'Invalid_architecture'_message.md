---
title: "'Invalid architecture' message"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Ugluk on 2009-04-27
When I'm trying to install a package in Xubuntu 9.04, I'm getting the error 'wrong architecture: i386'. I'm having Celeron M 530 processor, why I386 doesn't work?

---

### Post by skymera on 2009-04-27
What package are you trying to install?

Are you running 32bit or 64bit Ubuntu?

---

### Post by Ugluk on 2009-04-27
How can I tell the version used?

---

### Post by mikewhatever on 2009-04-27
Does it really say the architecture is wrong, or does it say that it couldn't find the specified package for i386 architecture? I suspect something is wrong with your internet connection or the repositories.

---

### Post by Ugluk on 2009-04-27
It's standalone package file, and is error is literally what debi tells me.

---

### Post by mikewhatever on 2009-04-27
> **Ugluk said:**
> It's standalone package file, and is error is literally what debi tells me.

And what package is that?

---

### Post by rajeev1204 on 2009-04-27
To check your installed ubuntu version just type uname -a in terminal.

---

### Post by Ugluk on 2009-04-27
Oh, it seems I have 'amd64' system. Any way to convert 'i386' package to this architecture?

---

### Post by oldos2er on 2009-04-27
What are you trying to install?

---

### Post by Ugluk on 2009-04-27
Why is it significant?

---

### Post by mikewhatever on 2009-04-27
> **Ugluk said:**
> Why is it significant?

You could be trying to install an .rpm package downloaded from somewhere. Ubuntu is Debian based, and rpm would be wrong architecture.

---

### Post by Ugluk on 2009-04-28
No, it's Debian package for 32-bit i386 processor architecture. Why cannot it be installed in 64-bit system? Does it mean that 64 bit Ubuntu cannot run 32-bit applications? If it can do it, how can I convert this 32 bit *.deb for it to be installed in 64-bit system?

---

### Post by Peter09 on 2009-04-28
I believe you can force a 32 bit package to be installed on 64 bit architecture by using the -Force switch. But you should google this to confirm that its correct, and be aware that it may have unforeseen consequences.

---

### Post by ndefontenay on 2009-04-28
Also, if you tell us what you want to install we might be able to give you an alternative to get your application.

---

### Post by rajeev1204 on 2009-04-28
> **Ugluk said:**
> Oh, it seems I have 'amd64' system. Any way to convert 'i386' package to this architecture?


Cant convert but you can install the package like this

```
sudo dpkg -i --force-architecture packagename
```

Dont expect it to always work because there are a lot of extra 32 bit libraries you might need.

---

