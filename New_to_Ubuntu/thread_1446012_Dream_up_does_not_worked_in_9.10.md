---
title: "Dream up does not worked in 9.10"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by fairbird on 2010-04-03
i want to run dreamup in ubuntu 9.10 but i get error when i make this command in terminal 
 
# sudo ./Dreamup
 
i get this line error
 
```
libgtk-1.2.so.0: cannot open shared object file: No such file or directory 
```
 
i was read this thread but i don't now how to make packages run . 
 
[http://ubuntuforums.org/showthread.php?t=1341472](http://ubuntuforums.org/showthread.php?t=1341472)
 
help please
 
Regards

---

### Post by @rizz on 2010-04-03
Hi,
  
 There Dreamup folder present in home folder? 
is the path that u show in the command correct?

if you want to install the libgtk1.2 package 
this command will work:

```
$ sudo apt-get install libgtk1.2 
```

---

### Post by @rizz on 2010-04-03
Hi,
  
 There Dreamup folder present in home folder? 
is the path that u show in the command correct?

if you want to install the libgtk1.2 package 
this command will work:

```
$ sudo apt-get install libgtk1.2 
```[/QUOTE]

Then try and run the Dreamup with the correct path

---

### Post by fairbird on 2010-04-03
Thank you ...


> There Dreamup folder present in home folder?
on Desktop

>  is the path that u show in the command correct?
yes

> sudo apt-get install libgtk1.2
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Then try and run the Dreamup with the correct path> 
this terminal result for run Dreamup in the correct path

> raed@ubuntu:~/Desktop$ sudo ./DreamUP
./DreamUP: error while loading shared libraries: libgdk_pixbuf.so.2: cannot open shared object file: No such file or directory


---

### Post by fairbird on 2010-04-03
i was success to worked Dreamup ... with help my friend (fergy) ...

Thank you **_fergy_**

and here is the way to do it ....

wget [http://mirrors.kernel.org/ubuntu/pool/universe/g/gdk-pixbuf/libgdk-pixbuf2_0.22.0-14_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gdk-pixbuf/libgdk-pixbuf2_0.22.0-14_i386.deb)

dpkg -x libgdk-pixbuf2_0.22.0-14_i386.deb libgdk-pixbuf

sudo cp libgdk-pixbuf/usr/lib/libgdk* /usr/lib/

wget [http://mirrors.kernel.org/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.24.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.24.0-0ubuntu1_i386.deb)

dpkg -x libglib2.0-0_2.24.0-0ubuntu1_i386.deb libglib 

sudo cp libglib/usr/lib/libgmodule* /usr/lib/

sudo ln -sf /usr/lib/libgmodule-2.0.so.0 /usr/lib/libgmodule-1.2.so.0

wget [http://mirrors.kernel.org/ubuntu/pool/main/libc/libcanberra/libcanberra-gtk-module_0.6-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libc/libcanberra/libcanberra-gtk-module_0.6-0ubuntu3_i386.deb)

dpkg -x libcanberra-gtk-module_0.6-0ubuntu3_i386.deb libcanberra

sudo cp libcanberra/usr/lib/gtk-2.0/modules/* /usr/lib/modules

Regards

---

