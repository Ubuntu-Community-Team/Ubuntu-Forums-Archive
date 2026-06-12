---
title: "Any way to avoid polluting /usr/lib et al.?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by ebirah on 2010-05-12
I want to run a set of applications which came with their own .so library. This library is irrelevant to all other applications. On Windows, you can just put the .dll in the same directory as the executable. This doesn't work on Linux (at least not for me); "cannot open shared object file: No such file or directory". Is there any way to run these programs without either adding the library to a system directory or editing system configuration files?

---

### Post by ajgreeny on 2010-05-12
If you try to run the applications in terminal they may spit out an error message telling you what files are missing, eg  ```
can not find** /usr/lib/folder/file.so**
```If so simply copy your **file**.so to that destination.

Worth trying, I think.

---

### Post by gmargo on 2010-05-12
You can try the **LD_LIBRARY_PATH** environment variable.  Similar format to $PATH, it controls the order of directory searching for shared libraries.  See the **ld.so** man page for more info.

---

### Post by srs5694 on 2010-05-12
If the program came as a Debian package (.deb file) or if you installed it via apt-get, Synaptic, or a similar standard Debian package installer, you shouldn't muck with it. The locations of the files are recorded in the package manager database, so trying to move them will just end up creating problems down the line. You shouldn't think of these files as "pollution;" they're *supposed* to go there!

If you installed the package by compiling it from source code yourself or by using some non-standard installer, it's conceivable that another location (in /usr/local or /opt, say) would make more sense, but it's hard to be more precise without knowing more details, such as what the program is and how you obtained and installed it.

For more details on where various files are supposed to go in Linux, consult the [Filesystem Hierarchy Standard (FHS).](http://www.pathname.com/fhs/)

---

### Post by ebirah on 2010-05-13
> **ajgreeny said:**
> If you try to run the applications in terminal they may spit out an error message telling you what files are missing, eg  ```
can not find** /usr/lib/folder/file.so**
```If so simply copy your **file**.so to that destination.

Worth trying, I think, moron.

I know 'what files are "missing"'. I was mainly just **CURIOUS** about whether you can temporarily add a library search directory or not. Perhaps it is difficult to see beyond immediate utility. ;-))))))))))))))

I should have been clearer in the OP. It's basically a c++ library which comes with some programs which are built at the same time as the library. I compiled it myself. As I'm just experimenting with it for now, I want the "installation" to be self-contained. I am aware that I could have copied the .so to /usr/lib/..., but **I DON'T WANT TO** if it can be avoided. I could make my own .deb package, but if there is a way to add a search directory temporarily or for a specific program (maybe using a shell script) then that would have been easier. I don't really care anymore.

---

### Post by srs5694 on 2010-05-13
In that case, check out the LD_LIBRARY_PATH environment variable. See [here,](http://www.faqs.org/docs/Linux-HOWTO/Program-Library-HOWTO.html#AEN77) for example, or Google it.

---

### Post by ajgreeny on 2010-05-13
I did _not_ call you a moron and did not think you are one;  I was merely trying to help, so please don't add your own words to my post when you quote it, and make it look as if I was being rude to you;  I was not!

---

### Post by ebirah on 2010-05-14
> **srs5694 said:**
> In that case, check out the LD_LIBRARY_PATH environment variable. See [here,]("http://www.faqs.org/docs/Linux-HOWTO/Program-Library-HOWTO.html#AEN77") for example, or Google it.

Thanks :D

---

