---
title: "idevicerestore error"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by jepy10 on 2010-09-21
Hi im sorry im newbie in linux and i have search everywhere on google for help but i cant get pass this point i was following the tutorial on how to compile the idevicerestore on ubuntu but after i get the **libirecovery/git** and i cd into the directory and i type on the terminal **make linux && sudo make install** it tells me that it cant find the cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
cp: cannot stat `libirecovery.dylib': No such file or directory

so i went around and found that if i go into the makefile and remove the** install** info on there it will get me through so that worked but, i have a problem when i run the **make && sudo make install command on idevicerestore **it gives me this error:


jonathan@jonathan-laptop:~/idevicerestore$ make && sudo make install
Making all in src
make[1]: Entering directory `/home/jonathan/idevicerestore/src'
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I. -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/local/include -g -O2 -MT idevicerestore-idevicerestore.o -MD -MP -MF .deps/idevicerestore-idevicerestore.Tpo -c -o idevicerestore-idevicerestore.o `test -f 'idevicerestore.c' || echo './'`idevicerestore.c
In file included from idevicerestore.c:29:
dfu.h:29:26: error: libirecovery.h: No such file or directory
In file included from idevicerestore.c:29:
dfu.h:33: error: expected specifier-qualifier-list before ‘irecv_client_t’
make[1]: *** [idevicerestore-idevicerestore.o] Error 1
make[1]: Leaving directory `/home/jonathan/idevicerestore/src'
make: *** [all-recursive] Error 1

before i ran this command i ran the ./autogen.sh command and no errors.
Please someone help!!

---

### Post by lkjoel on 2010-09-23
> **jepy10 said:**
> Hi im sorry im newbie in linux and i have search everywhere on google for help but i cant get pass this point i was following the tutorial on how to compile the idevicerestore on ubuntu but after i get the **libirecovery/git** and i cd into the directory and i type on the terminal **make linux && sudo make install** it tells me that it cant find the cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
cp: cannot stat `libirecovery.dylib': No such file or directory

so i went around and found that if i go into the makefile and remove the** install** info on there it will get me through so that worked but, i have a problem when i run the **make && sudo make install command on idevicerestore **it gives me this error:


jonathan@jonathan-laptop:~/idevicerestore$ make && sudo make install
Making all in src
make[1]: Entering directory `/home/jonathan/idevicerestore/src'
gcc -DPACKAGE_NAME=\"idevicerestore\" -DPACKAGE_TARNAME=\"idevicerestore\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"idevicerestore\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"idevicerestore\" -DVERSION=\"1.0\" -I. -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/local/include -g -O2 -MT idevicerestore-idevicerestore.o -MD -MP -MF .deps/idevicerestore-idevicerestore.Tpo -c -o idevicerestore-idevicerestore.o `test -f 'idevicerestore.c' || echo './'`idevicerestore.c
In file included from idevicerestore.c:29:
dfu.h:29:26: error: libirecovery.h: No such file or directory
In file included from idevicerestore.c:29:
dfu.h:33: error: expected specifier-qualifier-list before ‘irecv_client_t’
make[1]: *** [idevicerestore-idevicerestore.o] Error 1
make[1]: Leaving directory `/home/jonathan/idevicerestore/src'
make: *** [all-recursive] Error 1

before i ran this command i ran the ./autogen.sh command and no errors.
Please someone help!!
It looks like as if it was a faulty download.
> error: libirecovery.h: **No such file or directory**

---

### Post by newbootsucks on 2010-09-30
hey guys, i am folling the guide posted here : [http://www.ipodtouchfans.com/forums/showpost.php?p=2190981&postcount=24](http://www.ipodtouchfans.com/forums/showpost.php?p=2190981&postcount=24) . and when i try to install libirecovery i get this error...  any ideas?

chris@ubuntu:~/libimobiledevice/libirecovery$ sudo make linux install
gcc -o libirecovery.o -c src/libirecovery.c -g -I./include -lreadline -fPIC 
src/libirecovery.c: In function ‘irecv_send_buffer’:
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
src/libirecovery.c:436: warning: format ‘%d’ expects type ‘int’, but argument 5 has type ‘long unsigned int’
gcc -o libirecovery.so libirecovery.o -g -shared -Wl,-soname,libirecovery.so -lusb-1.0
gcc -o irecovery src/irecovery.c -g -I./include -L. -lirecovery -lreadline
#cp libirecovery.so /usr/local/lib/libirecovery.so
cp libirecovery.dylib /usr/local/lib/libirecovery.dylib
cp: cannot stat `libirecovery.dylib': No such file or directory
make: *** [install] Error 1

---

