---
title: "[SOLVED] .bin file"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by JohnPta on 2008-12-04
I have downloaded a .bin file, upgrade of Google Earth. How do I install this? Thanks.

---

### Post by binbash on 2008-12-04
./binfileblabla.bin

---

### Post by sayakb on 2008-12-04
```
chmod +x filename.bin
./filename.bin
```

---

### Post by oldos2er on 2008-12-04
> **JohnPta said:**
> I have downloaded a .bin file, upgrade of Google Earth. How do I install this? Thanks.

 If it's on your desktop, run these commands one at a time (in a terminal):

 cd Desktop

 chmod a+x GoogleEarthLinux.bin

 sudo ./GoogleEarthLinux.bin

 And then QUIT the installer before running the program.

---

### Post by JohnPta on 2008-12-04
Oups, NONE of the previous advices worked what did I do wrong? ?

---

### Post by JohnPta on 2008-12-04
Thanks oldos2er. Your advised to put one command after the other one. But I copied your complete advice and pasted it to my terminal in the directory where the .bin file was and it looks like everything is working. Great advice. Thanks

---

