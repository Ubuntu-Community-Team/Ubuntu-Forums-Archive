---
title: "Installing a .bin file"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Jaraxle on 2009-09-21
Hello,

I just downloaded ASED from [www.tcl-home.de/ased](www.tcl-home.de/ased) (trying to learn TCL). The binary for linux is a .bin file, which I downloaded.

I know some files like .deb have a way to right-click and install from the context menu. However, I couldn't find anything like that.

How would I go about installing this type of file?

---

### Post by lisati on 2009-09-21
Most of the time, if you trust the source of a .bin file, you can just run it from a terminal. You might have to use the chmod command to mark it as executable.

---

### Post by dearingj on 2009-09-21
Expanding on what lisati said:
The exact commands you'd need to make the file executable are
```
cd /path/to/file/
chmod +x file.bin
```
where file.bin is the name of the file.

You then run it by entering
```
./file.bin
```
Add sudo in front of that if the file is one that needs root privileges, such as an installer.

---

### Post by Jaraxle on 2009-09-22
It worked! Thank you so much. I learned something new!

---

