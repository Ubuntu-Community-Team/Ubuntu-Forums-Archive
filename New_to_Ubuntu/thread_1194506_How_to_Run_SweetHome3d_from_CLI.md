---
title: "How to Run SweetHome3d from CLI"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by A_M_S on 2009-06-22
Hi!
Anyone know how to run SweetHome3D (Its a Java aplication) from CLI?

It works fine with nautilus but in the CLI it returns "command not found".


```
ams@ams-laptop:~/SweetHome3D-1.8$ ls
COPYING.TXT                           THIRDPARTY-LICENSE-ITEXT.TXT
jre1.6.0_12                           THIRDPARTY-LICENSE-JAVA3D.TXT
lib                                   THIRDPARTY-LICENSE-JAVA.TXT
LICENSE.TXT                           THIRDPARTY-LICENSE-LOADER3DS.TXT
SweetHome3D                           THIRDPARTY-LICENSE-TANGO.TXT
THIRDPARTY-LICENSE-CONTRIBUTIONS.TXT  THIRDPARTY-LICENSE-VECTORGRAPHICS.TXT
ams@ams-laptop:~/SweetHome3D-1.8$ SweetHome3D
bash: SweetHome3D: command not found
ams@ams-laptop:~/SweetHome3D-1.8$ 
```

As the file SweetHome3D is marked as executable, shouldn't i be able to run it from the CLI?

Tnx in adv.

---

### Post by Cheesemill on 2009-06-22
You have to prefix it with a ./
```
./SweetHome3D
```
This is because your working directory isn't included in the $PATH variable (it's a security risk) so Ubuntu won't look in your current directory for executables without you manually specifying it (the ./).

---

### Post by A_M_S on 2009-06-22
Thanks!!! :D

But why do i have to do that? 

What is the meaning of the ./ prefix? :confused:

---

### Post by Cheesemill on 2009-06-22
The . is just a shortcut for the current folder you're in, so instead of typing the full path:
```
/home/ams/SweetHome3D-1.8/SweetHome3D
```
You can just do
```
./SweetHome3D
```
as you are already in the /home/ams/SweetHome3D-1.8/ directory.

---

### Post by Cheesemill on 2009-06-22
To expand further:

Until a few years ago all major distros included the current working directory in the $PATH variable (this is a list of directories where linux looks for executable files). When that was the case you would have been able to just type in the filename of your program to run it. However this is now considered bad practice for the following reason. What if I were to get onto your machine and do the following in your home folder (DO NOT USE THE FOLLOWING COMMAND!!!!)
```
echo "rm -rf /*" > ls ; chmod 755 ls 
```If you were then to type ls to get a directory listing what do you think would happen? The script called ls that I put in your home folder would be executed instead with serious consequences.


**NEVER EXECUTE rm -rf /* ON YOUR MACHINE**

---

### Post by A_M_S on 2009-06-22
I just tried to execute the file in the DOS way ;).

Thanks again for the help!

---

