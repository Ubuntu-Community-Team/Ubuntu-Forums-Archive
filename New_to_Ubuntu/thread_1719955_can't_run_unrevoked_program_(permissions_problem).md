---
title: "can't run unrevoked program (permissions problem?)"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by alayoyo on 2011-04-02
I downloaded the tar.gz (multiple times) and extracted the 'reflash' program. nautilus says its an executable.

When i double click the file, it says 
"Could not display "/home/yoyo/android/reflash".
There is no application installed for executable files"
(But the properties of the file show it IS allowed to run as executable, and I am the owner.)

this is the result when i try to use terminal:

```
yoyo@musicbox:~/android$ chmod +x ./reflash
yoyo@musicbox:~/android$ gksudo ./reflash
yoyo@musicbox:~/android$ sudo ./reflash
sudo: unable to execute ./reflash: Permission denied
yoyo@musicbox:~/android$ 

```
the gksudo command gives a gui admin password prompt. after entering the pword, it just gives a new prompt in the terminal. the other tries just say permission denied. The program never shows up. The only threads i can find are about enabling the "allow execution as program" flag.

---

### Post by Perfect Storm on 2011-04-02
Tried with sh instead of ./ ?

---

### Post by alayoyo on 2011-04-02
> **Artificial Intelligence said:**
> Tried with sh instead of ./ ?

I may be interpreting this wrong, but i tried this:


```

$ cd /home/yoyo/android/
$ reflash
sh: reflash: not found
$ /home/yoyo/android/reflash
sh: /home/yoyo/android/reflash: Permission denied
$ sudo /home/yoyo/android/reflash
sudo: unable to execute /home/yoyo/android/reflash: Permission denied
$ 

```
:confused:

---

### Post by Perfect Storm on 2011-04-02
```
cd ~/android
sudo sh reflash
```

---

### Post by alayoyo on 2011-04-02
> **Artificial Intelligence said:**
> ```
cd ~/android
sudo sh reflash
```

thanks, but then i got a new error:

```

yoyo@musicbox:~$ cd /home/yoyo/android
yoyo@musicbox:~/android$ sudo sh reflash
[sudo] password for yoyo: 
reflash: 1: Syntax error: "(" unexpected


```i also tried that from within sh:

```
$ cd /home/yoyo/android/
$ sudo sh reflash
reflash: 1: Syntax error: "(" unexpected
$ 
```

---

### Post by Perfect Storm on 2011-04-02
Can you please provide a link to the stuff you're trying to install.

---

### Post by alayoyo on 2011-04-02
File is:
[http://downloads.unrevoked.com/recovery/3.32/reflash.tar.gz](http://downloads.unrevoked.com/recovery/3.32/reflash.tar.gz)

from this website:
[http://unrevoked.com/recovery/](http://unrevoked.com/recovery/)

---

### Post by Perfect Storm on 2011-04-03
```
cd
wget http://downloads.unrevoked.com/recovery/3.32/reflash.tar.gz
tar zxf reflash.tar.gz
sudo ./reflash
```

Did for me. 
I think you forgot extract the package. The **tar zxf reflash.tar.gz** upacks .tar.gz (or just right click and click exttract).

---

### Post by alayoyo on 2011-04-03
> **Artificial Intelligence said:**
> ```
cd
wget http://downloads.unrevoked.com/recovery/3.32/reflash.tar.gz
tar zxf reflash.tar.gz
sudo ./reflash
```Did for me. 
I think you forgot extract the package. The **tar zxf reflash.tar.gz** upacks .tar.gz (or just right click and click exttract).

I had used the archive manager gui to extract before, and have a file called "reflash" that nautilus lists are "executable"

I redownloaded and extracted on command line 
```

yoyo@musicbox:~/android$ tar xvfz reflash.tar.gz
reflash
yoyo@musicbox:~/android$

```

but i try to run in i'm still getting the same errors as before.

---

### Post by Perfect Storm on 2011-04-03
Strange...Lets see it's permissions:
```
ls -l reflash
```


By the way, are you logged in with a user that is allowed to use **sudo**? You're not using a guest account or something?

---

### Post by alayoyo on 2011-04-04
> **Artificial Intelligence said:**
> Strange...Lets see it's permissions:
```
ls -l reflash
```By the way, are you logged in with a user that is allowed to use **sudo**? You're not using a guest account or something?

here is the output for that...
```

yoyo@musicbox:~$ cd /home/yoyo/android/
yoyo@musicbox:~/android$ ls -l reflash
-rwxr-xr-x 1 yoyo androot 27554756 2011-01-07 23:54 reflash
yoyo@musicbox:~/android$ 


```i'm pretty sure my account can use sudo (once i enter my pword). not really sure how to test this. i log in on boot-up with 'yoyo' and my pword. when i need to sudo, i enter that same pword.
the 'androot' thing was a group i added a few days ago, while trying to fix this. the group i see for properties on folder is yoyo (and user yoyo) which i assume is from when i first installed.

---

### Post by Perfect Storm on 2011-04-04
hm...is it a wubi install or a real install of Ubuntu? I'm running out of ideas what it can be, as the previous codes I showed earlier worked for me (and I'm running 64-bit as well). Try put 'group' back to yoyo, try again.

also try first with
```
chmod x+a reflash
./reflash
#or
sh reflash
```

---

### Post by alayoyo on 2011-04-10
Well i figured out it was actually a conflict of an program for 32 bit vs running 64 bit OS, although if you have some libraries installed already it can still work.

I had an old 32 bit laptop in the closet, and it worked on there.  I sort of forgot that 32/64 is still an issue sometimes.

thanks for the help, AI

---

