---
title: "tarball iscan"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by delphin on 2009-01-04
Hi,
i am trying to install a tarball of iscan for my epson scanner, since alien conversion of the rpm package does not work.
./configure ran without a problem
then 
sudo make 
and it ended with
/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libsane-epkowa.la] Error 1
make[3]: Leaving directory `/home/xx/Desktop/iscan-2.3.0/backend'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/xx/Desktop/iscan-2.3.0/backend'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/xx/Desktop/iscan-2.3.0'
make: *** [all] Error 2

could anyone please help me figure this out???
i dearly appreciate any input / support.
thanks
heinz

---

### Post by RomeReactor on 2009-01-04
Hi. By the error output:
> **/usr/bin/ld: ./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC**
./.libs/libsane-epkowa-s.a(libsane_epkowa_s_la-epkowa-s.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libsane-epkowa.la] Error 1
make[3]: Leaving directory `/home/xx/Desktop/iscan-2.3.0/backend'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/xx/Desktop/iscan-2.3.0/backend'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/xx/Desktop/iscan-2.3.0'
make: *** [all] Error 2
looks like you have to run configure like this:
```
./configure -fPIC
```
Do you have a link for the source? Are you running Ubuntu 64 bit?

---

