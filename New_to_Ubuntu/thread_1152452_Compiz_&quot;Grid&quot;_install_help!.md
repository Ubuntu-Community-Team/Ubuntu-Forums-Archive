---
title: "Compiz &quot;Grid&quot; install help!"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by mern1 on 2009-05-07
I'm trying to install the Grid plugin for Compiz.  I found great directions [here]("http://wiki.compiz-fusion.org/Plugins/Grid"); however, when I run the "git clone git://anon...." command I get the following error: "fatal: The remote end hung up unexpectedly".  I have no idea what this error means or what the git command does.  Can someone please help?  Thanks

---

### Post by finer recliner on 2009-05-08
git is a repository for software packages that also manages version control. basically the command you are stuck on is trying to download a copy of the files needed install your plugin from a remote server.


there are a couple troubleshooting steps for your given error at:

[http://git.or.cz/gitwiki/GitFaq#head-748cd02e89bfc354f7813cafd9ecbce476e38c34](http://git.or.cz/gitwiki/GitFaq#head-748cd02e89bfc354f7813cafd9ecbce476e38c34)

---

### Post by mern1 on 2009-05-11
Turns out the address (or whatever its called) was wrong.  I eventually found the right one and it appears to have downloaded the files and created a new directory.  Now I can't get make to work.  

Contents of grid:
```
@AMD-linux:~/grid$ ls
CMakeLists.txt  grid.xml.in  src
```

Contents of CMakeLists.txt:
```
find_package (Compiz REQUIRED)

include (CompizPlugin)

compiz_plugin(grid)
```

If I try to make with the CMakeLists.txt file I get the following error:
```
@AMD-linux:~/grid$ make -f CMakeLists.txt 
CMakeLists.txt:1: *** missing separator.  Stop.
```

Am I missing a makefile?  Do I have to create one?  What am I doing wrong?

---

