---
title: "PARTIMAGE-0.6.9.tar.bz2/HELP ME PLEASEEEEE"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by mylnx on 2011-08-15
PLEASE HELP ME!
               I am attempting ti install partimage-0.6.9.tar.bz2 in UBUNTU 10.04.  I am getting really frustrated!  Here is what I have done so far

jb@jb-laptop:/$ cd /tmp
jb@jb-laptop:/tmp$ ls -l
total 684
srwxr-xr-x 1 jb  jb       0 2011-08-15 00:52 gedit.jb.160972927
drwx------ 2 jb  jb    4096 2011-08-14 23:40 keyring-6Ii6te
drwx------ 2 gdm gdm   4096 2011-08-14 23:40 orbit-gdm
drwx------ 2 jb  jb    4096 2011-08-15 00:54 orbit-jb
-rwxrwxrwx 1 jb  jb  666522 2011-08-15 00:30 partimage-0.6.9.tar.bz2
drwx------ 2 jb  jb    4096 2011-08-15 00:32 plugtmp
drwx------ 2 gdm gdm   4096 2011-08-14 23:41 pulse-PKdhtXMmr18n
drwx------ 2 jb  jb    4096 2011-08-14 23:40 pulse-XJFYPZ52d6NL
drwx------ 2 jb  jb    4096 2011-08-14 23:40 ssh-vTvtPO1600
drwx------ 2 jb  jb    4096 2011-08-14 23:41 virtual-jb.Xfo6Do
jb@jb-laptop:/tmp$ sh ./configure
sh: Can't open ./configure
jb@jb-laptop:/tmp$ sh ./configure partimage-0.6.9.tat.bz2
sh: Can't open ./configure
jb@jb-laptop:/tmp$ ./configure partimage-0.6.9.tar.bz2
bash: ./configure: No such file or directory
jb@jb-laptop:/tmp$ sh
$ partimage-0.6.9.tar.bz2
sh: partimage-0.6.9.tar.bz2: not found
$ pwd
/tmp
$ cd ..
$ cd /
$ pwd
/
$ csh ./configure
sh: csh: not found
$ csh
sh: csh: not found
$ bsh
BeanShell 2.0b4 - by Pat Niemeyer (pat@pat.net)
bsh % ./configure
// Error: Parser Error: Parse error at line 1, column 1.  Encountered: .
bsh % configure
patrimage-0.6.9.tar.bz2
// Error: Parser Error: Parse error at line 3, column 1.  Encountered: patrimage
bsh % // Error: Parser Error: Parse error at line 1, column 4.  Encountered: .9
bsh % 

WHAT should I do to get this installed?

Thanks in advance everyone!  :popcorn:

---

### Post by WyleECoyote on 2011-08-15
do you have to have partimage? if not I highly recommend partclone here
[http://partclone.org/](http://partclone.org/)

have been using it for a long time without fail and is something I can easily help with

---

### Post by WyleECoyote on 2011-08-15
btw if you have to have partimage, you need to extract first with this command:

```
tar xfjp partimage-0.6.9.tar.bz2
```

then:
```
./configure --prefix=/usr && make && make install
```

as far as using it I have never tried it

---

### Post by fdrake on 2011-08-15
you don't need to compile it from source. partimage is on your repositories:

```
sudo apt-get install partimage partimage-doc
```

make sure you have your repo enabled.

---

### Post by Elfy on 2011-08-15
You've got to extract it before you compile it. 

You can also install it from the repos - though it's not the latest version.

You can also get it in SystemRescueCD. 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.partimage.org/Download](http://www.partimage.org/Download) - there's a how to compile section.

---

### Post by ciampix on 2011-09-10
> **mylnx said:**
> PLEASE HELP ME!
               I am attempting ti install partimage-0.6.9.tar.bz2 in UBUNTU 10.04.  I am getting really frustrated!  Here is what I have done so far

....

WHAT should I do to get this installed?

Thanks in advance everyone!  :popcorn:

Are you 64bit? Partimage (apt-get install partimage partimage-doc) is 32bit only... go sourceforge for partclone if you do on a 64bit ubuntu 10.04 ...

bye

---

