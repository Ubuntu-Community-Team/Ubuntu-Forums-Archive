---
title: "compile ALOS_pre_process.c"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by shaheru on 2010-11-23
Hello,
I look for compiling the file process.c in a directory that contains:

ALOS_pre_process.c  
Makefile               
parse_ALOS_commands.c  
read_ALOS_data.c       
swap_ALOS_data_info.c

I tried with "make" but obtain 

shaheru@Fentale:ALOS_pre_process$ make
gcc -g -Wall  -c ALOS_pre_process.c -o ALOS_pre_process.o -I../include
gcc -g -Wall  -c parse_ALOS_commands.c -o parse_ALOS_commands.o -I../include
gcc -g -Wall  -c read_ALOS_data.c -o read_ALOS_data.o -I../include
read_ALOS_data.c: In function ‘read_sardata_info’:
read_ALOS_data.c:236: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘unsigned int’
read_ALOS_data.c:242: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘unsigned int’
read_ALOS_data.c:246: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘unsigned int’
gcc -g -Wall  -c swap_ALOS_data_info.c -o swap_ALOS_data_info.o -I../include
gcc -g -Wall     -o ALOS_pre_process ALOS_pre_process.o parse_ALOS_commands.o read_ALOS_data.o swap_ALOS_data_info.o     -L../lib/`uname -p` -lALOS -lm  
/usr/bin/ld: cannot find -lALOS
collect2: ld returned 1 exit status
make: *** [ALOS_pre_process] Error 1

jruch@Fentale:ALOS_pre_process$ ls
ALOS_pre_process.c  parse_ALOS_commands.c  read_ALOS_data.o
ALOS_pre_process.o  parse_ALOS_commands.o  swap_ALOS_data_info.c
Makefile            read_ALOS_data.c       swap_ALOS_data_info.o

It adds me some file.o but didn't compile the .c file,

Thank you for your help!

---

