---
title: "How to install a *.package file"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by joepz on 2009-12-07
Hi, I am still pretty new to Ubuntu, but getting there step by step.
Now I need to install a file/package: ko2009_linux-1.20.x86.package

It didn't 'autorun' when clicking the link on the website, so I downloaded this package (saved it locally). When doubleclicking the file, I get prompted to select an application.
Apparantly a *.package is not associated.
Now what do I do? Associate it with something? How?
Or run it somehow from the terminal?

Help is welcome,
Thanks,
Joep

---

### Post by rubenverweij on 2009-12-07
Hi Joep,

I don't really know what a .package file is, but are you sure the package isn't available via the Software Center?
Otherwise, you could try to execute this command in a terminal to determine what kind of file it is:
```
file -i *.package
```
Then we might be able to determine what kind of file it is.

Hope this helped.

---

### Post by achase79 on 2009-12-07
.package files are usually a self-installing file using autopackage.  you must execute this file in terminal to install and usually you need an active link to the internet.

---

### Post by joepz on 2009-12-07
> **rubenverweij said:**
> Hi Joep,

I don't really know what a .package file is, but are you sure the package isn't available via the Software Center?
Otherwise, you could try to execute this command in a terminal to determine what kind of file it is:
```
file -i *.package
```Then we might be able to determine what kind of file it is.

Hope this helped.

Hi, this is the response:
joep@joep-desktop:~/Downloads$ file -i ko2009_linux-1.20.x86.package
ko2009_linux-1.20.x86.package: text/x-shellscript; charset=binary

Familiar to you?

It is definitely not in the software center. It is a package provided by Dutch tax regulator to fill out for a refund related to child day-care costs. Pretty 'exotic' :p

Thanks,
Joep

---

### Post by joepz on 2009-12-07
> **achase79 said:**
> .package files are usually a self-installing file using autopackage.  you must execute this file in terminal to install and usually you need an active link to the internet.

Okay, how would I execute this in terminal? What command?
Is an active link to the internet something special?
It is supposed to run on the internet when clicking the link. But then everything froze.

Cheers,
Joep

---

### Post by joepz on 2009-12-07
> **achase79 said:**
> .package files are usually a self-installing file using autopackage.  you must execute this file in terminal to install and usually you need an active link to the internet.


It worked!!!

:guitar:

I googled autopackage and followed these instructions:
[http://www.autopackage.org/howtoinstall.html](http://www.autopackage.org/howtoinstall.html)

Thanks a mil!
:p
Joep

---

