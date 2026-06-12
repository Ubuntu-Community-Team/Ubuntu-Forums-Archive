---
title: "Installing vmd-1.8.7"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by dcasimir on 2010-08-10
I am trying to install vmd-1.8.7 on ubuntu 10.04.

After typing "./configure" in the vmd-1.8.7 directory I got, "[COLOR=#ff0000]using configure.options: LINUX OPENGL FLTK TK ACTC CUDA IMD LIBSBALL XINPUT LIBTACHYON VRPN NETCDF TCL PTHREADS SILENT[/COLOR]"


Next after doing step 3 in the installation process by typing "make  install" in the src directory I was blocked with the following, 


[COLOR=#ff0000]administrator@ubuntu:~/vmd-1.8.7/src$ make install[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]mkdir: cannot create directory `/usr/local/lib/vmd': Permission denied[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]mkdir: cannot create directory `/usr/local/lib/vmd': Permission denied[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]make: *** [install] Error 1[/COLOR]


Guidance appreciated,

---

### Post by dcasimir on 2010-08-10
> **dcasimir said:**
> I am trying to install vmd-1.8.7 on ubuntu 10.04.

After typing "./configure" in the vmd-1.8.7 directory I got, "[COLOR=#ff0000]using configure.options: LINUX OPENGL FLTK TK ACTC CUDA IMD LIBSBALL XINPUT LIBTACHYON VRPN NETCDF TCL PTHREADS SILENT[/COLOR]"


Next after doing step 3 in the installation process by typing "make  install" in the src directory I was blocked with the following, 


[COLOR=#ff0000]administrator@ubuntu:~/vmd-1.8.7/src$ make install[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]mkdir: cannot create directory `/usr/local/lib/vmd': Permission denied[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]mkdir: cannot create directory `/usr/local/lib/vmd': Permission denied[/COLOR][COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]make: *** [install] Error 1[/COLOR]


Guidance appreciated,


Sorry for bothering you.

For any other ubuntu beginners who run into similar issues I logged in as the root user then performed step 3 in the src directory.

what I did is below.

administrator@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
administrator@ubuntu:~$ su -
Password: 
root@ubuntu:~# cd vmd-1.8.7/src/
-su: cd: vmd-1.8.7/src/: No such file or directory
root@ubuntu:~# cd /home/administrator/
root@ubuntu:/home/administrator# cd vmd-1.8.7
root@ubuntu:/home/administrator/vmd-1.8.7# cd src/
root@ubuntu:/home/administrator/vmd-1.8.7/src# make install
Make sure /usr/local/bin/vmd is in your path.
VMD installation complete.  Enjoy!

---

### Post by astronautameya on 2010-11-11
thanks it was really helpful

---

### Post by Wtower on 2010-11-11
Some su considerations on [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Regards

---

### Post by nvjopsddhapnv on 2011-02-23
> **dcasimir said:**
> Sorry for bothering you.

For any other ubuntu beginners who run into similar issues I logged in as the root user then performed step 3 in the src directory.

what I did is below.

administrator@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
administrator@ubuntu:~$ su -
Password: 
root@ubuntu:~# cd vmd-1.8.7/src/
-su: cd: vmd-1.8.7/src/: No such file or directory
root@ubuntu:~# cd /home/administrator/
root@ubuntu:/home/administrator# cd vmd-1.8.7
root@ubuntu:/home/administrator/vmd-1.8.7# cd src/
root@ubuntu:/home/administrator/vmd-1.8.7/src# make install
Make sure /usr/local/bin/vmd is in your path.
VMD installation complete.  Enjoy!

Thanks a lot. This works fine.

---

### Post by niziris on 2011-12-04
> **dcasimir said:**
> sorry for bothering you.

For any other ubuntu beginners who run into similar issues i logged in as the root user then performed step 3 in the src directory.

What i did is below.

Administrator@ubuntu:~$ sudo passwd root
enter new unix password: 
Retype new unix password: 
Passwd: Password updated successfully
administrator@ubuntu:~$ su -
password: 
Root@ubuntu:~# cd vmd-1.8.7/src/
-su: Cd: Vmd-1.8.7/src/: No such file or directory
root@ubuntu:~# cd /home/administrator/
root@ubuntu:/home/administrator# cd vmd-1.8.7
root@ubuntu:/home/administrator/vmd-1.8.7# cd src/
root@ubuntu:/home/administrator/vmd-1.8.7/src# make install
make sure /usr/local/bin/vmd is in your path.
Vmd installation complete.  Enjoy!
thanks!!!!!!!!!!!!:ks:ks:ks

---

### Post by plazaster on 2012-10-21
thanks

---

### Post by wildmanne39 on 2012-10-21
Old thread closed.

---

