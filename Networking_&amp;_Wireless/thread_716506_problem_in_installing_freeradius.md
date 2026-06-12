---
title: "problem in installing freeradius"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by sheshe on 2008-03-06
I[COLOR="Black"] try to install freeradius 1.1.7 in ubuntu 1.10. but lots of error and warning while doing 'make'.:confused::confused:

Please...i have spend lots oftime doing this, but nothing change...[/COLOR].

[COLOR="Red"]*** Warning: Linking the shared library rlm_perl.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portable!
gcc -shared  .libs/rlm_perl.o  -Wl,--rpath -Wl,/home/ashitah/freeradius-1.1.7/src/lib/.libs /home/ashitah/freeradius-1.1.7/src/lib/.libs/libradius.so -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lc -lcrypt -lnsl -lresolv -lpthread  -Wl,-E -Wl,-soname -Wl,rlm_perl-1.1.7.so -o .libs/rlm_perl-1.1.7.so
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[6]: *** [rlm_perl.la] Error 1
make[6]: Leaving directory `/home/ashitah/freeradius-1.1.7/src/modules/rlm_perl'
make[5]: *** [common] Error 2
make[5]: Leaving directory `/home/ashitah/freeradius-1.1.7/src/modules'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/ashitah/freeradius-1.1.7/src/modules'
make[3]: *** [common] Error 2
make[3]: Leaving directory `/home/ashitah/freeradius-1.1.7/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ashitah/freeradius-1.1.7/src'
make[1]: *** [common] Error 2
make[1]: Leaving directory `/home/ashitah/freeradius-1.1.7'
make: *** [all] Error 2
[/COLOR]

Hope to hear the solution soon.Thanks in advance

---

