---
title: "Gimp"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by billyfish010 on 2010-10-17
Hi I have Gimp installed on my Ubuntu 10.10 operating system and though it has been working fine for some reason it has stopped working. I have tried removing and reinstalling but it still won't work. Can  anyone advise what may have happened to stop it working.

---

### Post by TeoBigusGeekus on 2010-10-17
Open terminal, type
```
gimp
```
and post us any error messages.

---

### Post by billyfish010 on 2010-10-17
Hi Please see info below.


billyfish010@billyfish010-desktop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:3988): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:3988): LibGimpBase-WARNING **: gimp: wire_read(): error

---

### Post by Joshwaa on 2010-10-17
Try
```
sudo apt-get purge gimp
```
then
```
sudo apt-get install gimp
```

---

### Post by TeoBigusGeekus on 2010-10-17
Open synaptic package manager, search for these two packages (libgtkhtml, libgimpprint), install them and try again.

---

### Post by billyfish010 on 2010-10-17
Hi I have tried both of the above but still no joy is there anything else I could try.

---

### Post by TeoBigusGeekus on 2010-10-17
Have you installed the packages?

---

### Post by billyfish010 on 2010-10-17
Hi TeoBigusGeekus,

I have tried both the suggestions and installed both the packages you listed. I am not sure what I should do now but my own feelings are that it might be worth uninstalling Ubuntu and reinstalling which should fix the problem, the only problem with that is I would have to go through setting up MS office, Google Earth, Picasa,tunebite maybe I should just go back to Windows. I really shouldn't say that though since I still have three computers with MS 7 installed I just had this computer spare with XP on so I thought I would blank it and install Ubuntu and I have been pleasantly surprised so I am trying to get to grips with it to see if it would be capable of replacing my Windows programs however, learning about Windows takes a lot of time and I am not sure I have the patience anymore to learn Ubuntu and it's quirkyness.

---

### Post by TeoBigusGeekus on 2010-10-17
Ok, now what error messages you get when you start gimp from terminal?

---

### Post by billyfish010 on 2010-10-17
Hi Teo,

Please see below.


billyfish010@billyfish010-desktop:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:3784): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:3784): LibGimpBase-WARNING **: gimp: wire_read(): error

---

### Post by TeoBigusGeekus on 2010-10-17
Try one more thing.
```
sudo apt-get purge gimp
```
Go to your home folder and delete the .gimp folder (.gimp-2.something). Then
```
sudo apt-get install gimp
```

---

### Post by billyfish010 on 2010-10-17
Hi Teo,
 
No still nothing but I have to say the folder with Gimp in is not in the home folder so I could not delete it.***** Not to worry guys gone back to good old Windows 7 the best operating system and most reliable in the world virus's and all. I tried Ubuntu and different variations a couple of years ago and have used 10.04 for the last month to my mind they are still unstable and grossly overestimated. Now how do I remove myself from this forum.

---

