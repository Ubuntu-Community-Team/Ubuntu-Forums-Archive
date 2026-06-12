---
title: "no such file or directory &quot;google earth.bin&quot;"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-05-25
hello im trying to install google earth and everything time i try to run ./googleearth.bin i keep getting this error "no such file or directory". I'm about to have a tantrum of a life time... Please assist.

---

### Post by DLG102282 on 2009-05-25
Is that the name of the file you downloaded? Are you sure you have the terminal in the coreect directory when you use the command?

---

### Post by qamelian on 2009-05-25
Why not just add the Google repository for apt? That way, you get the benefit of receiving updates, as well.

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

---

### Post by taurus on 2009-05-25
If you have saved it to your computer, then it would be on your desktop.  Therefore, you need to change to that directory, reset the permission so you can run it, then run it to install it.  Just so you know in case you plan to throw another big tantrum, Linux/Unix is case SenSitive so googleearthlinux.bin is NOT the same as GoogleEarthLinux.bin.

```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by Ravernomina on 2009-05-25
got it to work it was the cd command for desktop TYVM!!

---

