---
title: "Fortran library"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by ubugross on 2009-05-03
How I can install fortran library slatec on ubuntu 8.10?. Many thanks.

---

### Post by Spiritous on 2009-05-03
[http://packages.ubuntu.com/dapper/libs/slatec](http://packages.ubuntu.com/dapper/libs/slatec)

Might need 

[http://packages.ubuntu.com/dapper/g77](http://packages.ubuntu.com/dapper/g77) , [http://packages.ubuntu.com/hardy/devel/g77-3.4](http://packages.ubuntu.com/hardy/devel/g77-3.4)
, [http://packages.ubuntu.com/dapper/gcc-3.4](http://packages.ubuntu.com/dapper/gcc-3.4) and [http://packages.ubuntu.com/hardy/gcc-3.4-base](http://packages.ubuntu.com/hardy/gcc-3.4-base)

---

### Post by ubugross on 2009-05-03
> **ubugross said:**
> How I can install fortran library slatec on ubuntu 8.10?. Many thanks.
How I can install fortran library slatec on ubuntu 8.10?. Many thanks.

---

### Post by fabio.hipolito on 2009-05-06
Hello, it worked for me.

Yet before installing *slatec's* package, I installed the following packages
[LIST]
[*]g77-3.4
[*]cpp-3.4
[*]gcc-3.4
[*]gcc-3.4-base
[*]libg2c0
[*]libg2c0-dev
[/LIST]
To install these packages you should add hardy repositories, in order to do that see reply number #14 to the following post  (it is quoted at the bottom of this post)

[http://ubuntuforums.org/showthread.php?t=969198]("http://ubuntuforums.org/showthread.php?t=969198")

after having installed the packages listed above and its dependencies go to 

[http://packages.ubuntu.com/dapper/libs/slatec]("http://packages.ubuntu.com/dapper/libs/slatec")

download the package (its a .deb file) and just run it to install.

As I said it worked for me.

Notes
[LIST]
[*]I use g77 as my FORTRAN compiler, I have not tested it in any other compiler;
[*]Also this worked in Ubuntu 9.04 Jaunty Jackalope
[/LIST]

Best regards.

> **horvathd said:**
> I just added the following lines to the source.list after the lines of universe repositories for intrepid:

```
deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
```

(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, etc.)

after that in the terminal:

```
sudo aptitude update
sudo aptitude install g77
```

That worked for me.

---

