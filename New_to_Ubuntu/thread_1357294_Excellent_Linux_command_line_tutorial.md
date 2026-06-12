---
title: "Excellent Linux command line tutorial"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by L a r r y on 2009-12-17
I have just re-installed and updated Ubuntu 9.04 again to clear up any issues I had from a ruptured disk.  I had a power failure to my hard drive, and a few things got corrupted.

One issue I keep running into is the cp command omitting the source directory and doing no copying.

[This page on www.tuxfiles.org]("http://www.tuxfiles.org/linuxhelp/dirman.html") explained the problem and is going to be a big help in letting me make better use of the command line.

---

### Post by zkriesse on 2009-12-17
Glad you found something to help..here is a link for Terminal Line help.... :) [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ukripper on 2009-12-17
> **L a r r y said:**
> 

One issue I keep running into is the cp command omitting the source directory and doing no copying.



you will need -R or -r after cp to copy the sub-directories and files in a directory. example:
```
cp -r test-folder /home/user/somewhere
```

---

