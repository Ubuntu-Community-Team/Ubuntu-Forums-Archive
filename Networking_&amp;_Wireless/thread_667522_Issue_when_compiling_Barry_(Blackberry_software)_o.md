---
title: "Issue when compiling Barry (Blackberry software) on Gutsy"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by leisuresuitgreg on 2008-01-14
Hi

I am trying to compile Barry-0.11 so that I can run my blackberry on Linux. I have installed all the dependancies and ./configure finishes without errors. However, when I try to run 'sudo make' I get these error messages.

```
greg@GregLappy:~/Programs/barry-0.11$ sudo make
make  all-recursive
make[1]: Entering directory `/home/greg/Programs/barry-0.11'
Making all in .
make[2]: Entering directory `/home/greg/Programs/barry-0.11'
rm -f ./barry
ln -s ./src ./barry
make[2]: Leaving directory `/home/greg/Programs/barry-0.11'
Making all in src
make[2]: Entering directory `/home/greg/Programs/barry-0.11/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/greg/Programs/barry-0.11/src'
Making all in tools
make[2]: Entering directory `/home/greg/Programs/barry-0.11/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/greg/Programs/barry-0.11/tools'
Making all in examples
make[2]: Entering directory `/home/greg/Programs/barry-0.11/examples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/greg/Programs/barry-0.11/examples'
Making all in man
make[2]: Entering directory `/home/greg/Programs/barry-0.11/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/greg/Programs/barry-0.11/man'
Making all in gui
make[2]: Entering directory `/home/greg/Programs/barry-0.11/gui'
make  all-recursive
make[3]: Entering directory `/home/greg/Programs/barry-0.11/gui'
Making all in .
make[4]: Entering directory `/home/greg/Programs/barry-0.11/gui'
make[4]: Leaving directory `/home/greg/Programs/barry-0.11/gui'
Making all in src
make[4]: Entering directory `/home/greg/Programs/barry-0.11/gui/src'
/bin/bash ../libtool --tag=CXX --mode=link g++ -ansi -Wall -g -g -O2   -o barrybackup  main.o BackupWindow.o DeviceSelectDlg.o DatabaseSelectDlg.o PasswordDlg.o ConfigDlg.o ConfigFile.o DeviceIface.o tarfile.o tarfile-ops-nt.o util.o  -L/home/greg/Programs/barry-0.11/src -L/usr/local/lib -lbarry -lusb   -pthread -L/usr/local/lib -lglademm-2.4 -lgtkmm-2.4 -lglade-2.0 -lgdkmm-2.4 -latkmm-1.6 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lrt -lglib-2.0   -ltar -lz
g++ -ansi -Wall -g -g -O2 -o .libs/barrybackup main.o BackupWindow.o DeviceSelectDlg.o DatabaseSelectDlg.o PasswordDlg.o ConfigDlg.o ConfigFile.o DeviceIface.o tarfile.o tarfile-ops-nt.o util.o -pthread  -L/home/greg/Programs/barry-0.11/src -L/usr/local/lib /home/greg/Programs/barry-0.11/src/.libs/libbarry.so /usr/local/lib/libusb.so /usr/lib/libglademm-2.4.so /usr/lib/libgtkmm-2.4.so /usr/lib/libglade-2.0.so /usr/lib/libgdkmm-2.4.so /usr/lib/libatkmm-1.6.so /usr/lib/libpangomm-1.4.so /usr/lib/libcairomm-1.0.so /usr/lib/libglibmm-2.4.so /usr/lib/libsigc-2.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libxml2.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/local/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage /usr/local/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 -lXfixes /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so -lrt /usr/lib/libglib-2.0.so -ltar -lz
/usr/lib/libpangomm-1.4.so: undefined reference to `pango_cairo_font_map_get_font_type'
/usr/lib/libpangomm-1.4.so: undefined reference to `pango_font_face_is_synthesized'
collect2: ld returned 1 exit status
make[4]: *** [barrybackup] Error 1
make[4]: Leaving directory `/home/greg/Programs/barry-0.11/gui/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/greg/Programs/barry-0.11/gui'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/greg/Programs/barry-0.11/gui'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/greg/Programs/barry-0.11'
make: *** [all] Error 2

```

I have the most up-to-date version of libcairo and libpango, so what am i missing? Any ideas, help would be very useful.

I am running Kubuntu Gutsy with KDE4 
Dell Inspiron 1300
Pentium M 1.8 GHz
512 MB RAM

Cheers in advance.

Greg

---

