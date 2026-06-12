---
title: "copy files to cd or memory stick from console"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by WileyGaia on 2008-12-12
Hi
I need to copy some files from my hard drive to a cd or usb memory stick from the console. How do I do this?
I can't use the normal GUI because I have a "Ubuntu has to start in low graphics mode" problem which I cannot resolve, so cannot see my screen unless in the console. I just need to save the files, then I am going to re-install the whole thing from scratch to try sort out the problem.

---

### Post by Michael.Godawski on 2008-12-12
```
cp path/to/file1 path/to/whereyouwant 
```

The ```
cp -r 
```command will copy any directories you specify.

---

### Post by WileyGaia on 2008-12-12
thanks - how do i specify a usb memory stick as the destination? sorry I am a little clueless here...

---

### Post by meindian523 on 2008-12-12
As soon as you plugin your memory stick,it should be mounted automagically at /media/<whatever label>
So,that's your destination path.About a CD,the path would be /media/cdrom0.To burn to a CD,you will need cdrecord.Check ```
man cdrecord
``` for details.

---

