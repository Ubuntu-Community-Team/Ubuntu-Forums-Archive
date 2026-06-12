---
title: "iBook debian need synaptic"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by ant2ne on 2009-02-14
I need synaptic installed on my debian (not ubuntu) xfce iBook. Is it possible? I like cli apt-get, but the GUI is handy too. How do i install synaptic from the command line.

```
badapple:/etc/X11# apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
badapple:/etc/X11# 

```

---

### Post by SunnyRabbiera on 2009-02-14
it should be installed apt-get install synaptic but remember to use superuser mode.
what version of debian are you using?

---

### Post by ant2ne on 2009-02-14
Sorry i guess that does help. xfce and 40r7 for the ppc architecture.

---

### Post by kerry_s on 2009-02-14
do you got all the repo's on, make sure you add "contrib non-free" to the end, su, then "apt-get update", then "apt-get install synaptic".

if your not sure post your /etc/apt/sources.list and will do the changes for you to copy.

---

### Post by ant2ne on 2009-02-15
```

ant2ne@badapple:~$ cat /etc/apt/sources.list 
# 
# deb cdrom:[Debian GNU/Linux 4.0 r7 _Etch_ - Official powerpc xfce-CD Binary-1 20090210-03:12]/ etch contrib main

deb cdrom:[Debian GNU/Linux 4.0 r7 _Etch_ - Official powerpc xfce-CD Binary-1 20090210-03:12]/ etch contrib main

# Line commented out by installer because it failed to verify:
#deb http://security.debian.org/ etch/updates main contrib
# Line commented out by installer because it failed to verify:
#deb-src http://security.debian.org/ etch/updates main contrib
ant2ne@badapple:~$
```

---

### Post by kerry_s on 2009-02-15
you missing the main repo and your security repo is off:

```

#deb cdrom:[Debian GNU/Linux 4.0 r7 _Etch_ - Official powerpc xfce-CD Binary-1 20090210-03:12]/ etch contrib main

# Line commented out by installer because it failed to verify:
deb ftp://ftp.debian.org/debian/ etch main contrib non-free
deb ftp://ftp.debian-multimedia.org etch main
deb http://security.debian.org/ etch/updates main contrib non-free

# Line commented out by installer because it failed to verify:
#deb-src http://security.debian.org/ etch/updates main contrib


```

however, i recommend you go lenny instead it's more up to date and just better. here's the new xfce4+lxde installer, i recommend you try lxde as it will is far lighter than xfce4:
[http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso)

---

