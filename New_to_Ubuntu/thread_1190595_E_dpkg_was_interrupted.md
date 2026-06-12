---
title: "E: dpkg was interrupted"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by mrfotheringham on 2009-06-18
Hi have seen archives for this problem. However they I still can't resolve.

martin@martin-desktop:~$ sudo dpkg configure a
[sudo] password for martin: 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
martin@martin-desktop:~$ 

any help gratefully recieved.

---

### Post by pbpersson on 2009-06-18
Here is the entire error message which you originally received:
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

In your example you were missing part of the command which is why it did not work for you

---

### Post by _Purple_ on 2009-06-18
Try
```
sudo dpkg --configure -a
```
Then 
```
sudo apt-get update
```

For details, please check
```
man dpkg
```

---

### Post by mrfotheringham on 2009-06-18
Thank for reply excuse my idiocy but whicj bit am i missing?

---

### Post by Gazneth on 2009-06-18
The correct command is ```
sudo dpkg --configure -a
``` try that followed by ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade
``` If you get another error message post it here.

---

### Post by mrfotheringham on 2009-06-18
Thank _Purple_ and Gazneth worked a treat. I originally though hyphens indicated exact spacing derrrr!

Best wishes:D

---

### Post by _Purple_ on 2009-06-18
mrfotheringham, 
You are welcome. :)
Usually options are prefixed hyphens.

---

