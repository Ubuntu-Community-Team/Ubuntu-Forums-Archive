---
title: "source code???///"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-04
where can i find the source code of ubuntu... i mean as we can see the source code of a web page i wanna see yhe source code of ubuntu so were can i find it? pls somebody help thanx to all

---

### Post by Linyx on 2011-01-04
> **neo_aryan said:**
> where can i find the source code of ubuntu... i mean as we can see the source code of a web page i wanna see yhe source code of ubuntu so were can i find it? pls somebody help thanx to all

[SIZE=2]"[/SIZE][SIZE=3]This is a common misunderstanding as to the role of Ubuntu - there isn't
really much "Ubuntu source code", there's just the code of the various
"upstream" projects (GNOME - which is itself composed of many disparate
projects, the linux kernel, bzr, etc) that are shipped together to form
an Ubuntu install.[/SIZE]
[SIZE=2]"
Edit:- [/SIZE]
[SIZE=3]If you want to
modify a particular piece of software, all you need to do is to get the
source package (apt-get source $PACKAGENAME), make your change, build it
(with debuild or dpkg-buildpackage), then install the package.[/SIZE][SIZE=2] 
[/SIZE]

---

### Post by vivek.pandey on 2011-01-04
> **Linyx said:**
> [SIZE=2]"[/SIZE][SIZE=3]This is a common misunderstanding as to the role of Ubuntu - there isn't
really much "Ubuntu source code", there's just the code of the various
"upstream" projects (GNOME - which is itself composed of many disparate
projects, the linux kernel, bzr, etc) that are shipped together to form
an Ubuntu install.[/SIZE]
[SIZE=2]"
Edit:- [/SIZE]
[SIZE=3]If you want to
modify a particular piece of software, all you need to do is to get the
source package (apt-get source $PACKAGENAME), make your change, build it
(with debuild or dpkg-buildpackage), then install the package.[/SIZE][SIZE=2] 
[/SIZE]
  k so anyways were can i see those codes for kernel etc...?

---

### Post by Linyx on 2011-01-04
> **neo_aryan said:**
> k so anyways were can i see those codes for kernel etc...?


[SIZE=2]Go 4 it > [/SIZE][http://tldp.org/LDP/tlk/sources/sources.html](http://tldp.org/LDP/tlk/sources/sources.html)

---

### Post by Decatf on 2011-01-04
[http://kernel.ubuntu.com/git](http://kernel.ubuntu.com/git)

---

### Post by Leovi on 2011-01-04
Glad to be here. I love this place.

---

### Post by Verbeck on 2011-01-04
gnome ; [http://ftp.gnome.org/pub/GNOME/sources/](http://ftp.gnome.org/pub/GNOME/sources/)

just to add something.

---

### Post by vivek.pandey on 2011-01-04
> **Linyx said:**
> [SIZE=2]Go 4 it > [/SIZE][http://tldp.org/LDP/tlk/sources/sources.html](http://tldp.org/LDP/tlk/sources/sources.html)

no wat i actually wanna say is i have heard ubuntu comes with all codes..ie if i have ubuntu installed i can see the source code in it..i wanna know that file location and not a web site

---

### Post by Elfy on 2011-01-04
Post #2 appears to be lifted from - [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008045.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008045.html)

Read the whole reply. 

This points the same place ;)

[http://ubuntuforums.org/showpost.php?p=67109&postcount=6](http://ubuntuforums.org/showpost.php?p=67109&postcount=6)

---

### Post by vivek.pandey on 2011-01-05
> **forestpiskie said:**
> Post #2 appears to be lifted from - [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008045.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008045.html)

Read the whole reply. 

This points the same place ;)

[http://ubuntuforums.org/showpost.php?p=67109&postcount=6](http://ubuntuforums.org/showpost.php?p=67109&postcount=6)


i guess that reply was modified later to include my second question..:guitar:

---

