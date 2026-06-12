---
title: "error when trying to &quot;make&quot;"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by rupsyco on 2009-03-25
Dear forum...

I'm trying to compile gspeakers, unsuccessfully. I followed instructions in the readme file but I've got this:

riccardo@riccardo:~/Desktop/gspeakers-0.11$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... none
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.4 libxml-2.0... yes
checking DEPS_CFLAGS... -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2  
checking DEPS_LIBS... -lgtkmm-2.4 -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lxml2  
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  sv
checking how to run the C++ preprocessor... g++ -E
checking vector usability... yes
checking vector presence... yes
checking for vector... yes
checking iostream usability... yes
checking iostream presence... yes
checking for iostream... yes
checking fstream usability... yes
checking fstream presence... yes
checking for fstream... yes
checking string usability... yes
checking string presence... yes
checking for string... yes
checking map usability... yes
checking map presence... yes
checking for map... yes
checking iterator usability... yes
checking iterator presence... yes
checking for iterator... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking strstream usability... yes
checking strstream presence... yes
checking for strstream... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating xml/Makefile
config.status: creating pixmaps/Makefile
config.status: creating gspeakers.desktop
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
riccardo@riccardo:~/Desktop/gspeakers-0.11$ make
make  all-recursive
make[1]: Entering directory `/home/riccardo/Desktop/gspeakers-0.11'
Making all in src
make[2]: Entering directory `/home/riccardo/Desktop/gspeakers-0.11/src'
source='main.cc' object='main.o' libtool=no \
	depfile='.deps/main.Po' tmpdepfile='.deps/main.TPo' \
	depmode=none /bin/bash ../depcomp \
	g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -c -o main.o `test -f 'main.cc' || echo './'`main.cc
/bin/bash: ../depcomp: No such file or directory
make[2]: *** [main.o] Error 127
make[2]: Leaving directory `/home/riccardo/Desktop/gspeakers-0.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/riccardo/Desktop/gspeakers-0.11'
make: *** [all] Error 2
riccardo@riccardo:~/Desktop/gspeakers-0.11$ 

I've seen in the forum that other people has had the same kind of error when trying to compile, but the thread had no conclusion and was closed with just other people having the same problem.

Hope you guys will help or if anyone knows about a ready package for Ubuntu or Debian... Thank you very much.

---

### Post by mc4man on 2009-03-26
That's a fairly old app, whether the app works right I won't know.

The easiest way to resolve your build issue is to start fresh, so delete the extracted gspeakers folder. Before extracting it again run this

```
sudo apt-get install automake1.7
```

Then extract the source and do your build.

You may want to do a checkinstall instead of a sudo make install.

If so, install checkinstall and after the make use this at a min.
```
sudo checkinstall --fstrans=no


```

---

### Post by rupsyco on 2009-03-26
Well it did improve after that, but when I called checkinstall that seems like it's not there. I tried make install and few things ran ok but I still got some error on some portion (I'm pasting the whole thing... sorry for junking up)

riccardo@riccardo:~/Desktop/gspeakers-0.11$ sudo make install
Making install in src
make[1]: Entering directory `/home/riccardo/Desktop/gspeakers-0.11/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT main.o -MD -MP -MF ".deps/main.Tpo" \
	  -c -o main.o `test -f 'main.cc' || echo './'`main.cc; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
	else rm -f ".deps/main.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT common.o -MD -MP -MF ".deps/common.Tpo" \
	  -c -o common.o `test -f 'common.cc' || echo './'`common.cc; \
	then mv -f ".deps/common.Tpo" ".deps/common.Po"; \
	else rm -f ".deps/common.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT gspeakersobject.o -MD -MP -MF ".deps/gspeakersobject.Tpo" \
	  -c -o gspeakersobject.o `test -f 'gspeakersobject.cc' || echo './'`gspeakersobject.cc; \
	then mv -f ".deps/gspeakersobject.Tpo" ".deps/gspeakersobject.Po"; \
	else rm -f ".deps/gspeakersobject.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT part.o -MD -MP -MF ".deps/part.Tpo" \
	  -c -o part.o `test -f 'part.cc' || echo './'`part.cc; \
	then mv -f ".deps/part.Tpo" ".deps/part.Po"; \
	else rm -f ".deps/part.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT net.o -MD -MP -MF ".deps/net.Tpo" \
	  -c -o net.o `test -f 'net.cc' || echo './'`net.cc; \
	then mv -f ".deps/net.Tpo" ".deps/net.Po"; \
	else rm -f ".deps/net.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT crossover.o -MD -MP -MF ".deps/crossover.Tpo" \
	  -c -o crossover.o `test -f 'crossover.cc' || echo './'`crossover.cc; \
	then mv -f ".deps/crossover.Tpo" ".deps/crossover.Po"; \
	else rm -f ".deps/crossover.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT crossoverlist.o -MD -MP -MF ".deps/crossoverlist.Tpo" \
	  -c -o crossoverlist.o `test -f 'crossoverlist.cc' || echo './'`crossoverlist.cc; \
	then mv -f ".deps/crossoverlist.Tpo" ".deps/crossoverlist.Po"; \
	else rm -f ".deps/crossoverlist.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT speaker.o -MD -MP -MF ".deps/speaker.Tpo" \
	  -c -o speaker.o `test -f 'speaker.cc' || echo './'`speaker.cc; \
	then mv -f ".deps/speaker.Tpo" ".deps/speaker.Po"; \
	else rm -f ".deps/speaker.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT speakerlist.o -MD -MP -MF ".deps/speakerlist.Tpo" \
	  -c -o speakerlist.o `test -f 'speakerlist.cc' || echo './'`speakerlist.cc; \
	then mv -f ".deps/speakerlist.Tpo" ".deps/speakerlist.Po"; \
	else rm -f ".deps/speakerlist.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT box.o -MD -MP -MF ".deps/box.Tpo" \
	  -c -o box.o `test -f 'box.cc' || echo './'`box.cc; \
	then mv -f ".deps/box.Tpo" ".deps/box.Po"; \
	else rm -f ".deps/box.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT boxlist.o -MD -MP -MF ".deps/boxlist.Tpo" \
	  -c -o boxlist.o `test -f 'boxlist.cc' || echo './'`boxlist.cc; \
	then mv -f ".deps/boxlist.Tpo" ".deps/boxlist.Po"; \
	else rm -f ".deps/boxlist.Tpo"; exit 1; \
	fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -MT speakereditor.o -MD -MP -MF ".deps/speakereditor.Tpo" \
	  -c -o speakereditor.o `test -f 'speakereditor.cc' || echo './'`speakereditor.cc; \
	then mv -f ".deps/speakereditor.Tpo" ".deps/speakereditor.Po"; \
	else rm -f ".deps/speakereditor.Tpo"; exit 1; \
	fi
speakereditor.cc: In member function ‘void Speaker_ListStore::on_selection_changed()’:
speakereditor.cc:554: error: ‘strtok’ was not declared in this scope
speakereditor.cc: In member function ‘void Speaker_ListStore::draw_imp_plot(Speaker&, bool)’:
speakereditor.cc:662: error: ‘strstr’ was not declared in this scope
speakereditor.cc:668: error: ‘strtok’ was not declared in this scope
speakereditor.cc:702: error: ‘strtok’ was not declared in this scope
make[1]: *** [speakereditor.o] Error 1
make[1]: Leaving directory `/home/riccardo/Desktop/gspeakers-0.11/src'
make: *** [install-recursive] Error 1
riccardo@riccardo:~/Desktop/gspeakers-0.11$ 

But I'm quite happy that at least got some improvement... what is it actually that I did?? hahaha... what does that program do?

Thank you very much for your help and... this forum is very quick I've seen a couple of hundreds of post in the last few hours.

---

### Post by snova on 2009-03-26
> **rupsyco said:**
> ```

speakereditor.cc: In member function &#8216;void Speaker_ListStore::on_selection_changed()&#8217;:
speakereditor.cc:554: error: &#8216;strtok&#8217; was not declared in this scope
speakereditor.cc: In member function &#8216;void Speaker_ListStore::draw_imp_plot(Speaker&, bool)&#8217;:
speakereditor.cc:662: error: &#8216;strstr&#8217; was not declared in this scope
speakereditor.cc:668: error: &#8216;strtok&#8217; was not declared in this scope
speakereditor.cc:702: error: &#8216;strtok&#8217; was not declared in this scope
make[1]: *** [speakereditor.o] Error 1
make[1]: Leaving directory `/home/riccardo/Desktop/gspeakers-0.11/src'
make: *** [install-recursive] Error 1
riccardo@riccardo:~/Desktop/gspeakers-0.11$
```

But I'm quite happy that at least got some improvement... what is it actually that I did?? hahaha... what does that program do?

Thank you very much for your help and... this forum is very quick I've seen a couple of hundreds of post in the last few hours.

Looks like a minor problem in the source code. Open src/speakereditor.cc, and add this line at the top:

[PHP]#include <string.h>[/PHP]

---

### Post by rupsyco on 2009-03-26
I found some more errors, but guessed that perhaps were all related to #include <string.h> missing... and true :P

Thank you very much guys for your support!

---

### Post by BudBear on 2009-12-19
> **rupsyco said:**
> I found some more errors, but guessed that perhaps were all related to #include <string.h> missing... and true :P

Thank you very much guys for your support!

what other errors did you find? i am pretty much at the same point as you were here and added the #include <string.h> but still get the following:

> filterlinkframe.cc: In member function ‘void FilterLinkFrame::on_plot_crossover()’:
filterlinkframe.cc:676: error: ‘strstr’ was not declared in this scope
filterlinkframe.cc:682: error: ‘strtok’ was not declared in this scope
filterlinkframe.cc:705: error: ‘strtok’ was not declared in this scope
make[2]: *** [filterlinkframe.o] Error 1
make[2]: Leaving directory `/home/pcstudio/Desktop/downloads/gspeakers-0.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pcstudio/Desktop/downloads/gspeakers-0.11'
make: *** [all] Error 2
pcstudio@studioPC:~/Desktop/downloads/gspeakers-0.11$ 

---

### Post by BudBear on 2009-12-19
figured it out. i had to add the #include <string.h> to popupentry.cc, freqrespeditor.cc, and summedfreqrespplot.cc

program works!  now it wont let me create a launcher, or put a link on the desktop.  gives me a permissions error. so i am in the process of determining what i need to do  to get permissions. chmod 777 if i remember correctly, but on what?

---

### Post by grindstone on 2010-06-08
Basically two things to get this--fix a link and add one line to five files.

1)    fix bad depcomp link in local gspeakers dir

search for your depcomp path
~/gspeakers/gspeakers-0.11$ sudo find / -name "*depcomp*"
/usr/share/automake-1.10/depcomp
/home/custom/gspeakers/gspeakers-0.11/depcomp

~/gspeakers$    ln -sf /usr/share/automake-1.10/depcomp ./depcomp

2)    add 

#include <string.h> 

near the rest of the #includes at the top of the files 

speakereditor.cc
popupentry.cc
summedfreqrespplot.cc
freqrespeditor.cc
filterlinkframe.cc

FWIW.  Worked for me.

---

### Post by Michl on 2011-02-12
> **grindstone said:**
> Basically two things to get this--fix a link and add one line to five files.

1)    fix bad depcomp link in local gspeakers dir

search for your depcomp path
~/gspeakers/gspeakers-0.11$ sudo find / -name "*depcomp*"
/usr/share/automake-1.10/depcomp
/home/custom/gspeakers/gspeakers-0.11/depcomp

~/gspeakers$    ln -sf /usr/share/automake-1.10/depcomp ./depcomp

2)    add 

#include <string.h> 

near the rest of the #includes at the top of the files 

speakereditor.cc
popupentry.cc
summedfreqrespplot.cc
freqrespeditor.cc
filterlinkframe.cc

FWIW.  Worked for me.

Worked for me, too.  Thank you so much!  (After installing
automake).

---

