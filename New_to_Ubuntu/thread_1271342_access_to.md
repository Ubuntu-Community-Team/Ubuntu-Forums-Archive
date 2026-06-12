---
title: "access to"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by jtmedin on 2009-09-20
Have an external usb drive & want to look @ some of the files. When i try to open one of the files i get the 'access to * denied'. What do i do to become super user & open some of the file with openoffice? Been here before but forget so sone. TIA

---

### Post by ChrT on 2009-09-20
Copy the files over to your disk and chmod/chown them?

---

### Post by SoftwareExplorer on 2009-09-20
You could hit Alt+F2, then type in ```
gksudo nautilus
```. In the window that comes up, you can copy the files to wherever you want them. Then highlight them, Right click and go to properties, then the permissions tab, and set the owner and groups to your username.

Hope that helps

---

