---
title: "cannot update cpp-4.3"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by karlmp on 2009-02-17
i have weeks now that cpp-4.3 won't update

this is 8.10 intrepid

---

### Post by ftpaddict on 2009-02-17
Is there any particular error message you'd like to share with us?

---

### Post by karlmp on 2009-02-17
```
W: Failed to fetch [http://ve.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/cpp-4.3_4.3.2-1ubuntu12_i386.deb](http://ve.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/cpp-4.3_4.3.2-1ubuntu12_i386.deb)
  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://mirrors.rit.edu/ubuntu/pool/main/g/gcc-4.3/cpp-4.3_4.3.2-1ubuntu12_i386.deb](http://mirrors.rit.edu/ubuntu/pool/main/g/gcc-4.3/cpp-4.3_4.3.2-1ubuntu12_i386.deb)
  Connection failed

```


i still can update whenever an update comes, the problem is with cpp-4.3

i changed the server several times and is still the same

---

### Post by karlmp on 2009-02-19
[duplicate post]

---

### Post by karlmp on 2009-02-26
0

---

### Post by karlmp on 2009-03-18
[FONT="Arial Black"][/FONT][COLOR="Lime"][SIZE="7"]bump[/SIZE][/COLOR] :(

---

### Post by mc4man on 2009-03-18
First make sure in System -> Admin -> Software Sources -> Updates that the first 2 boxes are checked.
Then try again or even just go to post 3 and click on the http...

or here
[http://packages.ubuntu.com/intrepid-updates/cpp-4.3](http://packages.ubuntu.com/intrepid-updates/cpp-4.3)

---

### Post by karlmp on 2009-03-18
the 2 boxes are checked 

[QUOTE=mc4man]Then try again or even just go to post 3 and click on the http...

or here
[http://packages.ubuntu.com/intrepid-updates/cpp-4.3](http://packages.ubuntu.com/intrepid-updates/cpp-4.3)[/QUOTE]

tried that and it doesn't make any difference, unless you're suggesting to install it that way

---

### Post by mc4man on 2009-03-19
> unless you're suggesting to install it that way 
not really, cpp is already installed, the only question is it up to date.
You could just ck. in synaptic - current is 4:4.3.1-1ubuntu2 (cpp)  for cpp-4.3 it's 4:4.3.1-1ubuntu12

---

### Post by karlmp on 2009-03-19
i checked in synaptic, it says that i have 4:4.3.1-1ubuntu2:confused:

---

### Post by karlmp on 2009-03-23
i have cpp-4.3 but the update manager keeps telling me to update to cpp-4.3, so it must be a problem with update manager :confused::(

---

### Post by karlmp on 2009-03-28
[FONT="Century Gothic"][SIZE="7"][COLOR="Magenta"]bump[/COLOR][/SIZE][/FONT]:cry:

---

### Post by karlmp on 2009-03-28
[duplicate post] sorry the server got slow so i double posted

---

### Post by karlmp on 2009-03-29
```
karl@karlzt:~$ aptitude show cpp-4.3
Package: cpp-4.3
State: installed
Automatically installed: no
Version: 4.3.2-1ubuntu11
Priority: standard
Section: interpreters
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7676k
Depends: gcc-4.3-base (= 4.3.2-1ubuntu11), libc6 (>= 2.8~20080505), libgmp3c2,
         libmpfr1ldbl
Suggests: gcc-4.3-locales (>= 4.3.2-1)
Description: The GNU C preprocessor
 A macro processor that is used automatically by the GNU C compiler to transform
 programs before actual compilation. 
 
 This package has been separated from gcc for the benefit of those who require
 the preprocessor but not the compiler.

```

---

### Post by karlmp on 2009-04-01
**[solved]**


[https://answers.launchpad.net/ubuntu/+question/65683](https://answers.launchpad.net/ubuntu/+question/65683)


[FONT="Comic Sans MS"]**[SIZE="4"]thanks[/SIZE]**[/FONT]

---

