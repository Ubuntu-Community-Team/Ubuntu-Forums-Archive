---
title: "compiling codes from Unix network programming -- richard stevens"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-09-30
Hi,

I'm working on the unix network programming. So I started with the book by richard stevens. (source codes can be obtained  [here]("http://www.kohala.com/start/unpv12e.html") ). I started out by reading the README file. I found different errors at each stage. I'm posting the errors and the config.h file it created. 

the errors are ( same as the file errors.txt):
```
1)  cd unpv12e/
    ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for pthread_create in -lpthread... yes
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for /usr/local/bind/lib/libbind.a... no
checking for /home/bhargava/libbind.a... no
checking for /home/bhargava/libresolv.a... no
checking for res_init in -lresolv... no
checking for t_open in -lxti... no
checking for /home/bhargava/libunp.a... no
checking for /home/bhargava/libunpxti.a... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/socket.h... yes
checking for sys/time.h... yes
checking for time.h... yes
checking for netinet/in.h... yes
checking for arpa/inet.h... yes
checking for errno.h... yes
checking for fcntl.h... yes
checking for netdb.h... yes
checking for signal.h... yes
checking for stdio.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for sys/stat.h... yes
checking for sys/uio.h... yes
checking for unistd.h... yes
checking for sys/wait.h... yes
checking for sys/un.h... yes
checking for sys/select.h... yes
checking for poll.h... yes
checking for strings.h... yes
checking for sys/ioctl.h... yes
checking for sys/filio.h... no
checking for sys/sockio.h... no
checking for pthread.h... yes
checking for sys/sysctl.h... yes
checking for poll.h... (cached) yes
checking for xti.h... no
checking for xti_inet.h... no
checking for netconfig.h... no
checking for netdir.h... no
checking for stropts.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking if uint8_t defined... yes
checking if int16_t defined... yes
checking if uint16_t defined... yes
checking if int32_t defined... yes
checking if uint32_t defined... yes
checking if size_t defined... yes
checking if ssize_t defined... yes
checking if socklen_t defined... yes
checking if sa_family_t defined... yes
checking if t_scalar_t defined... no
checking if t_uscalar_t defined... yes
checking if sockaddr{} has sa_len member... no
checking if msghdr{} has msg_control member... yes
checking for getaddrinfo function prototype in netdb.h... yes
checking for getnameinfo function prototype in netdb.h... yes
checking for gethostname function prototype in unistd.h... yes
checking for getrusage function prototype in sys/resource.h... yes
checking for hstrerror function prototype in netdb.h... yes
checking for if_nametoindex function prototype in net/if.h... yes
checking for inet_aton function prototype in arpa/inet.h... yes
checking for inet_pton function prototype in arpa/inet.h... yes
checking for isfdtype function prototype in sys/stat.h... no
checking for pselect function prototype in sys/select.h... yes
checking for snprintf function prototype in stdio.h... yes
checking for sockatmark function prototype in sys/socket.h... yes
checking for addrinfo{}... yes
checking for if_nameindex{}... yes
checking for sockaddr_dl{}... no
checking for timespec{}... yes
checking for /dev/tcp... no
checking for /dev/xti/tcp... no
checking for /dev/streams/xtiso/tcp... no
checking for bzero... yes
checking for getaddrinfo... yes
checking for gethostname... yes
checking for gethostbyname2... yes
checking for gethostbyname_r... yes
checking for getnameinfo... yes
checking for hstrerror... yes
checking for if_nametoindex... yes
checking for inet_aton... yes
checking for inet_pton... yes
checking for isfdtype... yes
checking for poll... yes
checking for pselect... yes
checking for snprintf... yes
checking for sockatmark... yes
checking for vsnprintf... yes
checking for IPv4 support... yes
checking for IPv6 support... yes
checking for Unix domain sockets... yes
checking for multicast support... yes
checking for -I/home/bhargava/doc/unp2ev1/src/include... no
updating cache ./config.cache
creating ./config.status
creating Makefile
creating Make.defines
creating config.h


2)    cd lib
    make
gcc -g -O2 -D_REENTRANT -Wall   -c -o connect_nonb.o connect_nonb.c
In file included from connect_nonb.c:1:
unp.h:114: error: redefinition of ‘struct in_pktinfo’
make: *** [connect_nonb.o] Error 1

    
3)    cd ../libfree/
        make
gcc -g -O2 -D_REENTRANT -Wall   -c -o in_cksum.o in_cksum.c
gcc -g -O2 -D_REENTRANT -Wall   -c -o inet_ntop.o inet_ntop.c
gcc -g -O2 -D_REENTRANT -Wall   -c -o inet_pton.o inet_pton.c
ar rv ../libunp.a in_cksum.o inet_ntop.o inet_pton.o
ar: creating ../libunp.a
a - in_cksum.o
a - inet_ntop.o
a - inet_pton.o
ranlib ../libunp.a



4)    cd ../libgai/
     make
gcc -g -O2 -D_REENTRANT -Wall   -c -o getaddrinfo.o getaddrinfo.c
In file included from gai_hdr.h:1,
                 from getaddrinfo.c:2:
unp.h:114: error: redefinition of ‘struct in_pktinfo’
getaddrinfo.c: In function ‘getaddrinfo’:
getaddrinfo.c:58: error: ‘EAI_ADDRFAMILY’ undeclared (first use in this function)
getaddrinfo.c:58: error: (Each undeclared identifier is reported only once
getaddrinfo.c:58: error: for each function it appears in.)
getaddrinfo.c:116: error: ‘EAI_NODATA’ undeclared (first use in this function)
make: *** [getaddrinfo.o] Error 1


5)     cd ../libroute/
     make
gcc -g -O2 -D_REENTRANT -Wall   -c -o get_rtaddrs.o get_rtaddrs.c
In file included from unproute.h:1,
                 from get_rtaddrs.c:1:
unp.h:114: error: redefinition of ‘struct in_pktinfo’
In file included from get_rtaddrs.c:1:
unproute.h:3:45: error: net/if_dl.h: No such file or directory
get_rtaddrs.c: In function ‘get_rtaddrs’:
get_rtaddrs.c:21: error: ‘RTAX_MAX’ undeclared (first use in this function)
get_rtaddrs.c:21: error: (Each undeclared identifier is reported only once
get_rtaddrs.c:21: error: for each function it appears in.)
get_rtaddrs.c:24: error: ‘struct sockaddr’ has no member named ‘sa_len’
get_rtaddrs.c:24: error: ‘struct sockaddr’ has no member named ‘sa_len’
get_rtaddrs.c:24: error: ‘struct sockaddr’ has no member named ‘sa_len’
get_rtaddrs.c:24: error: ‘struct sockaddr’ has no member named ‘sa_len’
make: *** [get_rtaddrs.o] Error 1
```If any one can help me with the errors, I'll be thankful.


Thank you.

---

### Post by Bachstelze on 2009-09-30
How old is the book?

---

### Post by bhargava470 on 2009-09-30
> **Bachstelze said:**
> How old is the book?


*UNIX Network Programming, Volume 1, Second Edition: Networking APIs: Sockets and XTI*,     Prentice Hall, 1998, ISBN 0-13-490012-X. further information may be found [here]("http://www.kohala.com/start/unpv12e.html").

---

### Post by NareshCodename37 on 2010-06-26
Comment the line 125 where the struct in_pktinfo and that should go fine and you will be able to execute your programs. However you may run into some errors while using this struct in your program. So refine from using it.

---

