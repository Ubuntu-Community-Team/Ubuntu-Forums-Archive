---
title: "How do I install this file?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by saskatchewan on 2009-04-05
How do I install this file:

jre-6u13-linux-i586-rpm.bin

I downloaded it to my Documents folder and went cd Documents

I have eee 1000 with Ubuntu.

---

### Post by bekind2thenoob on 2009-04-05
Type ```
sudo aptitude install sun-java6-bin
``` into your terminal to install the java runtime  from the repos its at the same version 6-13.

---

### Post by gandaran on 2009-04-05
> **saskatchewan said:**
> How do I install this file:

jre-6u13-linux-i586-rpm.bin

I downloaded it to my Documents folder and went cd Documents

I have eee 1000 with Ubuntu.
you got the wrong file, this one is for RPM based linux systems, download the .bin not rpm.bin file or why don't you use apt-get or synaptic package manager to install java? it's a lot easier, just open synaptic, scroll down to sun-java6-plugin mark for install and click the apply button! it will install the full java package, firefox pulgin and jre!

---

### Post by saskatchewan on 2009-04-05
Now I have another problem:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
shawn@shawn-laptop:~$ dpkg -- configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
shawn@shawn-laptop:~$ 
What should I do?

---

### Post by Peasantoid on 2009-04-05
You typed "-- configure" instead of "--configure".

---

### Post by gandaran on 2009-04-05
sudo dpkg --configure -a

---

### Post by saskatchewan on 2009-04-05
now it asks for superuser privilage
How do I get that?

---

### Post by sheshbesh on 2009-04-05
dont forget the "sudo" before the command as mentioned in post #6
you may be asked for your password

if this was your last command you can also use "sudo !!" to repeat the command with superuser privileges

---

### Post by saskatchewan on 2009-04-05
OK, I just do sudo.

But is said that I have broken packages and to use the broken filter to resolve.

How do I use broken filter?

---

### Post by gandaran on 2009-04-05
> **saskatchewan said:**
> OK, I just do sudo.

But is said that I have broken packages and to use the broken filter to resolve.

How do I use broken filter?
use the filters option in synaptic for that.

---

### Post by gandaran on 2009-04-05
is it the java package that is broken? use synaptic to reinstall not apt-get, this should fix it?

---

### Post by saskatchewan on 2009-04-05
I will try that, but, it seems to be working.

I will keep trying to work with it.

---

