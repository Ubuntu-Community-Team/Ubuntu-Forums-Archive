---
title: "problem in installing java in ubuntu 11.04"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by konsolelover on 2011-05-24
hello everyone, i just download jre-6u25-linux-i586.bin and jdk-6u25-linux-i586.bin files from official sun java site. then i installed them using 
sudo chmod a+x file-name.bin
sudo ./file_name.bin 
commands for both jdk and jre. then i tried to compile my first java program in ubuntu from terminal and changed the directory to jdk1.6/bin and tried to compile it using
$ javac file_name.java
and got the error

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>


pls help..............

---

### Post by beew on 2011-05-24
[http://ubuntuforums.org/showthread.php?p=10850120#post10850120](http://ubuntuforums.org/showthread.php?p=10850120#post10850120)

See my posst #3

---

### Post by konsolelover on 2011-05-24
can someone plz illustrate in offline mode bcoz i am having some network issues when i'm trying to add ppa in ubuntu center when it try to update repository it gives error to check your internet connection....while everything just works fine even my download.....so please help ...i have self extractor bin files........thanks

---

### Post by Azdour on 2011-05-25
Hi,

I agree with beew. You seem to have installed the jre and jdk. If you installed the jre first then this probably told your machine to use the jre for java related things, and I believe jre does not come with javac. You need to follow beew's suggestion to update the java on your system to the jdk you installed.

If you are unsure what the java package is called run:

```
sudo update-alternatives --config java
```

This should list which versions of Java have been installed on your machine. Its also a good way to check that the jre and jdk you installed are installed correctly on you system, i.e. you can see them in the list that command above produces.

---

