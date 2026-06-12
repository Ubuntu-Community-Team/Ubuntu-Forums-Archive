---
title: "Accessing My files"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by joebipp on 2009-10-09
Dear Xubuntu world I tried making a data base and I cannot seem to retrieve the info. Not sure what I am doing wrong:
joeb@joeb-laptop:~$ sudo su
root@joeb-laptop:/home/joeb# my family.dat
bash: my: command not found
root@joeb-laptop:/home/joeb# ls
arithmetic  Desktop    family      Math   mydata  Pictures  Templates
bin         Documents  family.dat  Music  mymenu  Public    Videos
root@joeb-laptop:/home/joeb# cd family
bash: cd: family: Not a directory
root@joeb-laptop:/home/joeb# cd family.dat
bash: cd: family.dat: Not a directory
root@joeb-laptop:/home/joeb# $family.dat
bash: .dat: command not found
root@joeb-laptop:/home/joeb# /family.dat
bash: /family.dat: No such file or directory
root@joeb-laptop:/home/joeb# 

Any ideas 
Joe

---

### Post by Zill on 2009-10-09
joebipp:  I don't really understand what you mean by "...making a data base".  Do you mean a spreadsheet produced by OpenOffice.org/Gnumeric etc or do you mean a relational database produced by an application such as MySQL?

Generally files produced by OpenOffice etc are held in your home directory and are therefore "owned" by you.  You should not need to use superuser permissions to access these files.  Please read the stickies at the start of the "Absolute Beginner Talk" section above for further help on this.

If the file you are trying to access is called "family.dat" then what application created this file?

Please clarify this and post the output of the following command to show the permissions associated with each file:
```
ls -l
```

---

### Post by cholericfun on 2009-10-09
> **joebipp said:**
> Dear Xubuntu world I tried making a data base and I cannot seem to retrieve the info. Not sure what I am doing wrong:
joeb@joeb-laptop:~$ sudo su
root@joeb-laptop:/home/joeb# my family.dat
bash: my: command not found
root@joeb-laptop:/home/joeb# ls
arithmetic  Desktop    family      Math   mydata  Pictures  Templates
bin         Documents  family.dat  Music  mymenu  Public    Videos
root@joeb-laptop:/home/joeb# cd family
bash: cd: family: Not a directory
root@joeb-laptop:/home/joeb# cd family.dat
bash: cd: family.dat: Not a directory
root@joeb-laptop:/home/joeb# $family.dat
bash: .dat: command not found
root@joeb-laptop:/home/joeb# /family.dat
bash: /family.dat: No such file or directory
root@joeb-laptop:/home/joeb# 

Any ideas 
Joe

i have no idea what youre trying to do but thought i might be able to help you understand why you didnt get any output:

```
my family.dat
```
is like trying to evoke a program called "my" with the option family.dat

in linux you dont have filenames with empty spaces, if there is (say from a windows file) you have a "\" in front of it like
my\ family.dat
putting just a filename into the terminal is of course not going to do anything
even when you:
```
/family.dat
```
in order to run a *program* in a particular folder (say one you compiled)
its:
```
./family.prog
```


maybe give us a better hint what your trying to do and maybe what guide youre following

---

