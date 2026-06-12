---
title: "pdflib install on ubuntu 9"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by garr1095 on 2010-07-31
Does anyone know of a guide to install and get the pdflib working? I am very new to Ubuntu/LINUX. I have read a few posts on the subject but have run into a problem. Pear is installed. when I run this:

which pear

I get the following:

/usr/bin/pear

Which, I am fairly certain tells me pear is installed and working. I am really at a loss after that. I did run the following:

bill@Bill-Linux:~$ sudo pecl install pdflib
downloading pdflib-2.1.8.tgz ...
Starting to download pdflib-2.1.8.tgz (55,797 bytes)
.............done: 55,797 bytes
10 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
path to pdflib installation? : /tmp/PDFlib-6.0.3p1-Linux/bind/c                 <<<I am fairly certain this is wrong
building in /var/tmp/pear-build-root/pdflib-2.1.8
running: /tmp/pear/temp/pdflib/configure --with-pdflib=/tmp/PDFlib-6.0.3p1-Linux/bind/c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for PDFlib support... yes, shared
configure: error: pdflib.h not found! Check the path passed to --with-pdflib=<PATH>. PATH should be the install prefix directory.
ERROR: `/tmp/pear/temp/pdflib/configure --with-pdflib=/tmp/PDFlib-6.0.3p1-Linux/bind/c' failed

Sooo, I am not sure what I need to fix to get this working. Any help is greatly appreciated.

---

### Post by garr1095 on 2010-08-01
I found this from the PDFlib web site:

PDFlib Lite source code must be compiled to generate a usable library.  PDFlib GmbH does not offer precompiled (binary) versions of PDFlib Lite.

Hmmmm....

Another beginner question... How do I compile this lib?

Thanks

---

