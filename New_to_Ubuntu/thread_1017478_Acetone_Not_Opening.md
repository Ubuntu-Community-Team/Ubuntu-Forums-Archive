---
title: "Acetone Not Opening"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Tumpster on 2008-12-21
I used the deb file from getdeb to install Acetone today and it does not open, I will click to open the program, I'll get the wait symobl and then it will dissapear. I have followed the readme and downloaded all the dependencies and utilized the chmod to add myself as a user. I followed the steps from this website: [http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)
And I still have the same issue. Any ideas? I'm running Hardy.

---

### Post by Partyboi2 on 2008-12-21
Have you tried starting it from the terminal
```
acetoneiso2
```

---

### Post by Tumpster on 2008-12-21
Just gave it a shot and got this:
craig@craig-desktop:~$ acetoneiso2
Segmentation fault
craig@craig-desktop:~$

---

### Post by Tumpster on 2008-12-22
Any ideas?

---

### Post by Tumpster on 2008-12-22
Ttt

---

### Post by bulletxt on 2008-12-22
are you running an x86 32bit OS? be sure to have installed the x86 32bit deb package if that is the case. I see no other reason for a segmentation fault.

---

### Post by Tumpster on 2008-12-23
Yes, I have it installed properly as I took it from the website and set it up properly.

---

