---
title: "How install printer driver in ubuntu 10.10 maverick"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by xracon on 2010-10-20
I want to know how to install printer drivers 
Kyocera FS-1016MFP Source: [https://sourceforge.net/projects/kyo-fs1016mfp/](https://sourceforge.net/projects/kyo-fs1016mfp/)

since the makefile that comes in the file refers to the folders 
foomatic-db package and apparently in this version of ubuntu this 
package was replaced by foomatic-db-ppds-compressed 

This makefile says 

CC=gcc
DEPS=jbig.h
%.o: %.c $(DEPS)
$(CC) -c -o $@ $<

foo2kyo: foo2kyo.o jbig.o jbig_tab.o
gcc -o $@ foo2kyo.o jbig.o jbig_tab.o
cp -R foomatic-db/* /usr/share/foomatic/db/source/
foomatic-compiledb foo2kyo

install: foo2kyo
cp foo2kyo-wrapper /usr/bin
cp foo2kyo /usr/bin
cp ppd/Kyocera-Mita-FS-1016MFP-foo2kyo.ppd /usr/share/cups/model

.PHONY: clean install

clean:
rm -f *.o foo2kyo
rm -r ppd/

---

### Post by P4man on 2010-10-20
foomatic-db is still there?
Anyway, this may help:
[https://bugs.launchpad.net/ubuntu/+bug/238228](https://bugs.launchpad.net/ubuntu/+bug/238228)

---

