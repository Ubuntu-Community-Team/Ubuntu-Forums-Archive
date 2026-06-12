---
title: "tar.gz (help installation). GNU Scheme"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-05-02
Hey all, thanks for the help in advance. I am new to linux. 

Issue: I am trying to install MIT/GNU Scheme (programing language) on my 10.04 Ubuntu 64bit. The file which i downloaded is called    < mit-scheme-0.0.1-x86-64.tar.gz >  

I am wondering how I would install this file. I can see no readme. However, at the website there is a page called "http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user/Unix-Installation.html" but im not sure if I should follow these instructions.  

Already i opened (unpacked?) the file with archive manager which let me see all the files/folders inside, just not sure, from there, how to install. 

 Thanks in advance.

---

### Post by old fert on 2010-05-02
I'll be following your post.  I just deleted a bunch of tar.gz files because I couldn't figure out how to install them.  Good luck.

---

### Post by kwacka on 2010-05-02
Installation instructions are at the the download site: [HTML]http://www.gnu.org/software/mit-scheme/[/HTML]

It is also usual for installation instructions to be part of the archive (usually INSTALL or README plain text files).

Check it out, any problems come back.

---

### Post by da burger on 2010-05-02
You may want to look into checkinstall. The instructions on that website will work but uninstalling the software is often difficult. If you use checkinstall it will create a package that can be manipulated using synaptic. To do it with checkinstall: ```
sudo apt-get install checkinstall
./configure
make compile-microcode
sudo checkinstall
```

---

### Post by UbuNoob001 on 2010-05-02
The site said to:>  
[LIST=1]
[*]Unpack the tar file, mit-scheme-VERSION-ARCH.tar.gz,  into the directory mit-scheme-VERSION.   For example,                 tar xzf mit-scheme-9.0-i386.tar.gz
     will create a new directory mit-scheme-9.0.
[*]Move into the new directory:                 cd mit-scheme-VERSION/src
[*]Configure the software:                 ./configure
[*]Build the software:                 make compile-microcode
[*]Install the software:                 make install
[/LIST]
     After installing the software, you can delete the unpacked  directory:  
     cd ../..
     rm -rf mit-scheme-VERSION

i was able to do step 1&2 but unable to configure the software . 
./configure did nothing

---

### Post by oldos2er on 2010-05-02
Can you post the output from "./configure"? Have you installed the package build-essential ?

---

### Post by Arlion on 2010-05-02
this thread helped me.
[http://ubuntuforums.org/showthread.php?t=1400266&highlight=install+tar.gz](http://ubuntuforums.org/showthread.php?t=1400266&highlight=install+tar.gz)

quickly, the part i kept messing up on was where to put the folder for a proper installation so i didnt have to 'cd' and have to find it. Home. is the answer :P

---

