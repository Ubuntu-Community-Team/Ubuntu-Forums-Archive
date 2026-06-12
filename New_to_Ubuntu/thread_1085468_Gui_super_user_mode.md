---
title: "Gui super user mode"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by msidhard on 2009-03-03
Some files cannot be edited in gui . Those files should be opened by super user mode in terminal. Thats makes me tired. Is there any way to open the files as su  in gui . like if i want to edit wvdial.config i in to terminal and type sudo gedit /etc/wvdial.conf and password then. this makes ME tired . so any alter methods please

---

### Post by cet' on 2009-03-03
make a launcher as gksudo nautilus 

This way you will open your explorer up as root and edit any file without going to the console.

Or press alt+f2 
then enter gksudo nautilus

---

### Post by aquavitae on 2009-03-03
I think its gksu, not gksudo.

---

### Post by mikechant on 2009-03-03
I have package nautilus-gksu installed. This means that any time when running Nautilus (normally, not with gksu etc.), you can right click on any file and select 'open as administrator', type your password as normal and off you go.
I find it very handy.

---

