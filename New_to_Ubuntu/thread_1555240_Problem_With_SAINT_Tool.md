---
title: "Problem With SAINT Tool"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by saleh abbas on 2010-08-17
hi, i downloaded the [COLOR=DarkRed][SAINT]("http://www.saintcorporation.com/products/software/saintScanner.html")[/COLOR] tool for [COLOR=#ff0000]Penetration test [/COLOR] on my network and this is the result 

ls

[COLOR=red]bin      config.cache     configure       include       Makefile.in    perllib    reconfig  saint.1
CHANGES    config.log       configure.in    install-sh  old            README     rules       scripts
config     config.status    html          Makefile     perl          READMEs   saint      src[/COLOR]

./configure

[COLOR=magenta]loading cache ./config.cache
[/COLOR][COLOR=magenta]checking for gcc... (cached) gcc
[/COLOR][COLOR=magenta]checking whether the C compiler (gcc  ) works... yes
[/COLOR][COLOR=magenta]checking whether the C compiler (gcc  ) is a cross-compiler... no
[/COLOR][COLOR=magenta]checking whether we are using GNU C... (cached) yes
[/COLOR][COLOR=magenta]checking whether gcc accepts -g... (cached) yes
[/COLOR][COLOR=magenta]checking for a BSD compatible install... (cached) /usr/bin/install -c
[/COLOR][COLOR=magenta]checking whether make sets ${MAKE}... (cached) yes
[/COLOR][COLOR=magenta]checking for main in -lPW... (cached) no
[/COLOR][COLOR=magenta]checking for main in -lX11_s... (cached) no
[/COLOR][COLOR=magenta]checking for main in -lXm_s... (cached) no
[/COLOR][COLOR=magenta]checking for main in -lXt_s... (cached) no
[/COLOR][COLOR=magenta]checking for main in -lc_s... (cached) no
[/COLOR][COLOR=magenta]checking for main in -lnsl... (cached) yes
[/COLOR][COLOR=magenta]checking for main in -lresolv... (cached) yes
[/COLOR][COLOR=magenta]checking for main in -lrpc... (cached) no
[/COLOR][COLOR=magenta]checking for rpc socket compatibility... no
[/COLOR][COLOR=magenta]checking for main in -lrpcsvc... (cached) yes
[/COLOR][COLOR=magenta]checking for main in -lsocket... (cached) no
[/COLOR][COLOR=magenta]checking for getpwnam in -lsun... (cached) no
[/COLOR][COLOR=magenta]checking for +DAportable... no
[/COLOR][COLOR=magenta]checking how to run the C preprocessor... (cached) gcc -E
[/COLOR][COLOR=magenta]checking for linux/limits.h... (cached) yes
[/COLOR][COLOR=magenta]checking for ANSI C header files... (cached) yes
[/COLOR][COLOR=magenta]checking for sys/tiuser.h... (cached) no
[/COLOR][COLOR=magenta]checking for uid_t in sys/types.h... (cached) yes
[/COLOR][COLOR=magenta]checking type of array argument to getgroups... (cached) gid_t
[/COLOR][COLOR=magenta]checking if sys_errlist is declared... yes
[/COLOR][COLOR=magenta]checking if system netinet headers work... no
[/COLOR][COLOR=magenta]checking for glibc21... yes
[/COLOR][COLOR=magenta]checking for showmount... (cached) no
[/COLOR][COLOR=magenta]checking for rpcgen... (cached) /usr/bin/rpcgen
[/COLOR][COLOR=magenta]creating ./config.status
[/COLOR][COLOR=magenta]creating Makefile
[/COLOR][COLOR=magenta]Reconfiguring...
[/COLOR][COLOR=magenta]Checking to make sure all the targets are here...
[/COLOR][COLOR=magenta]Trying to find Perl... /usr/bin/perl5.10.1
[/COLOR][COLOR=magenta]Changing the source in PERL scripts...
[/COLOR][COLOR=magenta]Trying to find HTML/WWW browser...
[/COLOR][COLOR=magenta]Cannot find a web browser!  SAINT cannot be run from GUI
[/COLOR][COLOR=magenta]Looking for UNIX commands...
[/COLOR][COLOR=magenta]Doing substitutions on the shell scripts...
[/COLOR][COLOR=magenta]Changing paths in config/paths.pl...
[/COLOR][COLOR=magenta]Changing paths in config/paths.sh...
[/COLOR][COLOR=red][COLOR=magenta]root@saleh-desktop:/home/saleh/saint-3.0.1#[/COLOR] 

[/COLOR]make 

[COLOR=purple]make[1]: Entering directory `/home/saleh/saint-3.0.1'[/COLOR]
[COLOR=purple]cd src/misc; make "LIBS=-lnsl -lresolv -lrpcsvc"  "XFLAGS=-g -O2  -I/home/saleh/saint-3.0.1/include  -I/home/saleh/saint-3.0.1/include/glibc21  -DSTDC_HEADERS=1  -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1 "  "RPCGEN=/usr/bin/rpcgen"[/COLOR]
[COLOR=purple]make[2]: Entering directory `/home/saleh/saint-3.0.1/src/misc'[/COLOR]
[COLOR=purple]gcc -O -I. -g -O2   -I/home/saleh/saint-3.0.1/include  -I/home/saleh/saint-3.0.1/include/glibc21  -DSTDC_HEADERS=1  -DGETGROUPS_T=gid_t -DSYS_ERRLIST_DECLARED=1 -D_BSD_SOURCE=1    -c -o  rex_xdr.o rex_xdr.c[/COLOR]
[COLOR=purple]rex_xdr.c: In function ‘xdr_rex_start’:[/COLOR]
[COLOR=purple]rex_xdr.c:42: warning: assignment from incompatible pointer type[/COLOR]
[COLOR=purple]rex_xdr.c:53: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:54: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:55: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:56: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:72: warning: assignment from incompatible pointer type[/COLOR]
[COLOR=purple]rex_xdr.c:83: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:84: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:85: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]rex_xdr.c:86: error: lvalue required as increment operand[/COLOR]
[COLOR=purple]make[2]: *** [rex_xdr.o] Error 1[/COLOR]
[COLOR=purple]make[2]: Leaving directory `/home/saleh/saint-3.0.1/src/misc'[/COLOR]
[COLOR=purple]make[1]: *** [all] Error 2[/COLOR]
[COLOR=purple]make[1]: Leaving directory `/home/saleh/saint-3.0.1'[/COLOR]
[COLOR=purple]make: *** [generic] Error 2

[COLOR=Black]and this is my all problem 
thanks alot
[/COLOR][/COLOR]

---

### Post by saleh abbas on 2010-08-18
[CENTER][SIZE=4][COLOR=Blue]Can I know If There Is a Solution Or Not For My Problem ?
[/COLOR][/SIZE][/CENTER]

---

### Post by Bibosch on 2012-01-24
> **saleh abbas said:**
> [CENTER][SIZE=4][COLOR=Blue]Can I know If There Is a Solution Or Not For My Problem ?
[/COLOR][/SIZE][/CENTER]


Whats about Nessus. Its not written in c and easier to update?

---

### Post by nothingspecial on 2012-01-24
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

