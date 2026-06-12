---
title: "hostap installation help"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by chris857 on 2007-02-01
I am trying to install hostAP onto Ubuntu 2.6.17-10-generic and I keep getting errors. Here is the output I keep getting:

root@chris-laptop:/usr/src/modules/hostap-source# ./debian/rules binary-modules KSRC=/usr/src/linux-headers-2.6.17-10-generic
/usr/bin/gcc-4.1
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-10-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.17-10-generic/g ;s/#KVERS#/2.6.17-10-generic/g ; s/_KVERS_/2.6.17-10-generic/g ; s/##KDREV##//g ; s/#KDREV#//g ; s/_KDREV_//g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.17-10-generic
# build and install the module
/usr/bin/make KERNEL_PATH=/usr/src/linux-headers-2.6.17-10-generic DESTDIR=/usr/src/modules/hostap-source/debian/hostap-modules-2.6.17-10-generic OLDMAKE=
make[1]: Entering directory `/usr/src/modules/hostap-source'
/usr/bin/make -C /usr/src/linux-headers-2.6.17-10-generic SUBDIRS=/usr/src/modules/hostap-source/driver/modules \
                MODVERDIR=/usr/src/modules/hostap-source/driver/modules modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
scripts/Makefile.build:17: /usr/src/modules/hostap-source/driver/modules/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/modules/hostap-source/driver/modules/Makefile'.  Stop.
make[2]: *** [_module_/usr/src/modules/hostap-source/driver/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [2.6] Error 2
make[1]: Leaving directory `/usr/src/modules/hostap-source'
make: *** [binary-modules] Error 2

Can someone please help? I have no idea what is wrong. I've followed the directions mentioned in the WifiDocs exactly and I keep getting errors. Please help. Thanks. -Chris

---

