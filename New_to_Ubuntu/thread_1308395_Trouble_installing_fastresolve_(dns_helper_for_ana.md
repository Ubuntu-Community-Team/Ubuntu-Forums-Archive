---
title: "Trouble installing fastresolve (dns helper for analog)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Taxcheat on 2009-10-31
Trying to install fastresolve, a helper application that speeds up the sloooooow DNS lookups of the 'analog' web server log analyzer. The program is here:
[http://www.djmnet.org/sw/fastresolve/](http://www.djmnet.org/sw/fastresolve/)

I kludged my way through a bunch of errors until I hit this one: "configure: error: Berkeley DB library 2.x-4.x configured with --enable-cxx is required"

Ok, fine. I had 4.4 and 4.6 already installed by default or from apt-get. So I went ahead and downloaded 4.8 from oracle using [these instructions]("http://ubuntuforums.org/showthread.php?p=7598374") and the --enable-cxx command. I apt-get'ed python-cxx just because it said cxx. The error still is there. ](*,) HELP!

```
 $ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for perl5... no
checking for perl... /usr/bin/perl
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for fgetln... no
checking for socket... yes
checking for inet_ntoa... yes
checking for inet_aton... yes
checking for gzprintf in -lz... yes
checking for adns_submit in -ladns... yes
checking for Db::open in -ldb... no
checking for Db::open in -ldb_cxx... no
checking for Db::open in -ldb3_cxx... no
checking for Db::open in -ldb4_cxx... no
configure: error: Berkeley DB library 2.x-4.x configured with --enable-cxx is required
```My goal: I download raw log files to my desktop, but even with an i7, processing the DNS with analog takes an eternity. So fastresolve appears to do two things: (1) multi-thread the DNS lookups, (2) do a whois to fill out domain names with business names. Is there another program that can do those two things? Thanks in advance.

---

