---
title: "What are file descriptors?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by delcypher on 2009-02-17
Hi I'm a fairly new Ubuntu convert and I was wondering if someone could explain to me what a "file descriptor" is.

I came across this when I used...
```
tail -f myfile
```
in the console

I tried editing the file (myfile) using vim and noticed that ```
tail
``` showed no changed. I checked its man page and discovered that the ```
-F
``` option instead of ```
-f
```does the job apparently because it uses the filename rather than the file descriptor.

So what is the difference between filename and file descriptor?

Thanks.

---

### Post by mikewu on 2009-02-17
A file descriptor is an integer that refers to a file in the kernel list of open files. A filename is just a name we give a file. So my understanding is that the file descriptor will stay the same even if you change the file name. 

This becomes a problem when logs rotate, since tail -f will follow the file descriptor and continue following the old log. By using tail -F, tail follows the file name, not descriptor. 

I not sure why what you described happens. Maybe because vim is creating a new file which has a different file descriptor. Using tail -f would just follow the name. 

echo "1" >> test 
appears for me with tail -f so I assume it has to do with vim writing to the file.

---

