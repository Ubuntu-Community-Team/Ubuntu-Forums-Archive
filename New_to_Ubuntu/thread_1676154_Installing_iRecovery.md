---
title: "Installing iRecovery"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by amamann on 2011-01-26
Hi,

I'm new to Linux as a whole and one of the first things I'm  trying(!) to get working is iRecovery  ([https://github.com/Chronic-Dev/libirecovery](https://github.com/Chronic-Dev/libirecovery)).  I've already got my  Iphone picked up and mounted fine in 10.10 and I've downloaded the files  from the above site and extracted them just using the GUI tools.
I  understand now that the file needs to be complied and installed before  I'm able to use the commands in the terminal.  So I've also got the  build essential and checkinstall on as well.

From reading about  online there appears to be no ./configure file that its normally  suggested I run first but there is a makefile ready to go  and I've  posted the terminal happenings below.  I've looked online for solutions  but they all appear targetted at a very different version and makefile  so they've not got me anywhere.

Any assistance or guidance would be very much appreciated as my whole evening of trying has got me nowhere and I'm almost certain its something fairly straightforward.

> alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ ls
include  irecovery.c  libirecovery.c  LICENCE  Makefile  README  scripts  TODO
alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ sudo make
[sudo] password for alex: 
gcc -c libirecovery.c -o libirecovery.o -O3 -I./include -I/usr/include -I/usr/local/include 
ar rs libirecovery.a libirecovery.o
ar: creating libirecovery.a
alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ ls
include      libirecovery.a  libirecovery.o  Makefile  scripts
irecovery.c  libirecovery.c  LICENCE         README    TODO
alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ sudo checkinstall

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: n

Please write a description for the package.
End your description with an empty line or EOF.
>> iRecovery 
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "Chronic-Dev-libirecovery" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@alex-TA790GX-128M ]
1 -  Summary: [ iRecovery ]
2 -  Name:    [ chronic-dev-libirecovery ]
3 -  Version: [ 6f2649d ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ Chronic-Dev-libirecovery-6f2649d ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ chronic-dev-libirecovery ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by gordintoronto on 2011-01-26
The normal sequence is:
make
make install

---

### Post by amamann on 2011-01-27
Thanks for the reply.  That was what I initially tried but as it didn't work I tried the checkinstall instead.  When using the above I get a similar error message.

> alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ make
make: `libirecovery.a' is up to date.
alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ make install
make: *** No rule to make target `install'. Stop.
alex@alex-TA790GX-128M:~/Downloads/Chronic-Dev-libirecovery-6f2649d$ 

---

