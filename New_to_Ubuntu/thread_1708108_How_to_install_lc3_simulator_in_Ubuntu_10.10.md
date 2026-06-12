---
title: "How to install lc3 simulator in Ubuntu 10.10?"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by omkar_hande on 2011-03-16
I was trying to install the lc3 simulator that is available at [http://highered.mcgraw-hill.com/sites/0072467509/student_view0/lc-3_simulator.html](http://highered.mcgraw-hill.com/sites/0072467509/student_view0/lc-3_simulator.html)
getting this error...
```

root@ubuntu:/home/omkar# cd Downloads
root@ubuntu:/home/omkar/Downloads# cd lc3tools
root@ubuntu:/home/omkar/Downloads/lc3tools# ./configure
Configuring for Linux...
Installation directory is /home/omkar/Downloads/lc3tools
root@ubuntu:/home/omkar/Downloads/lc3tools# make
/usr/bin/flex -i -Plc3 lc3.f
/usr/bin/gcc -c -g -Wall -o lex.lc3.o lex.lc3.c
lc3.f: In function ‘sym_name’:
lc3.f:505: warning: pointer targets in initialization differ in signedness
lc3.f:512: warning: pointer targets in return differ in signedness
lc3.f: In function ‘find_label’:
lc3.f:525: warning: pointer targets in assignment differ in signedness
lc3.f:526: warning: pointer targets in passing argument 1 of ‘find_symbol’ differ in signedness
symbol.h:55: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3.f: In function ‘generate_instruction’:
lc3.f:564: warning: pointer targets in assignment differ in signedness
lc3.f:566: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/include/string.h:235: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:566: warning: pointer targets in assignment differ in signedness
lc3.f:569: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/include/string.h:235: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:569: warning: pointer targets in assignment differ in signedness
lc3.f:577: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:608: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:610: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:516: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:618: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:627: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:634: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:636: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:516: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:644: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:646: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:516: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:659: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:678: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:682: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:697: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:700: warning: pointer targets in passing argument 1 of ‘find_label’ differ in signedness
lc3.f:516: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f:734: warning: pointer targets in passing argument 1 of ‘read_val’ differ in signedness
lc3.f:463: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3.f: In function ‘found_label’:
lc3.f:772: warning: pointer targets in initialization differ in signedness
lc3.f:778: warning: pointer targets in passing argument 1 of ‘add_symbol’ differ in signedness
symbol.h:54: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3.f: At top level:
lex.lc3.c:2331: warning: ‘input’ defined but not used
/usr/bin/gcc -c -g -Wall -o symbol.o symbol.c
/usr/bin/gcc -g -o lc3as lex.lc3.o symbol.o
/usr/bin/flex -i -Plc3convert lc3convert.f
/usr/bin/gcc -c -g -Wall -o lex.lc3convert.o lex.lc3convert.c
lex.lc3convert.c:1279: warning: ‘input’ defined but not used
/usr/bin/gcc -g -o lc3convert lex.lc3convert.o
/usr/bin/gcc -c -g -Wall  -DINSTALL_DIR="\"/home/omkar/Downloads/lc3tools\"" -DMAP_LOCATION_TO_SYMBOL -o lc3sim.o lc3sim.c
lc3sim.c:147: warning: pointer targets in initialization differ in signedness
lc3sim.c:148: warning: pointer targets in initialization differ in signedness
lc3sim.c:149: warning: pointer targets in initialization differ in signedness
lc3sim.c:150: warning: pointer targets in initialization differ in signedness
lc3sim.c:151: warning: pointer targets in initialization differ in signedness
lc3sim.c:152: warning: pointer targets in initialization differ in signedness
lc3sim.c:153: warning: pointer targets in initialization differ in signedness
lc3sim.c:154: warning: pointer targets in initialization differ in signedness
lc3sim.c:155: warning: pointer targets in initialization differ in signedness
lc3sim.c:156: warning: pointer targets in initialization differ in signedness
lc3sim.c:157: warning: pointer targets in initialization differ in signedness
lc3sim.c:158: warning: pointer targets in initialization differ in signedness
lc3sim.c:159: warning: pointer targets in initialization differ in signedness
lc3sim.c:160: warning: pointer targets in initialization differ in signedness
lc3sim.c:161: warning: pointer targets in initialization differ in signedness
lc3sim.c:162: warning: pointer targets in initialization differ in signedness
lc3sim.c:163: warning: pointer targets in initialization differ in signedness
lc3sim.c:164: warning: pointer targets in initialization differ in signedness
lc3sim.c: In function ‘command_loop’:
lc3sim.c:397: warning: pointer targets in assignment differ in signedness
lc3sim.c:413: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:419: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:399: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:433: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:433: warning: pointer targets in passing argument 2 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char * const’
lc3sim.c:444: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:444: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘const char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:445: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
/usr/include/string.h:136: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:446: warning: pointer targets in passing argument 1 of ‘strdup’ differ in signedness
/usr/include/string.h:175: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:446: warning: pointer targets in assignment differ in signedness
lc3sim.c: In function ‘read_obj_file’:
lc3sim.c:597: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
/usr/include/stdio.h:269: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c: In function ‘read_sym_file’:
lc3sim.c:625: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
/usr/include/stdio.h:269: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:627: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
/usr/include/stdio.h:624: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:629: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:630: warning: pointer targets in passing argument 1 of ‘strcmp’ differ in signedness
/usr/include/string.h:143: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:634: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:636: warning: pointer targets in passing argument 1 of ‘add_symbol’ differ in signedness
symbol.h:54: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘init_machine’:
lc3sim.c:668: warning: pointer targets in passing argument 1 of ‘read_obj_file’ differ in signedness
lc3sim.c:591: note: expected ‘const unsigned char *’ but argument is of type ‘char *’
lc3sim.c:675: warning: pointer targets in passing argument 1 of ‘read_sym_file’ differ in signedness
lc3sim.c:617: note: expected ‘const unsigned char *’ but argument is of type ‘char *’
lc3sim.c:690: warning: pointer targets in passing argument 1 of ‘cmd_execute’ differ in signedness
lc3sim.c:113: note: expected ‘const unsigned char *’ but argument is of type ‘char *’
lc3sim.c:692: warning: pointer targets in passing argument 1 of ‘cmd_file’ differ in signedness
lc3sim.c:114: note: expected ‘const unsigned char *’ but argument is of type ‘char *’
lc3sim.c: In function ‘cmd_break’:
lc3sim.c:1076: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1079: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:399: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1080: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1090: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1091: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1102: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘cmd_execute’:
lc3sim.c:1186: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
/usr/include/stdio.h:269: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c: In function ‘cmd_file’:
lc3sim.c:1229: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:399: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3sim.c:1237: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:1237: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1240: warning: pointer targets in passing argument 1 of ‘strrchr’ differ in signedness
/usr/include/string.h:262: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1240: warning: pointer targets in assignment differ in signedness
lc3sim.c:1240: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/include/string.h:235: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1242: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
/usr/include/string.h:136: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:1244: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1251: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1269: warning: pointer targets in passing argument 1 of ‘strdup’ differ in signedness
/usr/include/string.h:175: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1271: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c:1286: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
/usr/include/string.h:128: note: expected ‘char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘parse_address’:
lc3sim.c:1370: warning: pointer targets in passing argument 1 of ‘find_symbol’ differ in signedness
symbol.h:55: note: expected ‘const char *’ but argument is of type ‘const unsigned char *’
lc3sim.c:1374: warning: pointer targets in assignment differ in signedness
lc3sim.c:1376: warning: pointer targets in assignment differ in signedness
lc3sim.c:1378: warning: pointer targets in assignment differ in signedness
lc3sim.c:1379: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1379: warning: pointer targets in passing argument 2 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘parse_range’:
lc3sim.c:1400: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1416: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘cmd_option’:
lc3sim.c:1507: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1509: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:399: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1510: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1512: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1518: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1525: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1532: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1540: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1550: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c: In function ‘cmd_register’:
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1628: warning: pointer targets in initialization differ in signedness
lc3sim.c:1629: warning: pointer targets in initialization differ in signedness
lc3sim.c:1629: warning: pointer targets in initialization differ in signedness
lc3sim.c:1629: warning: pointer targets in initialization differ in signedness
lc3sim.c:1630: warning: pointer targets in initialization differ in signedness
lc3sim.c:1632: warning: pointer targets in initialization differ in signedness
lc3sim.c:1632: warning: pointer targets in initialization differ in signedness
lc3sim.c:1632: warning: pointer targets in initialization differ in signedness
lc3sim.c:1633: warning: pointer targets in initialization differ in signedness
lc3sim.c:1638: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
lc3sim.c:1652: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘const unsigned char * const’
lc3sim.c:1652: warning: pointer targets in passing argument 2 of ‘strcasecmp’ differ in signedness
/usr/include/string.h:536: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1658: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
/usr/include/string.h:399: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1660: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
lc3sim.c:1660: warning: pointer targets in passing argument 2 of ‘strncasecmp’ differ in signedness
/usr/include/string.h:540: note: expected ‘const char *’ but argument is of type ‘const unsigned char * const’
lc3sim.c: In function ‘cmd_translate’:
lc3sim.c:1758: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
/usr/include/stdio.h:450: note: expected ‘const char * __restrict__’ but argument is of type ‘const unsigned char *’
/usr/bin/gcc -c -g -Wall -DMAP_LOCATION_TO_SYMBOL -o sim_symbol.o symbol.c
/usr/bin/gcc -g  -o lc3sim \
        lc3sim.o sim_symbol.o  -lcurses
/usr/bin/ld: cannot find -lcurses
collect2: ld returned 1 exit status
make: *** [lc3sim] Error 1


```Any idea how to make it work?

---

### Post by ikt on 2011-03-16
Did you do this?

[QUOTE=README]DEBIAN USERS (and possibly some other distributions of Linux):
After you configure, remove "-lcurses" from the OS_SIM_LIBS
definition in the Makefile.  (Or you can install the curses library,
but the routines that I use are in the standard library in the
Debian distribution.  In other distributions, they're in the
curses library.  One day, I'll extend configure to check for it.)[/QUOTE]

---

