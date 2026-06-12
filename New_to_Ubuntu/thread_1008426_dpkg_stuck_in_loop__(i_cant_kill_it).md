---
title: "dpkg stuck in loop  (i cant kill it)"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by JohnsShadow on 2008-12-11
hi when i try to open synaptic i get this error

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

when i run dpkg --configure -a it starts this sequence

```
Setting up pacpl (4.0.0-1) ...
CPAN: Storable loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  ftp://cpan.calvin.edu/pub/CPAN/authors/01mailrc.txt.gz
```

after a period of time i get this error

```
LWP failed with code[500] message[LWP:rotocol::MyFTP: connect: timeout]
Fetching with Net::FTP:
ftp://cpan.calvin.edu/pub/CPAN/authors/01mailrc.txt.gz
```

then it starts over looking for the same file again

when i open the system process i cannot find a package manager running
i have tryed rebooting

how do i stop dpkg from constantly looking for the file and how to i purge the installation of the program so that i can try again?
how to i cleanse this installation of the program so i can try again

---

### Post by bodhi.zazen on 2008-12-11
What were you installing and how were you installing it ?

---

### Post by decoherence on 2008-12-11
Don't know where you found this pacpl package, but try

```
sudo dpkg -r pacpl
```

then try running your
```

dpkg --configure -a
```

---

### Post by JohnsShadow on 2008-12-11
i was installing pacpl (pearl audio converter)
[http://pacpl.sourceforge.net/](http://pacpl.sourceforge.net/)

i was installing it as a .deb file through Gdeb package installer

---

### Post by JohnsShadow on 2008-12-11
> **decoherence said:**
> Don't know where you found this pacpl package, but try

```
sudo dpkg -r pacpl
```



Thanks that did the trick

i will remember that code ):P

---

