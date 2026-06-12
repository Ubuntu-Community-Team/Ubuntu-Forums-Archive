---
title: "Install GIMP without internet."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by alandaglish on 2010-07-13
I have just installed 10.02 (via an ISO image) on a clean PC which at the moment has no network card or wireless interface, hence no internet.  My question is how can I install (for instance) GIMP.  I have access to the internet via other pcs.

---

### Post by Ildanach on 2010-07-13
Your best bet is going to be using one of the computers that do have internet and downloading the source code and transferring that to a flash drive. Then compile the source on your computer without internet.

---

### Post by alandaglish on 2010-07-14
Getting the source code onto the Ubuntu machine is not a problem but the steps needed to compile it are not obvious

---

### Post by louis--taylor on 2010-07-14
I was in exactly the same situation about a year ago... Do you have an internet connection at your house or close by?

---

### Post by vagrale13 on 2010-07-14
If you have a pc **Ubuntu** with *internet connection*, some friend e.g. ,do this:
Run in terminal on your pc
```
 sudo apt-get --print-uris --yes install gimp | grep ^\' | cut -d\'  -f2 > mydownload.txt
```then take the archive **mydownload.txt** where create on your home folder, 
and go to other pc with *internet connection*, open a terminal and run
```
 cd path/to_folder/where_archive/mydownload.txt
``````
 wget --input-file mydownload.txt
```then take all .deb packages where download, and go to your pc, 
open a terminal and run
```
 cd path/to_folder/whith_deb_packages
``````
 sudo dpkg -i *.deb
```and then you can install it! 
You can do this, with all programs, just replace the name **gimp** in 1st command, with the name of program you want!

If the other pc where have *internet connection*, has other OS, try with **sushi-huh **[http://sushi-huh.sourceforge.net/](http://sushi-huh.sourceforge.net/)

---

### Post by alandaglish on 2010-07-15
I have an internet connection om my windows pc and my laptop, someone has suggested I use SUSHI-HUH what does this do?

---

### Post by alandaglish on 2010-07-16
Tried Sushi-Huh but there seemed to be a file missing (wizard.html)

---

### Post by vagrale13 on 2010-07-19
Download these packages
```
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.8-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.8-2ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.8-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.8-2ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/b/babl/libbabl-0.0-0_0.0.22-1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/babl/libbabl-0.0-0_0.0.22-1build1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gegl/libgegl-0.0-0_0.0.22-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gegl/libgegl-0.0-0_0.0.22-0ubuntu4_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng1_1.0.9-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmng/libmng1_1.0.9-1ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.8-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.8-2ubuntu1_i386.deb)
```It's  all the packages that need the **gimp**! :)

---

### Post by stmiller on 2010-07-19
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by alandaglish on 2010-07-27
Problem solved
Managed it implement wireless internet on Linux machine and got GIMP working within the hour

---

