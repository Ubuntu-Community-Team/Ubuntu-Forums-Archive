---
title: "ldconfig wont find library?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Stord on 2010-03-17
I have this in my /etc/ld.so.conf file:
```
include /usr/local/natinst/LabVIEW-8.6/cintools /etc/ld.so.conf.d/*.conf /usr/local/BerkeleyDB.4.8/lib /usr/local/lib  
```And i attempt to find the library liblv.so which is in the cintools directory by this:
```
 sudo ldconfig
 ldconfig -p | grep liblv.so
```But it returns nothing! Its definitely a valid library, i used nm -Ca liblv.so and got back reasonable results.

Ideas??? :D

---

### Post by lloyd_b on 2010-03-17
> **Stord said:**
> I have this in my /etc/ld.so.conf file:
```
include /usr/local/natinst/LabVIEW-8.6/cintools /etc/ld.so.conf.d/*.conf /usr/local/BerkeleyDB.4.8/lib /usr/local/lib  
```And i attempt to find the library liblv.so which is in the cintools directory by this:
```
 sudo ldconfig
 ldconfig -p | grep liblv.so
```But it returns nothing! Its definitely a valid library, i used nm -Ca liblv.so and got back reasonable results.

Ideas??? :D

You're misunderstanding the "include" directive.  It does *not* tell ldconfig to include libraries in those directories, but rather to read the specified files and append any search paths found in those.

You should never modify ld.so.conf directly.  Instead, go into the directory "/etc/ld.so.conf.d", and create a file ending in ".conf" ("mylibs.conf", for example).  In that file, have a list of the directories containing the libraries you want added.  An example file:```
# My extra library locations
/usr/local/natinst/LabVIEW-8.6/cintools
/usr/local/BerkeleyDB.4.8/lib
/usr/local/lib
```(Note: "/usr/local/lib" *should* be included in the file "/etc/ld.so.conf.d/libc.conf", but it shouldn't hurt to have it duplicated).

Lloyd B.

---

### Post by Stord on 2010-03-17
Wow! Works perfectly :D
Now, just on a side note, where would you put your extra include paths? I currently have them added to the ~/.bashrc file right at the bottom with this line:

export C_INCLUDE_PATH=$C_INCLUDE_PATH:/usr/local/BerkeleyDB.4.8/include:/usr/local/natinst/LabVIEW-8.6/cintools

Is this the correct way to do it?

---

### Post by lloyd_b on 2010-03-17
> **Stord said:**
> Wow! Works perfectly :D
Now, just on a side note, where would you put your extra include paths? I currently have them added to the ~/.bashrc file right at the bottom with this line:

export C_INCLUDE_PATH=$C_INCLUDE_PATH:/usr/local/BerkeleyDB.4.8/include:/usr/local/natinst/LabVIEW-8.6/cintools

Is this the correct way to do it?

Assuming that you are the only one using that machine that needs those paths, then ~/.bashrc *is* the correct place for those changes.  If the changes need to be for ALL users, then "/etc/environment" would probably be a better place.

Lloyd B.

---

